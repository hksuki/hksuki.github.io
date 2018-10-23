---
title: windows搭建nodejs开发环境
date: 2018-10-22 22:39:45
category: web开发
tags: 
- web开发 
- nodejs
---

# windows搭建nodejs开发环境

<!-- TOC -->

- [windows搭建nodejs开发环境](#windows搭建nodejs开发环境)
    - [安装express](#安装express)
    - [建立express工程，启动第一个项目](#建立express工程启动第一个项目)
        - [建立工程](#建立工程)
    - [参考文献](#参考文献)

<!-- /TOC -->

听说从nodejs入手实现简单的全栈网站开发比较容易，并且考虑到下一步可能需要开发一些简单的业务查询系统，准备捣鼓捣鼓nodejs，本博客本身就是使用[Hexo](https://hexo.io/)搭建的。
最近听说[express](http://www.expressjs.com)是nodejs的一个好用的网站框架，其中文网站是[express中文](http://www.expressjs.com.cn)。现在就简单讲下我是如何在windows下搭建一个简单的express开发环境的。

## 安装express

因为nodejs拥有好用的包管理器——`npm`，所以express的安装十分简单：

``` bash
npm install express -g
```

但是此时直接运行`express -v`命令的话会出现以下问题：

{% asset_img  express_cmd_error.JPG %}

这表示在环境变量中没有存在express命令。这个就和当时hexo的安装不同了。经过查询资料了解，**在express 4.x版本中将命令行工具分离出来了**。因此需要再安装一个工具：`express-generator`。

```bash
npm install express-generator -g
```

此时再运行`express`命令发现可以正常操作

{% asset_img express_cmd_ok.JPG %}

## 建立express工程，启动第一个项目

### 建立工程

```powershell
> mkdir express_demo
> cd express_demo
> code app.js
```

此时在文件夹下面会生成一个package.json文件，此时我们编写我们的页面，参照官方文档的[hello world example](http://www.expressjs.com.cn/starter/hello-world.html)

```js
const express = require('express')
const app = express()

app.get('/', (req, res) => res.send('Hello World!'))

app.listen(3000, () => console.log('Example app listening on port 3000!'))
```

此时直接运行`node app.js`，你会发现以下错误：

{% asset_img module_error.JPG %}

在网上查资料显示，这是因为没有找到`express`模块所致，因此需要添加`NODE_PATH`环境变量，在Windows上，默认的位置是`C:\Users\user\AppData\Roaming\npm\node_modules`，此时再打开一个新的终端，运行`node app.js`就可以将网站启动起来的。

{% asset_img hello_web.JPG %}

此时就完成了`express`环境的搭建。

## 参考文献

1. [准备Nodejs开发环境Ubuntu](http://blog.fens.me/nodejs-enviroment)
2. [nodejs require模块找不到怎么解决](https://jingyan.baidu.com/article/2d5afd6937ad7785a2e28e98.html)
3. [Hello world example](http://www.expressjs.com.cn/starter/hello-world.html)
