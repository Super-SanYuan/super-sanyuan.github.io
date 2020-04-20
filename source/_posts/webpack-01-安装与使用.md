---
title: webpack-01-安装与使用
date: 2020-04-20 21:16:47
tags:
  - webpack
categories:
  - webpack
---

> 前提: 请确保安装了 Node.js 的最新版本

## webpack

webpack 是一个现代 JavaScript 应用程序的静态模块打包器(module bundler) 当 webpack 处理应用程序时, 它会递归地构建一个依赖关系图(dependencygraph) 其中包含应用程序需要的每个模块, 然后将所有这些模块打包成一个或多个bundle

## 初始化项目

```shell
mkdir webpack-dmeo # 创建项目文件夹
cd webpack-demo # 进入项目目录
npm init -y # 默认配置初始化
```

出现 package.json 信息, 表示初始化成功

```json
// package.json
{
  "name": "webpack-demo",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "webpack": "^4.42.1",
    "webpack-cli": "^3.3.11"
  }
}
```

## 两种安装

### 全局安装

```shell
npm install -g webpack
```

### 本地安装

```shell
# 安装最新版本
npm install --save-dev webpack 

# 如果使用 weboack4+ 版本 还需要安装 CLI
npm install --save-dev webpack-cli
```

## webpack 命令使用方式

### 项目目录运行

```shell
# webpack-demo 目录中
./node_modules/.bin/webpack --sersion
# ---> 4.42.1
```

### NPM script命令运行

添加 script 脚本

```json
{
  "name": "webpack-demo",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "build": {
    "webpack": "webpack --version"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "webpack": "^4.42.1",
    "webpack-cli": "^3.3.11"
  }
}
```

```shell
npm run build
# ---> 4.42.1
```

### 全局运行

```shell
# 需要全局安装webpack
webpack --version
# ---> 4.42.1
```