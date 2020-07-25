---
title: gulp之压缩css，less转css
date: 2020-7-20
tags: 'gulp, css, Less'
abbrlink: f859
---

> 废话不多说上代码, 须有些 npm 经验！

#### package.json
```
{
  "name": "default",
  "version": "1.0.0",
  "description": "...",
  "main": "index.js",
  "scripts": {
    "test": "npm run test"
  },
  "repository": {
    "type": "git",
    "url": "no"
  },
  "keywords": [
    "..."
  ],
  "author": "siYuan",
  "license": "ISC",
  "devDependencies": {
    "gulp": "^4.0.2",
    "gulp-autoprefixer": "^7.0.1",
    "gulp-less": "^4.0.1",
    "gulp-minify-css": "^1.2.4"
  },
  "dependencies": {
    "require": "^2.4.20"
  }
}

```

#### gulpfile.js
```
var gulpfile = require("gulp"),
  less = require("gulp-less"),
  auto = require("gulp-autoprefixer"),
  minify_css = require("gulp-minify-css");//css浏览器兼容前缀

let cssFile = "./public/static/default";

gulpfile.task('compileLess', done => {
  // console.log(done)
  //找到项目中less文件夹中所有文件夹下的所有less文件
  gulpfile.src(cssFile + "/less/**/*.less")
  //进行预编译处理,保持与引入的模块一致
    .pipe(less())
    .pipe(minify_css())
    .pipe(auto({
      grid: true,
      browsers: ['last 2 version']
    }))
    //编译后将less编译成的css文件保存到项目目录下的css文件夹中
    .pipe(gulpfile.dest(cssFile + '/css'))
  done();
});

// 通过watch方法实时监测所有less文件，如果发生更改，执行compileLess方法
gulpfile.task('watch', function () {
  gulpfile.watch(cssFile + '/less/**/*.less', gulpfile.series('compileLess'));
})
```
