---
title: JavaScript编程风格归纳
tags: Web前端
categories: 
- JavaScript
- 技巧
date: 2020-02-12
---

## 概述
“编程风格”（programming style）指的是编写代码的样式规则。<br/>编程风格的选择不应该基于个人爱好、熟悉程度、打字量等因素，而要考虑如何尽量使代码清晰易读、减少出错。你选择的，不是你喜欢的风格，而是一种能够清晰表达你的意图的风格。这一点，对于JavaScript这种语法自由度很高的语言尤其重要。<br/>必须牢记的一点是，如果你选定了一种“编程风格”，就应该坚持遵守，切忌多种风格混用。如果你加入他人的项目，就应该遵守现有的风格。

## 我的风格
* ***缩进：*** 使用Tab键进行缩进。<br/>
  
* ***区块：*** 总是使用大括号表示区块，且起首的大括号跟在关键字的后面。<br/>
  
* ***圆括号：*** 
  1. 表示函数调用时，函数名与左括号之间没有空格。
  2. 表示函数定义时，函数名与左括号之间没有空格。
  3. 其他情况时，前面位置的语法元素与左括号之间，都有一个空格。<br/>
   
* ***行尾的分号：*** 
  1. 不使用分号的情况：
    * for和while循环&emsp; ***注意，*** do...while循环是有分号的。
    * 分支语句：if,switch,try
    * 函数的声明语句&emsp; ***注意，*** 函数表达式仍然要使用分号。
  2. 分号的自动添加：如果continue、break、return和throw这四个语句后面，直接跟换行符，则会自动添加分号。 ***不省略分号*** <br/>另外，不写结尾的分号，可能会导致脚本合并出错。所以，有的代码库在第一行语句开始前，会加上一个分号。<br/>
   
* ***全局变量&变量声明：*** 尽量少用全局变量，把变量声明都放在代码块的头部。<br/>
  
* ***相等(==)&严格相等(===)：*** 只使用严格相等。<br/>

* ***语句合并：*** 为了保证代码的可读性，不将不同目的的语句，合并成一行。<br/>

* ***自增和自减运算符：*** 自增（++）和自减（--）运算符尽量使用+=和-=代替。<br/>