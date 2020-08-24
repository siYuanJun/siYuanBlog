---
title: flipster 环形滚动插件
tags: jquery
categories: Plugins
abbrlink: '7941'
date: 2020-08-07 17:44:50
---

> 代码直接粘贴即可，资源文件可度娘查找

```
<div class="hospital" id="hospital">
    <div class="flipster">
        <ul class="flip-items">
            <li data-flip-category='1'><div class='img'><img src='https://s1.ax1x.com/2020/07/29/aZZiyq.jpg'></div></li>
        </ul>
    </div>
</div>
<script>
    $(function () {
        $("#hospital").hide();
    })
    
    setTimeout(function () {
        $("#hospital").show();
        $(".flipster").flipster({
            itemContainer: 'ul',
            itemSelector: 'li',
            style: 'carousel',
            start: 0,
            enableKeyboard: true,
            enableMousewheel: true,
            enableTouch: true,

            enableNav: false,
            enableNavButtons: false,

            onItemSwitch: function () {
            },
        });
    }, 500)
</script>
<link rel="stylesheet" href="/app/static/plugins/jquery.flipster.css">
<script src="/app/static/plugins/jquery.flipster.js"></script>
```