---
title: webpack-02-入口与出口
date: 2020-04-21 22:58:29
tags:
  - webpack
categories:
  - webpack
---
## 入口(entry)

**入口起点**(entry point)指示 webpack 应该使用哪个模块, 来作为构建其内部依赖图的开始. 进入入口后, webpack 会找出有哪些模块和库是入口起点(直接和简介)依赖的

### 属性

- entery: String|Array<string>

### CODE

`entry` 属性的单个入口语法

```js
// 简写
module.exports = {
  entry: './src/index.js'
}
// 非简写
module.exports = {
  entry: {
    main: './src/index.js'
  }
}
```

`entry` 多入口写法 - 对象写法: 

用法: `entry: {[entruChunkName: string]: string|Array<string>}

```js
const config = {
  entry: {
    app: './src/app.js',
    vendors: './src/vendors.js'
  }
}
module.exports = config
```

> 可应用于多页面程序

## 出口(output)

**output**属性告诉 webpack 在哪里输出它所创建的 bundles, 以及如何命名这些文件, 默认值为 `./dist`. 整个应用程序结构, 都会被编译到指定的输出路径的文件夹中, 

### 属性

- output: Object `output` 选项可以控制 webpack 如何向硬盘写入编译文件
  - filename: String 打包后的文件名
  - path: String 打包输出路径

### CODE

单入口

```js
// 借助 NodeJS 的 path 核心模块
const path = require('path')
module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist')
  }
}
```

多个入口

```js
const config = {
  entry: {
    app: './src/app.js',
    search: './src/search.js'
  },
  output: {
    filename: '[name].js',
    path: __dirname + '/dist'
  }
}
// 写入到硬盘：./dist/app.js, ./dist/search.js
```

### 高级进阶

使用 CDN 和资源 hash 的复杂示例

```js
output: {
  path: '/home/proj/cnd/assets/[hash]',
  publicPath: "http://cdn.example.com/assets/[hash]/"
}
```

在编译时不知道最终输出文件的 publicPath 的情况下，publicPath 可以留空，并且在入口起点文件运行时动态设置。如果你在编译时不知道 publicPath，你可以先忽略它，并且在入口起点设置 __webpack_public_path__。

```js
__webpack_public_path__ = myRuntimePublicPath
```