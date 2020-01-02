---
title: js基本语法
date: 2020-01-02 19:43:17
tags:
  - JavaScript
categories:
  - JavaScript
---

```
知识点:
  - 变量
  - 注释
  - 数据类型
  - 运算符
```

### 变量

> 变量---区分大小写

```javascript
// 变量的作用: 用来操作数据的(可以存储,可以读取)
var admin // 变量的声明->只声明,没有赋值
var name = '周杰伦' // 变量的初始化->声明并赋值

// 1.使用var关键字(variable:可变的量)
var uname // undefined
uname = '周杰伦' //赋值

// 2.声明变量即赋值(推荐)
var unam = '周杰伦'

// 3.声明多个变量
var unam = '周杰伦',
  age = 20
```

> 变量名的注意问题---变量名的命名规范,要遵循驼峰命名法

    * 1.变量的名字要有意义,
    * 2.变量名有一定的规范:一般以字母,$符号,下划线开头,中间或者后面可以有$符号,字母,数字
    * 3.变量名一般都是小写的
    * 4.变量名如果是多个单词,第一个单词的首字母是小写的,后面的所有的单词的首字母都是大写的,这种命名方式称为:驼峰命名法
    * 5.不能使用关键字(系统自带的一些单词,不能使用)
    * 6.不会单词用拼音,拼音也要遵循驼峰命名法

### 注释

```javascript
//注释是解释代码的含义,浏览器不会对注释内容进行解析执行

// 单行注释

/*
 * 多行注释
 * 建议在代码关键处添加注释
 * 不写注释-->写的时候只有你和上帝看的懂,写完之后你的代码只有上帝看得懂
 **/

/**
 * 另外一种多行注释
 */
```

### 数据类型

```javascript
// 原始数据类型(6种)
var num = 10 //number 数字类型(整数和小数)
var str = '周杰伦' //string 字符串类型(一般用单引号或双引号包裹)
var flag = true //boolean 布尔类型(值只有两个 true(真/1) false(假/0))
var nll = null //null 空类型 值只有一个null 一个对象指向为空,可以赋值为null
var undef //undefined 未定义值只有一个undefined(变量声明了,没有赋值 函数没有返回值)
var obj = new Object() //object 对象

NaN // 特殊(not an number) undefined加数字会出现NaN

// 获取数据类型
typeof num // number
typeof num // number
```

###　类型转行

> 其他类型转数字类型

```javascript
// 转整数
parseInt('10') // 10 转整数
parseInt('12abc') // 12
parseInt('1a1') // 1 遇到非数字就停止
parseInt('abc12') // NaN

// 转数字
Number('10') // 10
Number('12abc') // NaN
Number('1.1') // 1.1
Number('abc12') // NaN

// 转小数
parseFloat('12') // 10
parseFloat('12.12') // 12.12
parseFloat('abc12') // NaN
```

> 其他类型转字符串

```javascript
// 如果变量有意义调用.tostring（）使用转换  // undefined(无意义)
// 如果变量没有意义使用string（）转换
var num = 20
num.toString() // '20'
String(num) // '20'
```

> 其他类型转布尔类型

```javascript
// console.log(Boolean(1)) //true
// console.log(Boolean(0)) //false
// console.log(Boolean(11)) //true
// console.log(Boolean(-10)) //true
// console.log(Boolean("哈哈")) //true
// console.log(Boolean("")) //false
// console.log(Boolean(null)) //false
// console.log(Boolean(undefined)) //false
```

### 运算符

```javascript
// 算数运算符:  +  -  *  /  %
// 算数运算表达式:由算数运算符连接起来的表达式

// 一元运算符: 这个操作符只需要一个操作数就可以运算的符号  ++  --
// 二元运算符: 这个操作符需要两个操作数就可以运算,
// 三元运算符: 10 == 10 ? true:false

// 复合运算符: +=  -=  *=  /=  %=
// 复合运算表达式:由复合运算符连接起来的表达式

// 关系运算符: >  <  >=  <=  ==不严格的 ===严格的 !=不严格的不等 !==严格的不等
// 关系运算表达式:由关系运算符连接起来的表达式
// 关系运算表达式的结果是布尔类型

// 逻辑运算符:
// &&---逻辑与--并且
// ||---逻辑或---或者
// !---逻辑非---取反--取非
// 逻辑运算表达式:由逻辑运算符连接起来的表达式
// 表达式1 && 表达式2
// 如果有一个为false,整个的结果就是false
// 表达式1 || 表达式2
// 如果有一个为true,整个的结果为true

// !表达式1 取反
// 表达式1的结果是true,整个结果为false
// 表达式1的结果是false,整个结果为true

// 赋值运算符:  =
var num = 12
```

### 一元运算符

```javascript
// 基础  ++与--
var num = 10
num++ // 相当于num = num + 1 输出 11
num-- // 相当于num = num - 1 输出 9

// 进阶
var num = 10
var sum = num++ + 10 // sum = 20
// 如果++在后面：如上： num++ + 10参与运算
// 先运算 再加加

var sum1 = ++num + 10 // sum1 = 21
// 如果++在前面 如上： ++num + 10
// 先加加 再运算加10
```
