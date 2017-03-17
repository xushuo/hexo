---
title: 来谈谈Promise
date: 2017-03-17 09:39:43
tags:
    - promise
    - nodejs
    - es6
categories: es6
description: 简单了解下Promise

---

Promise——异步编程解决方案
===================


酱酱这段时间又学习了下nodejs，发现了promise这个神奇的东东。看了网上的几篇博文，各种思想在脑中疯狂的对战，乱的很。/(ㄒoㄒ)/~~实在没办法，希望一边写一边理解吧-。-

----------


Promise的登场
-------------

####promise是什么呢？

因为ES6发布了，promise被列为正式规范，主流浏览器对ES6也是极大的支持，所以我们先在chrome浏览器中看下这个宝贝啥东东。
![](/images/promise.png)
promise对象是一个构造函数，拥有all、race、reject以及resolve方法。new的新对象有catch和then方法。
####promise的状态

promise三种状态：未完成(pending),已完成(fulfilled),失败(rejected).状态之前之间不可逆转。
####promise的用法

    var promise = new Promise(function(resolve, reject) {  
	    if (/* 异步操作成功 */){    
	      resolve(value);  
	    } else {  
	      reject(error);   
    } });
    
promise添加了一个函数作为参数——resolve,reject。
resolve函数可以将promise状态由pending->fulfilled，异步操作成功时调用。
reject函数可以将promise状态由pending->rejected，异步操作失败时调用。
    
     promise.then(resolve,reject){
     } 

promise的then方法接收resolve和reject回调函数，分别为成功和失败。reject函数是可选的。
promise可以调用多个then方法，顺序执行。
