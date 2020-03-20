---
title: http和https的区别
tags: Web前端
categories: 
- HTML
date: 2020-03-07 
---
### 基本概念
http: 超文本传输协议，是互联网上应用最为广泛的一种网络协议，是一个客户端和服务器端请求和应答的标准（TCP），用于从WWW服务器传输超文本到本地浏览器的传输协议，它可以使浏览器更加高效，使网络传输减少。<br/>
https: 是以安全为目标的HTTP通道，简单讲是HTTP的安全版，即HTTP下加入SSL层，HTTPS的安全基础是SSL，因此加密的详细内容就需要SSL。https协议的主要作用是：建立一个信息安全通道，来确保数组的传输，确保网站的真实性。 

### 区别
1. 安全性：http是超文本传输协议，信息是明文传输，https则是具有安全性的ssl加密传输协议。
2. 端口：一般而言，http协议的端口为80，https的端口为443

### https的优缺点
* 优点：
  1. 可以认证用户和服务器，确保数据发送到正确的客户机和服务器；
  2. 比http更安全，可防止数据在传输过程中不被窃取、改变，确保数据的完整性。 
* 缺点：
  1. 握手阶段费时，延长页面加载时间，增加耗电；
  2. 缓存效率比http低，增加数据开销