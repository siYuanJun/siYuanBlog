---
title: 关于Less常用函数介绍
date: 2020-6-13
tags: 'css, Less'
abbrlink: 43ff
---

```
escape(@string); // 通过 URL-encoding 编码字符串
e(@string); // 对字符串转义
%(@string, values...); // 格式化字符串
unit(@dimension, [@unit: ""]); // 移除或替换属性值的单位
color(@string); // 将字符串解析为颜色值
data-uri([mimetype,] url); // * 将资源内嵌到css中，可能回退到url()
ceil(@number); // 向上取整
floor(@number); // 向下取整
percentage(@number); // 将数字转换为百分比，例如 0.5 -> 50%
round(number, [places: 0]); // 四舍五入取整
sqrt(number); // * 计算数字的平方根
abs(number); // * 数字的绝对值
sin(number); // * sin函数
asin(number); // * arcsin函数
cos(number); // * cos函数
acos(number); // * arccos函数
tan(number); // * tan函数
atan(number); // * arctan函数
pi(); // * 返回PI
pow(@base, @exponent); // * 返回@base的@exponent次方
mod(number, number); // * 第一个参数对第二个参数取余
convert(number, units); // * 在数字之间转换
unit(number, units); // * 不转换的情况下替换数字的单位
color(string); // 将字符串或者转义后的值转换成颜色
rgb(@r, @g, @b); // 转换为颜色值
rgba(@r, @g, @b, @a); // 转换为颜色值
argb(@color); // 创建 #AARRGGBB 格式的颜色值
hsl(@hue, @saturation, @lightness); // 创建颜色值
hsla(@hue, @saturation, @lightness, @alpha); // 创建颜色值
hsv(@hue, @saturation, @value); // 创建颜色值
hsva(@hue, @saturation, @value, @alpha); // 创建颜色值
hue(@color); // 从颜色值中提取 hue 值（色相）
saturation(@color); // 从颜色值中提取 saturation 值（饱和度）
lightness(@color); // 从颜色值中提取 'lightness' 值（亮度）
hsvhue(@color); // * 从颜色中提取 hue 值，以HSV色彩空间表示（色相）
hsvsaturation(@color); // * 从颜色中提取 saturation 值，以HSV色彩空间表示（饱和度）
hsvvalue(@color); // * 从颜色中提取 value 值，以HSV色彩空间表示（色调）
red(@color); // 从颜色值中提取 'red' 值（红色）
green(@color); // 从颜色值中提取 'green' 值（绿色）
blue(@color); // 从颜色值中提取 'blue' 值（蓝色）
alpha(@color); // 从颜色值中提取 'alpha' 值（透明度）
luma(@color); // 从颜色值中提取 'luma' 值（亮度的百分比表示法）
saturate(@color, 10%); // 饱和度增加 10%
desaturate(@color, 10%); // 饱和度降低 10%
lighten(@color, 10%); // 亮度增加 10%
darken(@color, 10%); // 亮度降低 10%
fadein(@color, 10%); // 透明度增加 10%
fadeout(@color, 10%); // 透明度降低 10%
fade(@color, 50%); // 设定透明度为 50%
spin(@color, 10); // 色相值增加 10
mix(@color1, @color2, [@weight: 50%]); // 混合两种颜色
greyscale(@color); // 完全移除饱和度，输出灰色
contrast(@color1, [@darkcolor: black], [@lightcolor: white], [@threshold: 43%]); // 如果 @color1 的 luma 值 > 43% 输出 @darkcolor，否则输出 @lightcolor
multiply(@color1, @color2);
screen(@color1, @color2);
overlay(@color1, @color2);
softlight(@color1, @color2);
hardlight(@color1, @color2);
difference(@color1, @color2);
exclusion(@color1, @color2);
average(@color1, @color2);
negation(@color1, @color2);
iscolor(@colorOrAnything); // 判断一个值是否是颜色
isnumber(@numberOrAnything); // 判断一个值是否是数字（可含单位）
isstring(@stringOrAnything); // 判断一个值是否是字符串
iskeyword(@keywordOrAnything); // 判断一个值是否是关键字
isurl(@urlOrAnything); // 判断一个值是否是url
ispixel(@pixelOrAnything); // 判断一个值是否是以px为单位的数值
ispercentage(@percentageOrAnything); // 判断一个值是否是百分数
isem(@emOrAnything); // 判断一个值是否是以em为单位的数值
isunit(@numberOrAnything, "rem"); // * 判断一个值是否是指定单位的数值
```
