---
title: webpack4+vue 的基本打包配置详解
date: 2020.6.2
tags: webpack4，vue
abbrlink: a61b
---

前提：确保已安装node，为了安装速度快一些，使用cnpm源，安装cnpm：npm i cnpm -g
注意：Mac环境下，操作全局环境，需要开启root权限，使用sudo npm i cnpm -g  （sudo表示开启root权限，其他操作全局的npm或者cnpm同理，需要在命令前面加上sudo）

### 1、安装webpack4
![](https://img-blog.csdnimg.cn/20181107163122114.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzM3ODk3MDEz,size_16,color_FFFFFF,t_70)
接下来全局安装webpack，进入项目根目录（webpack-study目录）的终端，输入命令：cnpm i webpack -g
输入命令webpack-v查看版本，发现会报如下提示：
![](https://img-blog.csdnimg.cn/20181107162306118.png)
因为webpack4开始，需要配套安装webpack-cli，输入no，因为webpack刚刚是全局安装的，所以webpack-cli也需要全局安装。
输入命令：cnpm i webpack-cli -g
安装完成后，再次输入webpack-v查看版本，如果出现下图所示版本号，则webpack4安装成功：
![](https://img-blog.csdnimg.cn/20181107162756533.png)

### 2、开始打包
输入命令 cnpm init 进行项目的初始化，成功之后，根目录下会多一个package.json文件。

安装jquery包： cnpm i jquery -D (-D 表示将安装的包保存在package.json文件中的devDependencies对象中）。

注意：一定加上-D，如果中途安装包出现错误的时候，把整个node_module包删掉，然后执行cnpm i命令，它会根据package.json文件中的配置去下载那些包。

接下来在index.html文件中输入以下代码：

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <h1 id="test"></h1>
    <script src="./index.js"></script>
</body>
</html>
```

在index.js文件中输入以下代码：

```
import $ from 'jquery'
$('#test').text('August')
```

浏览器中打开index.html文件，会发现控制台报错，因为import是ES6的语法，浏览器不能解析。

webpack4已经不能用webpack file1 file2来进行打包了，直接输入命令：webpack

webpack4会自动寻找src目录下的index.js文件，并将打包之后的文件，自动新建dist文件夹，并默认dist下的main.js文件就是打包生成的文件。

注意一定要有src目录下的index.js文件，否则会报错。

运行webpack命令之后，有这样的警告：
————————————————
版权声明：本文为CSDN博主「蒋蒋er」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/m0_37897013/article/details/83825990

![](https://img-blog.csdnimg.cn/20181107165250646.png)
webpack4需要指定生产还是开发模式，再次输入命令：webpack --mode development 指定开发模式，可以发现警告已经没有了。
但是每次输入这个命令比较繁琐，可以在package.json文件中的scripts对象中新增一条配置：
![](https://img-blog.csdnimg.cn/20181107170055199.png)
现在执行命令 npm run dev 就相当于webpack --mode development，可以把这个命令执行试一下。
最后，我们将index.html引入的js文件改成刚刚生成的main.js文件之后，再用浏览器打开index.html，可以看到代码成功生效了。
所以webpack的作用之一，就是将一些高级语法转换成浏览器可以识别的语法，兼容浏览器。

### 3、webpack配置文件
在根目录下新建文件webpack.config.js文件，注意，一定是这个名字，webpack打包时会自动寻找这个配置文件。
如果不想有src目录，也不想有index.js文件，想随便自定义自己的文件，这个时候就可以修改webpack配置文件。
在这个配置文件中输入：
```
const path = require('path')
module.exports = {
    entry: path.join(__dirname, './src/main.js'),//入口文件
    output: {
        path: path.join(__dirname, './dist'), //出口（打包后）文件路径
        filename: 'bundle.js' //出口（打包后））文件名
    }
}
```
entry指定的是你想要打包的入口文件，output指定的是打包后的出口文件，现在将src目录下的index.js文件重命名为main.js文件，并将dist文件夹删除，最后运行打包命令：npm run dev。
注：每次修改配置文件都需要重新运行打包命令。
![](https://img-blog.csdnimg.cn/20181108093349661.png)
如上图所示，webpack配置文件生效，最终将main.js文件打包成了bundle.js文件。
需要注意的是，index.html文件之前引入的是打包后的main.js文件，现在打包后文件我们指定为bundle.js文件，所以需要将index.html引入的js文件改为bundle.js，打开页面，能正常显示。

### 4、webpack-dev-server
假设现在有个需求，需要将页面内容的August改为September，很简单，只需要将src下main.js修改一下就行，问题是，由于html引用的是打包后文件，所以需要改完需要再执行打包命令。这个时候，假设又需要改回August了，你需要再修改，再打包，每次修改一点想看页面效果，都需要重新打包，这样太繁琐。
所以webpack-dev-server就出现了，它可以实时监听我们文件的变化，自动帮我们编译打包命令。
安装webpack-dev-server：cnpm i webpack-dev-server -D
安装之后出现下图所示警告：
![](https://img-blog.csdnimg.cn/20181108095321292.png)
由于webpack-dev-server依赖webpack，但是我们webpack是安装在全局的，需要再这个项目下安装局部的webpack，执行以下命令：
cnpm i webpack -D
cnpm i webpack-cli -D
安装成功之后，打开package.json文件，scripts中dev属性修改成如下代码：
```
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev": "webpack-dev-server --mode development"
  },
```
webpack-dev-server已经集成了webpack命令的作用，所以运行webpack-dev-server命令和webpack一样，只不过webpack-dev-server还能自动监听文件变化，自动打包。
运行命令：npm run dev
webpack-dev-server会自动启动一个本地服务器（webpack是基于node的），默认端口是8080，在浏览器输入localhost:8080,可以看到如下页面，说明安装配置成功：
到如下页面，说明安装配置成功：
![](https://img-blog.csdnimg.cn/20181108101253966.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzM3ODk3MDEz,size_16,color_FFFFFF,t_70)
这需要我们手动打开浏览器输入地址，webpack-dev-server提供了几个参数，可以执行完命令后，自动打开浏览器，package.json文件作如下修改：
```
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev": "webpack-dev-server --mode development --open 'google chrome' --port 3000"
},
```
如上配置意思是，默认以chrome浏览器打开，并修改默认端口为3000，保存文件后，重新运行npm run dev命令，可以发现浏览器已经自动打开了。

此外，还有几个参数：

--hot表示热加载，意思是默认每次重新编译都是生成一个新的打包文件，热加载则是你改了哪些，就局部更新打包文件的部分内容。

如果想局域网内其他主机也可以访问你的项目，需要增加配置，----host 0.0.0.0

如果想打开浏览器就能看到页面而不是这个目录结构，可以增加配置， --content-base src/

ps：除了可以在package.json文件中配置dev，还可以在webpack.config.js文件中通过devServer属性来修改配置。

然后我们修改main.js文件，改成September，然后刷新页面，发现并没有生效。

回头看下刚刚运行webpack-dev-server的命令后的提示信息：

![](https://img-blog.csdnimg.cn/20181108100639965.png)
第二行告诉我们它默认的output（生成的打包文件的输出目录）是/，也就是根目录，所以我们需要将index.html文件中的引入路径改为：
```
<!-- <script src="../dist/bundle.js"></script> -->
    <script src="/bundle.js"></script>
```
现在对main.js作任何修改都能不用执行打包命令，也不用刷 ... [更多详情请访问以下链接信息]

————————————————
原文链接：https://blog.csdn.net/m0_37897013/article/details/83825990