---
title: 利用axios和cors解决跨域问题
tags: Web前端
categories: 
- axios
- cors
- npm
date: 2020-03-19
---

## 什么是跨域
当一个请求url的协议、域名、端口三者之间任意一个与当前页面url不同即为跨域。

| 当前页面url | 被请求页面url | 是否跨域 |原因|
|---|---|---|---|
|http://www.test.com/ | http://www.test.com/index.html | 否 | 同源（协议、域名、端口号相同）|
|http://www.test.com/ | https://www.test.com/ | 跨域 | 协议不同（http/https）|
|http://www.test.com/ | http://www.baidu.com/ | 跨域 | 主域名不同（test/baidu）|
|http://www.test.com/ | http://blog.test.com/ | 跨域 |	子域名不同（www/blog）|
|http://www.test.com:8080/ | http://www.test.com:3000/ | 跨域 | 端口号不同（8080/3000）|

## 为什么会出现跨域问题
出于浏览器的同源策略限制。同源策略是一种约定，它是浏览器最核心也最基本的安全功能，如果缺少了同源策略，则浏览器的正常功能可能都会受到影响。可以说Web是构建在同源策略基础之上的，浏览器只是针对同源策略的一种实现。同源策略会阻止一个域的javascript脚本和另外一个域的内容进行交互。所谓同源（即指在同一个域）就是两个页面具有相同的协议（protocol），主机（host）和端口号（port）。<br/>
***非同源限制***
1. 无法读取非同源网页的 Cookie、LocalStorage 和 IndexedDB
2. 无法接触非同源网页的 DOM
3. 无法向非同源地址发送 AJAX 请求

## 什么是axios
axios 是一个基于 promise 的 HTTP 库，可以用在浏览器和 node.js 中，它依赖原生的 ES6 Promise 实现而被支持.Vue2.0之后，尤雨溪推荐大家用axios替换JQuery ajax<br/>
axios具有以下特征：
* 从浏览器中创建 XMLHttpRequest[XHR-最早出现的发送后端请求技术]
* 支持 Promise API
* 提供了一些并发请求的接口[是axios的一项重要特征，方便了许多的操作]
* 从 node.js 创建 http 请求
* 拦截请求和响应、转换请求和响应数据、取消请求
* 自动转换JSON数据
* 客户端支持防止CSRF[CSRF-跨站请求伪造]
创建实例：
```
var instance = axios.create({
  baseURL: 'https://some-domain.com/api/',
  timeout: 1000,
  headers: {'X-Custom-Header': 'foobar'}
});
```
其中 baseURL 是为 axios 实例的方法传递相对 URL ，默认在 url 前面（url可省略）；<br/>
timeout 指定请求超时的毫秒数(0 表示无超时时间) ,如果请求花费了超过 timeout 的时间，请求将被中断；<br/>
headers 是即将被发送的自定义请求头；<br/>
这三个请求配置中，只有 baseURL 是必须的。

## 什么是cors
这里的CORS并非指的跨域资源共享（Cross-origin resource sharing）,而是npm中的一个包，是Connect/Express框架的一个中间件，能够用多种方式被用来实现跨域资源共享。使用方法：<br/>
首先安装cors包，
```
$ npm install cors
```
然后在后端中引入并使用。
```
const express = require('express');
const cors = require('cors');
const app = express();

app.use(cors());

```
*** 至此，就可以解决普通跨域请求了。如果是带cookie的跨域请求，还需要在前端设置 *** <br/> 
axios.defaults.withCredentials = true
