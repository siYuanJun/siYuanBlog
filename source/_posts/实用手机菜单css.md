---
title: 实用手机菜单css
tags: 移动端手机菜单
categories: components
abbrlink: 525f
date: 2020-08-29 17:30:13
cover: https://s1.ax1x.com/2020/08/29/d7xDJg.jpg
---

> 参考地址 https://www.17sucai.com/preview/1424582/2020-07-21/oktilcal/index.html#

```
<!-- Mobile Menu  -->
    <div class="mobile-menu">
        <div class="menu-backdrop"></div>
        <div class="close-btn"><span class="icon flaticon-multiply"></span></div>

        <nav class="menu-box">
            <div class="nav-logo"><a href="index.html"><img src="assets/images/resources/mobilemenu-logo.png" alt="" title=""></a></div>
            <div class="menu-outer"><!--Here Menu Will Come Automatically Via Javascript / Same Menu as in Header--></div>
            <!--Social Links-->
            <div class="social-links">
                <ul class="clearfix">
                    <li><a href="#"><span class="fab fa fa-facebook-square"></span></a></li>
                    <li><a href="#"><span class="fab fa fa-twitter-square"></span></a></li>
                    <li><a href="#"><span class="fab fa fa-pinterest-square"></span></a></li>
                    <li><a href="#"><span class="fab fa fa-google-plus-square"></span></a></li>
                    <li><a href="#"><span class="fab fa fa-youtube-square"></span></a></li>
                </ul>
            </div>
        </nav>
    </div>
<!-- End Mobile Menu --> 
```

