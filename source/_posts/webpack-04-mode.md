---
title: webpack-04-mode
date: 2020-04-25 14:46:49
tags:
  - webpack
categories:
  - webpack
---

## 模式

提供 `mode` 配置选项, 告知 webpack 使用相应的模式的内置优化

## 用法

只在配置中提供 `mode` 选项

```js
module.exports = {
  mode: 'production', // 生产环境
}
```

或者在 CLI 参数中传递

```shell
webpack --mode=production
```

## 选项

- development:
  会将 `process.env.NODE_ENV` 的值设为 `development`. 启用 `NamedChunksPlugin` 和 `NamedModulesPlugin`

- production:
  会将 `process.env.NODE_ENV` 的值设为 `production`. 启用 `FlagDependencyUsagePlugin`, `FlagIncludedChunksPlugin`, `ModuleConcatenationPlugin`, `NoEmitOnErrorsPlugin`, `OccurrenceOrderPlugin`, `SideEffectsFlagPlugin` 和 `UglifyJsPlugin`.

## codes

mode: development

```js
// webpack.development.config.js
module.exports = {
+ mode: 'development'
- plugins: [
-   new webpack.NamedModulesPlugin(),
-   new webpack.DefinePlugin({ "process.env.NODE_ENV": JSON.stringify("development") }),
- ]
}
```

mode: production

```js
// webpack.development.config.js
module.exports = {
+ mode: 'development'
- plugins: [
-   new webpack.NamedModulesPlugin(),
-   new webpack.DefinePlugin({ "process.env.NODE_ENV": JSON.stringify("development") }),
- ]
}
```
