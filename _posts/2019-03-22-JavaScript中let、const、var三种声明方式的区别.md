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
function foo(){
   var a = 2;//此处声明的变量a为函数foo的局部变量
   console.log(a);//2
}
foo();
console.log(a);//1
```
