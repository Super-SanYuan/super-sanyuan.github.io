---
title: JavaScript简介
date: 2019-12-31 16:01:47
tags:
  - JavaScript
categories:
  - JavaScript
---

#### JavaScript --> 简称 js

> JavaScript 历史

​ 1995 年，网景公司希望能在静态 HTML 页面上添加一些动态效果, 让 Brendan Eich 设计出了 JavaScript 语言(用时 2 周)

> JavaScript 分为三个部分:

- ECMAScript 标准----js 的基本语法
- DOM---Document Object Model 文档对象模型
- BOM---Browser Object Model 浏览器对象模型

> JavaScript 是什么?

- 是一门脚本语言
- 是一门解释性语言
- 是一门弱类型的语言
- 是一门动态类型的语言
- 是一门基于对象的语言

> JavaScript 代码写在哪里

```javascript
第一种:写在html文件中-->使用script标签包裹代码
<script>
	alert('这对script标签中的就是js代码)
</script>
第二种:可以单独写在js文件中-->js文件中不需要使用<script>标签
```

> `<script>`标签的属性:

- src 表示要引入的外部文件
- type 表示脚本语言的类型 text/javascript,默认值就是它.
- language 已废弃。原来用于代码使用的脚本语言。由于大多数浏览器忽略它，所以不要用了。
- defer：可选。(等页面加载完成后,才执行 js)表示脚本可以延迟到文档完全被解析和显示之后再执行。由于大多数浏览器不支持，故很少用。
- charset：可选。表示通过 src 属性指定的字符集。由于大多数浏览器忽略它，所以很少有人用它。
- async:可选,能简单实现 js 的异步加载.

> 注意事项

- `<script>`标签尽量放在`<body>`标签内,放在结束的`</body>`标签前
- 一个`<script>`标签如果用于引入外部 js 文件,就不要在标签内写 script 代码
- html 文件中可以同时存在多对`<script>`标签,浏览器会依次解析执行
