---
title: 手风琴特效Html
tags: 'html, css'
abbrlink: 59b0
date: 2020-07-23 09:36:04
---

### 代码实例

#### css
```
 <style>
 .solcas {
    display: flex;
  }
  .solcas .img {
    width: 25%;
    height: 423px;
    position: relative;
    overflow: hidden;
    transition: all 0.3s ease 0s;
  }
  .solcas .img .back {
    transition: all 0.3s ease 0s;
    content: "";
    position: absolute;
    top: 0px;
    left: 0px;
    height: 100%;
    width: 100%;
    background: rgba(0, 0, 0, 0.345);
  }
  .solcas .img .strcon {
    position: absolute;
    top: 0px;
    left: 0px;
    height: 100%;
    width: 100%;
    z-index: 1;
    background: rgba(0, 0, 0, 0.111);
  }
  .solcas .img .strcon .con {
    padding: 50px;
  }
  .solcas .img .strcon .con .bg-white {
    background: none;
    border: 1px solid #ffffff;
    color: #ffffff;
  }
  .solcas .img .strcon .con .bg-white:hover {
    background: #ffffff;
    color: rgba(25, 100, 183, 0.9);
  }
  .solcas .img .strcon .con .name {
    font-size: 30px;
  }
  .solcas .img .strcon .con .enname {
    font-size: 26px;
  }
  .solcas .img.cur {
    transition: all 0.3s ease 0s;
    width: 50%;
  }
  .solcas .img.cur .back {
    transition: all 0.3s ease 0s;
    left: 100%;
  }
 </style>
```

#### html
```
<div class="solcas">
<div class="img" data-hover="" style="background: url(/f/image/20191217/1576565832654571.jpg) no-repeat center; background-size: cover;">
<div class="back"></div>
<div class="strcon">
<div class="con">
<div class="name text-large text-white">dome1 </div>
<div class="enname text-big margin-top text-white text-transform-uppercase">Company</div>
<a href="" class="button more bg-white radius-rounded margin-large-top">查看详情</a>
</div>
</div>
</div><div class="img" data-hover="" style="background: url(/f/image/20191217/1576565851331268.jpg) no-repeat center; background-size: cover;">
<div class="back"></div>
<div class="strcon">
<div class="con">
<div class="name text-large text-white">dome2</div>
<div class="enname text-big margin-top text-white text-transform-uppercase">news</div>
<a href="" class="button more bg-white radius-rounded margin-large-top">查看详情</a>
</div>
</div>
</div><div class="img cur" data-hover="" style="background: url(/f/image/20191217/1576565860675659.jpg) no-repeat center; background-size: cover;">
<div class="back"></div>
<div class="strcon">
<div class="con">
<div class="name text-large text-white">dome3</div>
<div class="enname text-big margin-top text-white text-transform-uppercase">Case</div>
<a href="" class="button more bg-white radius-rounded margin-large-top">查看详情</a>
</div>
</div>
</div>
</div>
```

### 图片实例

{% asset_img 20200723093922.png 手风琴效果 %}

### 参照链接

> http://hostljyju5v.s61.linktom.com.cn/