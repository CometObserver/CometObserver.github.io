---
title: export default 和 export 区别
tags: Web前端
categories: 
- ES6
- JavaScript
date: 2019-04-20 
---

1. export与export default均可用于导出常量、函数、文件、模块等
2. 在一个文件或模块中，export、import可以有多个，export default仅有一个
3. 通过export方式导出，在导入时要加{ }，export default则不需要
4. 
   * 输出单个值，使用export default
   * 输出多个值，使用export
   * export default与普通的export不要同时使用
示例：
```
1.export
//a.js
export const str = "blablabla~";
export function log(sth) { 
  return sth;
}
对应的导入方式：

//b.js
import { str, log } from 'a'; //也可以分开写两次，导入的时候带花括号

2.export default
//a.js
const str = "blablabla~";
export default str;

其实此处相当于为str变量值"blablabla"起了一个系统默认的变量名default，自然default只能有一个值，所以一个文件内不能有多个export default。
对应的导入方式： //b.js import str from 'a'; //导入的时候没有花括号

本质上，a.js文件的export default输出一个叫做default的变量，然后系统允许你为它取任意名字。所以可以为import的模块起任何变量名，且不需要用大括号包含
```

原贴链接:<https://www.cnblogs.com/mengfangui/p/9073459.html>