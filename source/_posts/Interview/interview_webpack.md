---
title: 八股文之webpack
tags: 构建工具
categories:
  - Interview
cover: cover_interview_webpack.webp
abbrlink: 7ed814e6
date: 2021-06-07 20:03:30
---

### 一、webpack的介绍和安装

1. **正常项目下的目录结构**

* dist：distribution  需要发布时直接将该文件给服务器发布
* src：开发的东西放这里，打包后放入dist文件夹
* js：存放js文件
* node_modules
* main.js    (index.js)  ：项目入口文件
* index.html：入口页面
* package.json
* package-lock.json
* webpack.config.js

2. **一般情况下，任何一个项目都有一个本地的webpack包，因为你这项目所依赖的webpack很有可能和全局的webpack是不一样的；比如项目依赖的webpack是3.x.x版本，你本机全局webpack也为3.x.x版本，但是同事本机webpack全局为4.x.x版本，那么你们各自在本机输入 webpack调用全局 webpack进行打包，打包结果就会不一致或者出错，那么此时若是能够都使用本地项目所依赖的webpack打包就会避免此类问题；所以一般情况下，任何一个项目都会有本地依赖webpack，而调用本地webpack进行打包的方式有两种**：

   * npm 的npx命令，`npx webpack`    执行 `node_modules/.bin/webpack`
   * npm 的`scripts`字段，即npm包脚本命令,`npm run ..`会执行该字段中对应的命令，在package.json文件中自定义的`scripts`字段会优先在本地依赖中查找webpack并执行，若没有才会去全局查找webpack命令执行打包操作

   ```java
   {
     "name": "webpackstudy",
     "version": "1.0.0",
     "description": "",
     "private": true,
     "main": "index.js",
     "scripts": {
       "test": "echo \"Error: no test specified\" && exit 1",
       "build": "webpack"		//执行 npm run build  即执行 webpack命令 进行打包，但是会优先使用本地依赖，而不是全局依赖
     },
     "keywords": [],
     "author": "",
     "license": "ISC",
     "devDependencies": {
       "webpack": "^4.43.0",	//项目运行不依赖webpack，即webpack为开发时依赖
       "webpack-cli": "^3.3.12"
     },
     "dependencies": {			
       "lodash": "^4.17.15"	//lodash 运行时依赖
     }
   }
   ```

   * **注意：只要是在终端中输入命令，都是全局的，即在终端中输入`webpack` 即使用的就是全局的**

### 二、Webpack五个核心概念

1. **Entry**：入口（Enrty）指示Webpack以哪个文件为入口起点开始打包，分析构建内部依赖图。

2. **Output**：输出（Output）指示webpack打包后的资源bundles输出到哪里去，以及如何命名。

3. **Loader**：loader让Webpack能够去处理那些非JavaScript文件（webpack自身只理解JavaScript）。

4. **Plugins**：插件（plugins）可以用于执行范围更广的任务。插件的范围包括：从打包优化和压缩，一直到重新定义环境中的变量等。

5. **Mode**：模式（Mode）指示webpack使用相应模式（development/production）。

   |    选项     |                             描述                             | 特点                       |
   | :---------: | :----------------------------------------------------------: | -------------------------- |
   | development | 会将process.env.NODE_ENV的值设为development。启用NamedChunksPlugin和NamedModulesPlugin。 | 能让代码本地调试运行的环境 |
   | production  | 会将process.env.NODE_ENV的值设为production。启动FlagDependencyUsagePlugin,FlagIncludedChunksPlugin,ModuleConcatenationPlugin,NoEmitOnErrorsPlugin，OccurenceOrderPlugin,SideEffectsFlagPlugin和UglifyPlugin。 | 能让代码优化上线运行的环境 |

### 二、loader

1. **样式需要两个loader**

   * **css-loader**：css-loader只负责加载css文件，并不解析样式，
   * **style-loader**：style-loader可以解析样式，即将样式添加到dom中

   ```javascript
   module.exports = {
     mode: 'development',
     entry: './src/main.js',
     output: {
       filename: 'bundle.js',
       path: path.resolve(__dirname, 'dist'),
     },
     module: {
       rules: [
         {
           test: /\.css$/,
           // css-loader只负责加载css文件，并不解析样式，style-loader可以解析样式，即将样式添加到dom中
           // 使用多个loader时是从右向左的
           // use: [{ loader: 'css-loader' }, { loader: 'style-loader' }],  //此时先加载style-loader会报错
           use: [{ loader: 'style-loader' },{ loader: 'css-loader' } ],  //正确加载顺序
         },
       ],
     },
   }
   ```

2. **图片加载  url-loader   file-loader**

   ![](E:\Projects\Markdown\images\webpack图片loader.png) 

   我们发现，webpack自动帮助我们生成一个非常长的名字

   * 这是一个32位的hash值，目的是为了防止名字重复
   * 但是在真实开发中，我们可能对打包的图片名字有一定的要求
   * 比如，将所有的图片放在一个文件夹中，跟上原来图片的名称，同时也要防止重复 `img/name.hash:8` ，hash默认32位   :8可以截取8位

   所以，我们在options添加如下选项：

   * img：文件要打包到的文件夹
   * name：获取图片原来的名字，放在该位置
   * hash:8：为了防止图片名字冲突，依然使用hash，但是我们只保留了8位
   * ext：使用图片原来的扩展名

   但是，我们发现图片没有显示出来，这是因为图片使用的路径不正确

   * 默认情况下，webpack会将生成的路径直接返回给使用者
   * 但是，我们整个程序是打包在dist文件夹下的，所以这里我们需要在路径下再添加一个 dist/

   ```javascript
   
   module.exports = {
     mode: 'development',
     entry: './src/main.js',
     output: {
       filename: 'bundle.js',
       path: path.resolve(__dirname, 'dist'),
       publicPath:'dist/'   //所有带url的都需要配置输出 publicPath  但是最后将index.html放进dist文件夹中后就不需要publicPath了，删除即可
     },
     module: {
       rules: [
         {
           test: /\.scss$/,
           use: [{ loader: 'style-loader' }, { loader: 'css-loader' }, { loader: 'sass-loader' }], //正确加载顺序
         },
         {
           test: /\.(png|jpg|gif)$/,
           use: [
             {
               loader: 'url-loader',
               options: {
                 // 当加载的图片小于limit时，会将图片编译成base64字符串形式，不需要文件来存储
                 // 若大于limit则会使用file-loader对图片进行加载,而file-loader不需要配置，只需要安装一下就行了，但是需要图片需要打包存储，否则显示				//加载成功但是图片显示不出来
                 limit: 8192,
                 name:'img/[name].[hash:8].[ext]'
               },
             },
           ],
         },
       ],
     },
   };
   ```

3. **ES6转ES5**

   如果你仔细阅读webpack打包的js文件，发现写的ES6语法并没有转成ES5，那么就意味着可能一些对ES6还不支持的浏览器没有办法很好的运行我们的代码。

   在前面说过，如果需要将ES6的语法转位ES5，那么就需要使用**babel**，而在webpack中，我们直接使用babel对应的loader就可以了。