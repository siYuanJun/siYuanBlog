---
title: new PHP函数file_get_contents()使用 https 协议时报错：SSL operation failed
categories: php
tags: 'https证书, ssl，file_get_contents'
abbrlink: c29a
date: 2020-07-25 17:21:10
---

### 场景

file_get_contents() 函数是用于将文件的内容读入到一个字符串中，是读取文件内容常用的函数之一。

但是有时在服务器上使用file_get_contents() 函数请求https 协议的url文件时会报错误，无法正确读取文件内容，

查看log日志，日志内容类似如下：

`
PHP Warning:  file_get_contents(): Failed to enable crypto in ......
PHP Warning:  file_get_contents......: failedream: operation failed in ......
PHP Warning:  file_get_contents(): SSL operatwith code 1. OpenSSL Error messages:
error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verin ......
`

### 原因
服务器未正确配置好https证书

### 解决方法：（三种解决方法）
#### 方法一

下载https证书到服务器

服务器 下载这个证书，http://curl.haxx.se/ca/cacert.pem
php.ini 配置
openssl.cafile = "/etc/ssl/certs/cacert.pem"//你实际下载证书的路径
重启 php 即可

#### 方法二

使用cURL 函数处理 https 的参数，获取文件内容

```
<?php
function getSSLPage($url) {
    $ch = curl_init();
    curl_setopt($ch, CURLOPT_HEADER, false);
    curl_setopt($ch, CURLOPT_URL, $url);
    curl_setopt($ch, CURLOPT_SSLVERSION,3); 
    $result = curl_exec($ch);
    curl_close($ch);
    return $result;
}

var_dump(getSSLPage("https://xxx.xxx.xxx"));
?>
```

> 引用：https://stackoverflow.com/questions/14078182/openssl-file-get-contents-failed-to-enable-crypto

#### 方法三

```
$stream_opts = [
    "ssl" => [
        "verify_peer"=>false,
        "verify_peer_name"=>false,
    ]
]; 

$response = file_get_contents("https://xxx.xxx.xxx",false, stream_context_create($stream_opts));
```

> 开发中建议使用 cURL 函数替代file_get_contents()函数。

> 发掘地：http://www.cnblogs.com/wenzheshen/