---
title: webpack-03-loader
date: 2020-04-22 23:15:21
tags:
  - webpack
categories:
  - webpack
---
## loader

loader 用于对模块的源代码进行转换. loader 可以使你在 `import` 或 "加载" 模块时预处理文件. loader 可以将文件从不同的语言转换为 JavaScript, 或将内联图像转换为 data URL, loader 甚至允许直接在 JavaScript 模块中 `import` CSS 文件

## 特性

- loader 支持链式传递, 一组链式的 loader 按照相反的顺序执行, loader 链中的第一个 loader 返回值给下一个 loader. 在最后一个 loader 返回 webpack 所预期的 JavaScript
- loader 可以是同步的, 也可以是异步的
- loader 运行在 Node.js 中, 并且能够执行任何可能的操作
- loader 接受查询参数, 用于对 loader 传递配置
- loader 也能够使用 options 对象进行配置
- 除了使用 `package.json` 常见的 `main` 属性, 还可以将普通的 `npm` 模块导出为 loader, 做法是在 `package.json` 里定义一个 loader 字段
- 插件(plugin)可以为 loader 带来更多特性
- loader 能够产生额外的任意文件

## css-loader

可以使用 loader 告诉 webpack 加载 CSS 文件

先安装对应的loader

```shell
npm install -D css-loader
```

然后配置 `webpack.config.js` 文件, 告诉 webpack 对每个 `.css` 使用 css-loader

```js
module.exports = {
  module: {
    rules: [
      {
        test: /\.css$/,
        use: [
          {
            loader: 'style-loader'
          },
          {
            loader: 'css-loader',
            options: true
          }
        ]
      }
    ]
  }
}
```
