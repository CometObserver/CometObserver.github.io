---
title: JavaScript中常见错误类型和异常处理机制
tags: Web前端
categories: 
- JavaScript
date: 2019-02-05
---

## 常见错误类型
* ***SyntaxError:***解析代码时发生的语法错误。
* ***ReferenceError:***引用一个不存在的变量时发生的错误；另一种触发场景是，将一个值分配给无法分配的对象，比如对函数的运行结果赋值。
* ***RangeError:***值超出有效范围时发生的错误。主要有几种情况，一是数组长度为负数，二是Number对象的方法参数超出范围，以及函数堆栈超过最大值。
* ***TypeError:***变量或参数不是预期类型时发生的错误。比如，对字符串、布尔值、数值等原始类型的值使用new命令，就会抛出这种错误，因为new命令的参数应该是一个构造函数。

## 异常处理

### throw
throw语句的作用是手动中断程序执行，抛出一个错误。另外，throw可以抛出任何类型的值。也就是说，它的参数可以是任何值。对于 JavaScript 引擎来说，遇到throw语句，程序就中止了。引擎会接收到throw抛出的信息，可能是一个错误实例，也可能是其他类型的值。***一般来说，throw语句用来处理逻辑错误***，对于逻辑错误，js是不会抛出异常的，也就是说，用try catch没有用。这种时候，需要自己创建error对象的实例，然后用throw抛出异常。例：
```
try{
    let 1/0;
    if(num=Infinity){
        throw new Error("除数不能为0");//Error大写，用new初始化,这个Error是异常里面的message属性！
    }
}
catch(exception){
    console.log(exception.message);
}
```

### try...catch...
一旦发生错误，程序就中止执行了。JavaScript 提供了try...catch结构，允许对错误进行处理，选择是否往下执行。
在不确定某些代码是否会报错的时候，就可以把它们放在try...catch代码块之中，便于进一步对错误进行处理。需此外，catch代码块之中，还可以再抛出错误，甚至使用嵌套的try...catch结构。***try……catch一般用于语法错误，错误有name和message两个属性。***例：
```
try {
  throw "出错了";
} catch (e) {
  console.log(111);
}
console.log(222);
// 111
// 222
```

### finally
try...catch结构允许在最后添加一个finally代码块，表示不管是否出现错误，都必需在最后运行的语句。需要注意的是return语句的执行是排在finally代码之前，只是等finally代码执行完毕后才返回。此外还需注意，catch代码块之中，触发转入finally代码块的标志，不仅有return语句，还有throw语句。下面的例子充分反映了try...catch...finally这三者之间的执行顺序:
```
function f() {
  try {
    console.log(0);
    throw 'bug';
  } catch(e) {
    console.log(1);
    return true; // 这句原本会延迟到 finally 代码块结束再执行
    console.log(2); // 不会运行
  } finally {
    console.log(3);
    return false; // 这句会覆盖掉前面那句 return
    console.log(4); // 不会运行
  }

  console.log(5); // 不会运行
}

var result = f();
// 0
// 1
// 3

result
// false
```

下面是finally代码块用法的典型场景：
```
openFile();

try {
  writeFile(Data);
} catch(e) {
  handleError(e);
} finally {
  closeFile();
}
```
上面代码首先打开一个文件，然后在try代码块中写入文件，如果没有发生错误，则运行finally代码块关闭文件；一旦发生错误，则先使用catch代码块处理错误，再使用finally代码块关闭文件。

