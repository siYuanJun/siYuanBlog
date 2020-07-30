---
title: input便签插件
categories: Plugins
tags: 'jquery, input'
abbrlink: '1767'
date: 2020-07-27 22:15:12
---

### jquery input 方便标签插件

```
<script src="http://xoxco.com/examples/jquery.tagsinput.js"></script>
<link rel="stylesheet" href="http://xoxco.com/examples/jquery.tagsinput.css">

<script>
$(function() {
	$('#tag').tagsInput({
		'width':'600',
		'defaultText':'新增'
	});
})
</script>

<input name="tag" type="text" id="tag" value="热销商品,年度商品" />
```