```
/*** 
========================================
    Mobile Menu
========================================
***/
.nav-outer .mobile-nav-toggler {
    position: relative;
    display: none;
    float: right;
    cursor: pointer;
    padding: 30px 0;
}
.nav-outer .mobile-nav-toggler .inner{
    position: relative;
    display: block;
    padding: 3px 5px;
}

.mobile-menu{
	position: fixed;
	top: 0;
	right: 0;
	width: 300px;
	max-width:100%;
	height: 100%;
	padding-right:30px;
	opacity: 0;
	visibility: hidden;
	z-index: 999999;
}
.mobile-menu .menu-backdrop{
	position: fixed;
	top: 0;
	right: 0;
	width: 100%;
	height: 100%;
    background-color: rgba(3, 13, 40, 0.90);
	-webkit-transform: translateX(101%);
	-ms-transform: translateX(101%);
	transform: translateX(101%);
	transition: all 900ms ease;
    -moz-transition: all 900ms ease;
    -webkit-transition: all 900ms ease;
    -ms-transition: all 900ms ease;
    -o-transition: all 900ms ease;
	z-index: 1;
}
.mobile-menu-visible .mobile-menu .menu-backdrop{
	opacity: 0.70;
	visibility: visible;
	-webkit-transition:all 0.7s ease;
	-moz-transition:all 0.7s ease;
	-ms-transition:all 0.7s ease;
	-o-transition:all 0.7s ease;
	transition:all 0.7s ease;
	-webkit-transform: translateX(0%);
	-ms-transform: translateX(0%);
	transform: translateX(0%);
}
.mobile-menu .mCSB_inside>.mCSB_container{
	margin-right:5px;	
}
.mobile-menu .navbar-collapse{
	display:block !important;	
}


.mobile-menu .nav-logo{
	position:relative;
	padding:30px 25px;
	text-align:left;	
}
.mobile-menu .nav-logo a{
    position: relative;
    display: inline-block;
}

.mobile-menu-visible{
	overflow: hidden;
}
.mobile-menu-visible .mobile-menu{
	opacity: 1;
	visibility: visible;
}
.mobile-menu .menu-box{
	position: absolute;
	left: 0px;
	top: 0px;
	width: 100%;
	height: 100%;
	max-height: 100%;
	overflow-y: auto;
	background: #000000;
	padding: 0px 0px;
	z-index: 5;
	opacity: 0;
	visibility: hidden;
	border-radius: 0px;
	-webkit-transform: translateX(101%);
	-ms-transform: translateX(101%);
	transform: translateX(101%);
}
.mobile-menu-visible .mobile-menu .menu-box{
	opacity: 1;
	visibility: visible;
	-webkit-transition:all 0.7s ease;
	-moz-transition:all 0.7s ease;
	-ms-transition:all 0.7s ease;
	-o-transition:all 0.7s ease;
	transition:all 0.7s ease;
	-webkit-transform: translateX(0%);
	-ms-transform: translateX(0%);
	transform: translateX(0%);
}
.mobile-menu .close-btn{
	position: absolute;
	top: 10px;
	right: 10px;
	color: #ffffff;
	font-size: 20px;
	line-height: 30px;
	width: 24px;
	text-align: center;
	cursor: pointer;
	z-index: 10;
	-webkit-transition:all 0.9s ease;
	-moz-transition:all 0.9s ease;
	-ms-transition:all 0.9s ease;
	-o-transition:all 0.9s ease;
	transition:all 0.9s ease;
}
.mobile-menu-visible .mobile-menu .close-btn{
	-webkit-transform:rotate(360deg);
	-ms-transform:rotate(360deg);
	transform:rotate(360deg);
}
.mobile-menu .close-btn:hover{
	-webkit-transform:rotate(90deg);
	-ms-transform:rotate(90deg);
	transform:rotate(90deg);
}


.mobile-menu .navigation{
	position: relative;
	display: block;
	width: 100%;
	float: none;
}
.mobile-menu .navigation li{
	position: relative;
	display: block;
	border-top: 1px solid rgba(255,255,255,0.10);
}
.mobile-menu .navigation:last-child{
	border-bottom: 1px solid rgba(255,255,255,0.10);
}
.mobile-menu .navigation li > ul > li:first-child{
	border-top: 1px solid rgba(255,255,255,0.10);
}
.mobile-menu .navigation li > a{
	position: relative;
	display: block;
	padding: 10px 25px;
	color: #ffffff;
	font-size: 15px;
	line-height: 24px;
	font-weight: 600;
	text-transform: uppercase;
	-webkit-transition: all 500ms ease;
	-moz-transition: all 500ms ease;
	-ms-transition: all 500ms ease;
	-o-transition: all 500ms ease;
	transition: all 500ms ease;	
}
.mobile-menu .navigation li > a:before{
	content:'';
	position:absolute;
	left:0;
	top:0;
	height:0;
	-webkit-transition: all 500ms ease;
	-moz-transition: all 500ms ease;
	-ms-transition: all 500ms ease;
	-o-transition: all 500ms ease;
	transition: all 500ms ease;	
}
.mobile-menu .navigation li.current > a:before{
	height:100%;
}



.mobile-menu .navigation li ul li > a{
	font-size: 15px;
    font-weight: 400;
	margin-left: 20px;
	text-transform: capitalize;
}

.mobile-menu .navigation li.dropdown .dropdown-btn{
	position:absolute;
	top:6px;
	right:6px;
	width:32px;
	height:32px;
	text-align:center;
	color:#ffffff;
	font-size:16px;
	line-height:32px;
	background:rgba(255,255,255,0.10);
	cursor:pointer;
	border-radius:2px;
	-webkit-transition: all 500ms ease;
	-moz-transition: all 500ms ease;
	-ms-transition: all 500ms ease;
	-o-transition: all 500ms ease;
	transition: all 500ms ease;	
	z-index:5;
}
.mobile-menu .navigation li.dropdown .dropdown-btn.open{
	-webkit-transform:rotate(90deg);
	-ms-transform:rotate(90deg);
	transform:rotate(90deg);	
}
.mobile-menu .navigation li > ul,
.mobile-menu .navigation li > ul > li > ul{
	display: none;
}

.mobile-menu .social-links{
	position:relative;
	text-align:center;
	padding:30px 25px;
}
.mobile-menu .social-links li{
	position:relative;
	display:inline-block;
	margin:0px 5px 10px;
}
.mobile-menu .social-links li a{
	position:relative;
	color:#ffffff;
	font-size: 20px;
	line-height:32px;
	-webkit-transition: all 500ms ease;
	-moz-transition: all 500ms ease;
	-ms-transition: all 500ms ease;
	-o-transition: all 500ms ease;
	transition: all 500ms ease;	
}
.mobile-menu .social-links li a:hover{
    color: #02c18d;    
}
```