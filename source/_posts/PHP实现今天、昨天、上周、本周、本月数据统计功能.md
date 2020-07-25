---
title: PHP实现 今天、昨天、上周、本周、本月 数据统计功能
date: 2020.6.5
tags: 'php, 时间统计'
abbrlink: d03
---

### PHP实现 今天、昨天、上周、本周、本月 数据统计功能

### 应用场景

> 按今天、昨天、上周、本周、本月 统计某个人发布文章数量

### 原理分析

> 假设 文章表里 有一个字段存储 创建文章时间戳（cdate），比如说 今天（2016-11-8） 那么查询条件 为 cdate >= 2016-11-8 00:00 AND cdate <= 2016-11-8 23:59

### 实现方案

> 根据以上分析，需要知道今日开始时间戳和结束时间戳, 那么昨天、上周、本周也类似。使用PHP 的mktime 函数 可获得开始时间戳和结束时间戳。

### mktime()

> 语法：mktime(hour,minute,second,month,day,year)

|参数|描述|
|:---|:---|
|hour|可选,规定小时|
|minute|可选,规定分钟。|
|second|可选,规定秒|
|month|可选,规定用数字表示的月|
|day|可选,规定天|
|year|可选,规定年|

### 代码实现

```
//php获取今日开始时间戳和结束时间戳
$today_start=mktime(0,0,0,date('m'),date('d'),date('Y'));
$today_end=mktime(0,0,0,date('m'),date('d')+1,date('Y'))-1;

//php获取昨日起始时间戳和结束时间戳
$yesterday_start=mktime(0,0,0,date('m'),date('d')-1,date('Y'));
$yesterday_end=mktime(0,0,0,date('m'),date('d'),date('Y'))-1;

//php获取上周起始时间戳和结束时间戳
$lastweek_start=mktime(0,0,0,date('m'),date('d')-date('w')+1-7,date('Y'));
$lastweek_end=mktime(23,59,59,date('m'),date('d')-date('w')+7-7,date('Y'));

//php获取本周周起始时间戳和结束时间戳
$thisweek_start=mktime(0,0,0,date('m'),date('d')-date('w')+1,date('Y'));
$thisweek_end=mktime(23,59,59,date('m'),date('d')-date('w')+7,date('Y'));

//php获取本月起始时间戳和结束时间戳
$thismonth_start=mktime(0,0,0,date('m'),1,date('Y'));
$thismonth_end=mktime(23,59,59,date('m'),date('t'),date('Y'));
```
