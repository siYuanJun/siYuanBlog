---
title: uniapp 增加自定义统计代码(h5)
tags: uniapp
abbrlink: 5ea2
date: 2020-09-22 13:45:52
cover: 'https://s1.ax1x.com/2020/09/22/wLyrKx.png'
top_img: 'https://s1.ax1x.com/2020/09/09/w8m1WF.jpg'
---

### 新建 statistics.html 界面

> 可放置在项目的根目录，文件名称根据自己情况命名。

{% asset_img 20200922135037.png %}

### 粘贴内容

> 请复制如下代码到上方新建的 html 中，修改自己的百度统计代码

```
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
        <title>
            <%= htmlWebpackPlugin.options.title %>
        </title>
        <script>
            document.addEventListener('DOMContentLoaded', function() {
                document.documentElement.style.fontSize = document.documentElement.clientWidth / 20 + 'px'
            })
            // 生产环境时运行此脚本
            var _hmt = _hmt || [];
            (function() {
              var hm = document.createElement("script");
              hm.src = "https://hm.baidu.com/hm.js?此处为自己的百度统计码";
              var s = document.getElementsByTagName("script")[0]; 
              s.parentNode.insertBefore(hm, s);
            })();
        </script>
        <link rel="stylesheet" href="<%= BASE_URL %>static/index.css" />
    </head>
    <body>
        <noscript>
            <strong>Please enable JavaScript to continue.</strong>
        </noscript>
        <div id="app"></div>
        <!-- built files will be auto injected -->
    </body>
</html>
```

### 配置模版代码

> 依次进入 manifest.json > 源码视图 > h5(最下方) 节点，增加

{% asset_img 20200922134956.png %}


> 启蒙地址：https://www.cnblogs.com/niceyoo/p/12053730.html

