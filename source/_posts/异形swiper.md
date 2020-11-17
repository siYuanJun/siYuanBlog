---
title: 异形swiper
tags: swiper
abbrlink: cbb6
date: 2020-09-24 13:32:32
---

> 形状个性的 Swiper， Swiper-v4.*

### certify.css
```
@charset "utf-8";
#certify {
    position: relative;
}

#certify .swiper-container {
    padding-bottom: 95px
}

#certify .swiper-slide {
    width: 520px;
    height: 310px;
    background: #fff;
    box-shadow: 0 8px 30px #ddd
}

#certify .swiper-slide img {
    display: block;
    width: 100%;
    border-radius:5px;
}

#certify .swiper-slide.swiper-slide-active {
    box-shadow: rgba(0,0,0,0.2) 0 2px 6px 0;
}

#certify .swiper-pagination {
    width: 100%;
    bottom: 20px
}

#certify .swiper-pagination-bullets .swiper-pagination-bullet {
    margin: 0 5px;
    border: 3px solid #fff;
    background-color: #d5d5d5;
    width: 10px;
    height: 10px;
    opacity: 1
}

#certify .swiper-pagination-bullets .swiper-pagination-bullet-active {
    border: 3px solid #00aadc;
    background-color: #fff
}

#certify .swiper-button-prev {
    left: -30px;
    width: 45px;
    height: 45px;
    background: url(../../images/15.png) no-repeat center center;
}


#certify .swiper-button-next {
    right: -30px;
    width: 45px;
    height: 45px;
    background: url(../../images/16.png) no-repeat center center;
}

@media (max-width: 640px) {
    #certify .swiper-slide {
        width: 100%;
        height: 160px;
    }
    #certify .swiper-button-next {
        right: 0;
    }
    #certify .swiper-button-prev {
        left: 0;
    }
}
```

### index.html

```
<div class="margin-top-xxl">
    <div id="certify">
        <div class="swiper-container">
            <div class="swiper-wrapper">
                <div class='swiper-slide'><img src=''/></div>
                <div class='swiper-slide'><img src=''/></div>
                <div class='swiper-slide'><img src=''/></div>                    
            </div>
        </div>
        <div class="swiper-pagination"></div>
        <div class="swiper-button-prev"></div>
        <div class="swiper-button-next"></div>
    </div>
</div>
<script>
    var certifySwiper = new Swiper('#certify .swiper-container', {
        watchSlidesProgress: true,
        slidesPerView: 'auto',
        centeredSlides: true,
        loop: true, autoplay: true,
        loopedSlides: 5,
        autoplay: true,
        navigation: {
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev',
        },
        pagination: {
            el: '.swiper-pagination',
            //clickable :true,
        },
        on: {
            progress: function (progress) {
                for (i = 0; i < this.slides.length; i++) {
                    var slide = this.slides.eq(i);
                    var slideProgress = this.slides[i].progress;
                    modify = 1;
                    if (Math.abs(slideProgress) > 1) {
                        modify = (Math.abs(slideProgress) - 1) * 0.3 + 1;
                    }
                    translate = slideProgress * modify * 260 + 'px';
                    scale = 1 - Math.abs(slideProgress) / 5;
                    zIndex = 999 - Math.abs(Math.round(10 * slideProgress));
                    slide.transform('translateX(' + translate + ') scale(' + scale + ')');
                    slide.css('zIndex', zIndex);
                    slide.css('opacity', 1);
                    if (Math.abs(slideProgress) > 3) {
                        slide.css('opacity', 0);
                    }
                }
            },
            setTransition: function (transition) {
                for (var i = 0; i < this.slides.length; i++) {
                    var slide = this.slides.eq(i)
                    slide.transition(transition);
                }
            }
        }
    })
</script>
```

{% asset_img 20200924133647.png %}
