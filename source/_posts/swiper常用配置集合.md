---
title: swiper常用配置集合
tags: swiper
abbrlink: '5152'
date: 2020-07-24 17:04:45
top_img:
cover:
---

### 导语
写项目的时候，使用的是swiper插件呈现的效果是一个swiper要实现两个分页器，下面就来总结一下
onInit 回调函数，初始化后执行。
swiper.bullets.length：是获取分页器swiper的分页器个数长度。
activeIndex：当前swiper-slide的索引。
onSlideChangeEnd(swiper)：回调函数，swiper从一个slide过渡到另一个slide结束时执行。
swiper.realIndex：当前活动的swiper-slide的索引，与activeIndex不同的是，在loop模式下不会将复制的块的数量

### 实现代码
```
<script>
    var caseviewSwiper = new Swiper('.swiper-container', {
        initialSlide: 0, // 当前页
        slidesPerView: 1, // 显示个数
        spaceBetween: 30, // 间距
        slidesPerGroup: 1, // 切换组个数
        loopFillGroupWithBlank: true, // 在loop模式下，为group填充空白slide
        pagination: {
            el: '.swiper-pagination',
            clickable: true,
            renderBullet: function (index, className) {
                var text = '';
                switch (index) {
                 case 0: text = '**'; break;
                }
                return '<li class="' + className + '">' + text + '</li>'
            }
        },
        navigation: {
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev',
        },
        on: {
            init: function () {
                var total = this.slides.length;
                console.log(total);
                $('.swiper-num .total').text('0' + total);
                this.emit('transitionEnd');
            },
            transitionEnd: function () {
                // 获取当前条数
                console.log(this.realIndex);
                var index = this.realIndex + 1;
                $(".swiper-num .active").text("0" + index);
            }
        }
    });
</script>
```

> 效果链接：http://huaruan.t.bjxcsy.com.cn/

> 发掘地址：https://www.cnblogs.com/ling-nl/p/10935749.html