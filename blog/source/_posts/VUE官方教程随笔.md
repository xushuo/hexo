---
title: VUE官方教程随笔
date: 2017-03-23 11:36:54
tags:
    - vue.js
    - 教程
    - 前端
categories: 教程

---

VUE.js官方教程随笔
===========

好吧~酱酱本来在看es6的promise，偶然发现了VUE.JS,一不小心看了下大概，发现还挺有趣。所以索性就先把promise撂在一边，去官网学习下vue*.*。当然我也不确定这个会更新到什么时候，哈哈。

--------

vue的安装
----------

### 兼容性
vue.js不支持ie8及其以下版本，支持所有兼容es5的浏览器。
### npm
`$ npm install vue`
### 命令行工具
vue.js 提供一个官方的命令行工具，可以快速搭建单页面应用，我们先用他来测试下。

    # 全局安装 vue-cli
    $ npm install --g vue-cli
    # 创建一个基于webpack模板的项目
    $ vue init webpack job
    # 安装依赖
    $ cd job
    $ npm install 
    $npm run dev
![](/images/vue/1.png)
上面这个就是我初步测试的一个项目,当然这个是没有路由的，init的时候会有选项，可以产生更多的功能以及模块

vue.js的初步体验
-------------

### hello world 

    <div id="app">
      {{ message }}
    </div>
    
    var app = new Vue({
      el: '#app',
      data: {
        message: 'Hello Vue!'
      }
    })

vue提供了数据和dom的绑定，当代码更改，页面就会更新。有点类似于webpack的热加载和angularjs。
### 生命周期
机智的我从官网上偷来了这个图，看起来灰常长~长~长~~~
所以，我就不解释了，很·清晰·
![](https://cn.vuejs.org/images/lifecycle.png)

vue.js 模板语法
-------------

    之后我就使用官方的title了，毕竟只是随笔，摘抄总结些知识点

### 语法
* 文本 mustache ： `<span>Message: {{ msg }}</span> ` 
* 如果为一次性插入，则为  `<span v-once>This will never change: {{ msg }}</span>`
* 纯html： `<div v-html="rawHtml"></div>`
* 文本 `v-text=“msg”` 等价于 `{{ msg }}`
* 绑定属性： v-bind `<div v-bind:id="dynamicId"></div>`
* js表达式： `{{ number+1 }}` `<div v-bind:id=" 'list' +id "></div>`
* 绑定事件 v-on  `<a v-on:click="event"></a>`
* 过滤器
   1.过滤器函数总是接受表达式的第一个值作为第一个参数，表达式的参数则从第二个开始。
   可以添加多个表达式。
 
   2.过滤器可以用到两个地方 mustache 插值以及v-bind 表达式
   
   
    {{ item.label | filter(''123') }}
    filters:{
          filter(val,arg1){
            if(!val) return '';
            val=val.toString();
            return val.charAt(0).toUpperCase()+val.slice(1);
          }
        }
    arg1 = 123 

* 缩写 
   1. v-on  `<a @click="doSomething"></a>`
   2. v-bind   `<a :href="url"></a>`
   
### 计算属性
计算属性不需要再data里声明，依赖于data里面的数据，并且自动更新。计算属性只有在它的相关依赖发生改变时才会重新求值

    <h4>{{ computedMsg }}</h4>
    computed:{
      computedMsg(){
          return this.newItem.split('').reverse().join('');
      }
    }
### watch
监听items的值，当发生变化，则调用handler函数。

    watch : {
          items : {
            handler(oldVal, newVal){
              Store.save(newVal);
            },
            deep : true
          }
        },
 
CLass与Style的绑定
 ---------------
 
 ### 绑定html class
 1. class   v-bind   
`  <div v-bind:class="{ active: isActive }"></div>`
 class ’active‘ 的更新取决于 isActive的 true or false
  多个class用 逗号 ,  分隔
 计算属性的应用：
 

        <div v-bind:class="classObject"></div>
        data: {
          isActive: true,
          error: null
        },
        computed: {
          classObject: function () {
            return {
              active: this.isActive && !this.error,
              'text-danger': this.error && this.error.type === 'fatal',
            }
          }
        }
 多个class，数组形式表现
      
      <div v-bind:class="[activeClass, errorClass]">
      data: {
        activeClass: 'active',
        errorClass: 'text-danger'
      }
      渲染为:
      <div class="active text-danger"></div>    
 
 2. style v-bind
 
 
     <div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>
     data: {
       activeColor: 'red',
       fontSize: 30
     }
     OR 直接绑定
     <div v-bind:style="styleObject"></div>
     data: {
       styleObject: {
         color: 'red',
         fontSize: '13px'
       }
     }
     
条件渲染   
----------
### v-if
条件判断

    <h1 v-if="ok">YES</h1>
    <h1 v-else>NO</h1>
切换多个元素，可以用 template
    
    <template v-if="ok">
        <span>s1</span>
        <span>s2</span>
    </template>
if = v-if
else if = v-else-if
else = v-else
### key管理可复用元素
如果用条件语句切换同一个元素的时候，改元素将不会替换掉，只会替换掉相对应的属性。
如果需要替换，需要添加key

    <template v-if="loginType === 'username'">
      <label>Username</label>
      <input placeholder="Enter your username" key="username-input">
    </template>
    <template v-else>
      <label>Email</label>
      <input placeholder="Enter your email address" key="email-input">
    </template>
### v-show 
* v-show 不支持 template语法
* v-show css的属性 display的切换  v-if涉及到元素的创建以及销毁

列表渲染
----------
### v-for
item in items  语法渲染  也可以用  item of items

    <ul id="example-2">
      <li v-for="(item, index) in items">
        {{ parentMessage }} - {{ index }} - {{ item.message }}
      </li>
    </ul>
* v-for 支持template标签
* v-for 支持遍历对象
参数分别为 value key index 

    
    <p v-for="(val, key , index) in object">{{ index+" : "+key+" - "+val }}</p>
* v-for支持取整数
`<span v-for="n in 10">{{ n }}</span>`
