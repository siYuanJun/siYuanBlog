---
title: hexo个性Url插件
tags: hexo插件集合
abbrlink: f3d8
date: 2020-07-25 13:01:47
---

### 导语
由于hexo缺省的文章连结是依照年/月/日/标题设定，而网址名称若是中文的话会被编译成ASCII码，而变得相当冗长以及不好看，而且修改标题的话网址会变更及失效，像我这种事后有空才会再次修改旧文章的就不适合使用，所以就使用该插件把网址变得稍微美观以及缩短网址。

### [hexo-abbrlink](https://github.com/rozbo/hexo-abbrlink)

#### hexo-uuid

当然，也可以使用另一个插件 `hexo-uuid` ，不过我是觉得变成网址没有 `hexo-abbrlink` 好看。

`https://www.xxx.com/posts/2f2dd790-1e71-11e6-95e1-ffc09ba0b0`

#### hexo-abbrlink

1. crc16 & hex
`https://www.xxx.com/posts/3ab2`

2. crc16 & dec
`https://www.xxx.com/posts/12345.html`

3. crc32 & hex
`https://www.xxx.com/posts/9a8b6c4d.html`

4. crc32 & dec
`https://www.xxx.com/posts/1690090958.html`

其中 dec 表示十进制
hex 表示十六进制
使用 git bash 安装 `hexo-abbrlink`

```
npm install hexo-abbrlink --save
```

更改站点目录的 `config.yml`
像我想要让人知道我是用静态网页 就在最后面加上 `.html` ，所以可加可不加

```
permalink:  posts/:abbrlink.html
permalink_defaults:
abbrlink:
  alg: crc16
  rep: hex
```

`https://www.xxx.com/3ab2`

### 自定义格式

```
permalink_defaults:
  author_name: siyuanjun
permalink: :author_name/:abbrlink
```

https://www.xxx.com/siyuanjun/3ab2
一切端看个人喜好。

### 参考数据：[siYuanJun-Blog](http://blog.lvtcn.com/)

> 发掘链接：https://www.dazhuanlan.com/2019/12/04/5de7c9db4b972