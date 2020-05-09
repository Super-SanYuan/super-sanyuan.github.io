---
title: React-初体验
date: 2020-05-09 14:24:32
tags:
  - React
categories:
  - React
---

## 从 JS 基本语法去理解 React

实现创建元素并且加入到页面进行渲染

第一版
实现功能:

- 1、创建节点元素
- 2、元素嵌套
- 3、元素渲染到页面

```js
const div = document.createElement('div')
const p = document.createElement('p')
const span = document.createElement('span')
div.appendChild(p)
p.appendChild(span)
span.innerText = '我是一个span'
document.body.appendChild(div)
```

第二版 代码优化:

- 1、将重复的 document.createElement() 提取成一个函数方法
- 2、方法接受一个 tagName 返回创建好的元素

```js
function createElement(tagName) {
  return document.createElement(tagName)
}
const div = createElement('div')
const p = createElement('p')
const span = createElement('span')
div.appendChild(p)
p.appendChild(span)
span.innerText = '我是一个 span'
document.body.appendChild(div)
```

第三版 继续优化:

- 1、方法接受第二个参数 参数值可以是一个元素节点 也可以是元素节点需要渲染的内容
- 2、将函数调用提取到一个函数方法中 返回一个组装好了子元素或内容的的元素节点

```js
function createElement(tagName, childer) {
  let parent = document.createElement(tagName)
  if (childer) {
    if (typeof childer === 'string') {
      let child = document.createTextNode(childer)
      parent.appendChild(child)
    } else {
      parent.appendChild(childer)
    }
  }
  return parent
}

function render() {
  return createElement(
    'div',
    createElement('p', createElement('span', '我是一个 span'))
  )
}
document.getElementById('root').appendChild(render())
```

## React 思想推导

使用 React 实现 JS 模拟实现的最终版

```js
import React, { useState } from 'react'
import ReactDom from 'react-dom'
```

第一版 :暂时不考虑 render 内部实现原理

- 通过 React.createElement 创建 节点对象
- 通过 ReactDom.render 渲染

```js
function Node() {
  return React.createElement(
    'div',
    null,
    React.createElement(
      'p',
      null,
      React.createElement('span', null, '我是 React 实现节点创建')
    )
  )
}

ReactDom.render(<Node />, document.getElementById('root'))
```

第二版: 加入 JSX

- 每次要写 React.createElement 实在太繁琐了
- 于是 React 提供了 JSX 语法

```js
const Node = (
  <div>
    <p>
      <span>我是 React JSX 创建的节点</span>
    </p>
  </div>
)

ReactDom.render(<Node />, document.getElementById('root'))
```

## React 组件

React 组件提供了 class 类写法与函数式组件写法

### 函数式组件

第一版:

- 事件无法传参

```js
function App() {
  const [n, setN] = useState(1)
  function onClick() {
    setN(n + 1)
  }
  return (
    <div>
      <p>
        <span>这是 React 函数式组件 {n} </span>
        <button onClick={onClick}>+1</button>
      </p>
    </div>
  )
}
ReactDom.render(<App />, document.getElementById('root'))
```

### 函数式组件

第二版:

- 利用闭包实现事件传参

```js
function App() {
  const [n, setN] = useState(1)
  function onClick(step) {
    setN(n + step)
  }
  return (
    <div>
      <p>
        <span>这是 React 函数式组件 {n} </span>
        <button onClick={() => onClick(2)}>+1</button>
      </p>
    </div>
  )
}
ReactDom.render(<App />, document.getElementById('root'))
```

### class 类 组件

```js
class App extends React.Component {
  constructor(props) {
    super(props)
    this.state = { count: props.count }
  }
  render() {
    return (
      <div>
        <p>
          <span>我是 React class 类 创建的组件 {this.state.count}</span>
          <button onClick={() => console.log(this)}>this</button>
        </p>
      </div>
    )
  }
}

ReactDom.render(<App count={1} />, document.getElementById('root'))
```
