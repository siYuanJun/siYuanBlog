---
title: Laravel 框架，关于 Symfony-locale 报错
tags: Laravel-Bug
abbrlink: '2353'
date: 2020-09-04 17:13:59
cover: https://s1.ax1x.com/2020/09/04/wky1hT.jpg
---

> 今天操作 Laravel Ai 时 需重新 composer install 包， 搞完结果出了下面这么一个报错，当时一脸懵逼夹 :hooh

```
错误信息：
Symfony\Component\Debug\Exception\FatalErrorException
Declaration of Symfony\Component\Translation\TranslatorInterface::setLocale($locale) must be compatible with Symfony\Contracts\Translation\LocaleAwareInterface::setLocale(string $locale)
```

> 首先先检查 Composer PHP 版本 是否和项目一致，Laravel 6.0 系统以上必须保持一致，调整后可以先刷新看下，如不行在进行下面操作！

### 解决方案

1. 打开项目根目录下的 composer.json 文件
2. 在 require 中添加 “symfony/translation”: “4.3.8”

```
"require": {
    "php-ai/php-ml": "^0.9.0",
    "predis/predis": "^1.1",
    "rap2hpoutre/laravel-log-viewer": "^1.2",
    "stevenyangecho/laravel-u-editor": "~1.4",
    "symfony/translation": "4.3.8"
},
```

> 注意一定是 4.3.8，我试了 4.4，5.0，5.0.2 都不行。

3. 然后保存 json 文件
4. 进入项目根目录
5. 执行以下升级命令

```
composer update
```

6. 刷新页面，错误消失


> 特别鸣谢：[启蒙链接](https://blog.csdn.net/bboyzhouda/article/details/106711172)