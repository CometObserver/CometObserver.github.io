---
title: JavaScript中let/const/var三种声明方式的区别
tags: 数据库
categories: 
- JavaScript
- ECMAScript6
date: 2019-03-22
---

## 前言
ES6一共有6种声明变量的方法，除了ES5中两种声明变量的方法：var命令和function命令外，ES6还添加let和const命令以及import命令和class命令。这里主要讨论var、let和const三种命令。

## var
关键词var声明的变量属于当前的函数作用域，如果声明是发生在任何函数外的顶层声明，那么这个变量就属于全局作用域。举例说明：
```
var a = 1; //此处声明的变量a为全局变量
function f(){
   var a = 2;//此处声明的变量a为函数f的局部变量
   console.log(a);//2
}
f();
console.log(a);//1
```

如果在声明变量时，省略 var 的话，该变量就会变成全局变量，如全局作用域中存在该变量，就会更新其值。如：
```
var a = 1; //此处声明的变量a为全局变量
function f(){
    a = 2;//此处的变量a为全局变量
   console.log(a);//2
}
f();
console.log(a);//2
```

## let
ES6 新增了let命令，用来声明变量。它的用法类似于var，但是所声明的变量，只在let命令所在的代码块内有效。例如：
```
{
  let a = 10;
  var b = 1;
}

console.log(a);//Uncaught ReferenceError: b is not defined
console.log(b);//1
```

另外，let在同一个块级作用域，不能重复声明变量。如：
```
function f(){
    let a = 1;
    let a = 2;//Uncaught SyntaxError: Identifier 'a' has already been declared
}
```

## const
除了拥有let具有的特点外，const声明一个只读的常量。一旦声明，常量的值就不能改变。如下，改变PI的值就会报错：
```
const PI = 3.14;
PI // 3.14

PI = 3;
// TypeError: Assignment to constant variable.
```

但是，并不是说 const 声明的变量其内部内容不可变，如：
```
const obj = {a:1,b:2};
console.log(obj.a);//1
obj.a = 2;
console.log(obj.a);//2
obj = {};//报错
```
上面代码中，常量obj储存的是一个地址，这个地址指向一个对象。不可变的只是这个地址，即不能把obj指向另一个地址，但对象本身是可变的，所以依然可以为其添加新属性。

## 变量提升
变量提升是指无论 var 出现在一个作用域的哪个位置，这个声明都属于当前的整个作用域，在其中到处都可以访问到。注意只有变量声明才会提升，对变量赋值并不会提升。例如：
```
console.log(a);//undefined
var a = 1;
```
上面的代码等同于：
```
var a;
console.log(a);//undefined
a = 1;
```

let和const命令改变了语法行为，它所声明的变量一定要在声明后使用，否则报错。即不存在变量提升，例：
```
// let 的情况
console.log(bar); // 报错ReferenceError
let bar = 2;

// const 的情况
console.log(foo); // 报错ReferenceError
const foo = 2;
```

## 总结

| var         | let    | const    |
|--------------|---------|---------|
| 函数作用域   |块级作用域 | 块级作用域 |
| 变量提升  | 变量不提升  | 变量不提升 |
| /      | 存在暂时性死区 | 存在暂时性死区 |
| 允许重复声明  | 不能重复声明 | 不能修改 |
