---
title: VUE官方教程随笔(基础篇)
date: 2017-03-23 11:36:54
tags:
    - vue.js
    - 教程
    - 前端
    - 基础
categories: 教程

---

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
 #### class   v-bind   
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
 
#### style v-bind
 
 
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

### 数组变更检测
* 以下两种情况，vue不能检测变动而的数组
1.当你利用索引直接设置一个项时，例如： `vm.items[indexOfItem] = newValue`
2.当你修改数组的长度时，例如： `vm.items.length = newLength`
解决办法：


    1： Vue.set(example1.items, indexOfItem, newValue)
        example1.items.splice(indexOfItem, 1, newValue)
    2： example1.items.splice(newLength)
    
时间处理器
-----
### 监听事件 
v-on监听
也可以直接用vue的实例调用。
    
    var vm = new Vue({
        method:{
             hello(){
             }
        }
    })；
    vm.hello();
表单控件绑定
-------
### v-model
v-model 可以绑定文本值
checkbox：`<input type="checkbox" id="checkbox" v-model="checked">`
radio： `<input type="radio" id="one" value="One" v-model="picked">`
select： `<select v-model="selected">`
v-model绑定的是标签的value
还可以更改绑定耳朵value。 v-bind
`<input  type="checkbox"  v-model="toggle"  v-bind:true-value="a"  v-bind:false-value="b" >`
`<input type="radio" v-model="pick" v-bind:value="a">`
过滤收尾空格： `<input v-model.trim="msg">`

组件 component
-------
### 注册
命名尽量遵守W3C规则(小写并包含一个短杠)
    
    #注册全局组件
    Vue.component(''my-componetn',{
        template: '<div>hello</div>'
    });
    #局部注册
    new Vue({
      components:{
        'my-btn': {
            data(){
               return {
                 id: 10
               }
             }, 
            template: '<button v-on:click="id++">{{ id }}</button>'
          }
      }
    })
### 组件传递数据
####  prop
子组件用 props 声明所需的**字符串**   
   
    
    Vue.component('child', {
      // 声明 props
      props: ['message'],
      // 就像 data 一样，prop 可以用在模板内
      // 同样也可以在 vm 实例中像 “this.message” 这样使用
      template: '<span>{{ message }}</span>'
    })
    #传值 
    <child message="hello!"></child>       

> **Note:**

> - HTML 特性是不区分大小写的。所以，当使用的不是字符串模版，camelCased (驼峰式) 命名的 prop 需要转换为相对应的 kebab-case (短横线隔开式) 命名

    Vue.component('child', {
      // camelCase in JavaScript
      props: ['myMessage'],
      template: '<span>{{ myMessage }}</span>'
    })
    <!-- kebab-case in HTML -->
    <child my-message="hello!"></child>
* 如果需要动态传值，绑定父子关系 **单项绑定**，则用 v-bind:my-mysssage 。
* 子组件不应该在内部改变prop。
    
    
    ① ： 定义一个局部变量，并用 prop 的值初始化它：
    props: ['initialCounter'],
    data: function () {
      return { counter: this.initialCounter }
    }
    ② ： 定义一个计算属性，处理 prop 的值并返回。
    props: ['size'],
    computed: {
      normalizedSize: function () {
        return this.size.trim().toLowerCase()
      }
    }
> **Tip:** 注意在 JavaScript 中对象和数组是引用类型，指向同一个内存空间，如果 prop 是一个对象或数组，在子组件内部改变它会影响父组件的状态。

#### 自定义事件
   vue的事件接口
   * $on(eventName) 监听事件
   * $emit(eventName) 触发事件


    <div id="counter-event-example">
      <p>{{ total }}</p>
      <button-counter v-on:increment="incrementTotal"></button-counter>
      <button-counter v-on:increment="incrementTotal"></button-counter>
    </div>
    Vue.component('button-counter', {
      template: '<button v-on:click="increment">{{ counter }}</button>',
      data: function () {
        return {
          counter: 0
        }
      },
      methods: {
        increment: function () {
          this.counter += 1
          this.$emit('increment')
        }
      },
    })
    new Vue({
      el: '#counter-event-example',
      data: {
        total: 0
      },
      methods: {
        incrementTotal: function () {
          this.total += 1
        }
      }
    })
#### 非父子组件间通信
* 如果简单情况下，可以使用一个空的Vue实例作为中央事件总线
    
    
    var bus = new Vue()
    // 触发组件 A 中的事件
    bus.$emit('id-selected', 1)
    // 在组件 B 创建的钩子中监听事件
    bus.$on('id-selected', function (id) {
      // ...
    })
#### 使用slot分发内容
##### 单个slot
除非子组件模板包含至少一个 <slot> 插口，否则父组件的内容将会被丢弃。当子组件模板只有一个没有属性的 slot 时，父组件整个内容片段将插入到 slot 所在的 DOM 位置，并替换掉 slot 标签本身。
    
    假定 my-component 组件有下面模板：
    <div>
      <h2>我是子组件的标题</h2>
      <slot>
        只有在没有要分发的内容时才会显示。
      </slot>
    </div>
    父组件模版：
    <div>
      <h1>我是父组件的标题</h1>
      <my-component>
        <p>这是一些初始内容</p>
        <p>这是更多的初始内容</p>
      </my-component>
    </div>
    渲染结果：
    <div>
      <h1>我是父组件的标题</h1>
      <div>
        <h2>我是子组件的标题</h2>
        <p>这是一些初始内容</p>
        <p>这是更多的初始内容</p>
      </div>
    </div>
##### 具名slot    
<slot> 元素可以用一个特殊的属性 name 来配置如何分发内容。多个 slot 可以有不同的名字。具名 slot 将匹配内容片段中有对应 slot 特性的元素。
仍然可以有一个匿名 slot ，它是默认 slot ，作为找不到匹配的内容片段的备用插槽。如果没有默认的 slot ，这些找不到匹配的内容片段将被抛弃。
    
    例如，假定我们有一个 app-layout 组件，它的模板为：
    <div class="container">
      <header>
        <slot name="header"></slot>
      </header>
      <main>
        <slot></slot>
      </main>
      <footer>
        <slot name="footer"></slot>
      </footer>
    </div>
    父组件模版：
    <app-layout>
      <h1 slot="header">这里可能是一个页面标题</h1>
      <p>主要内容的一个段落。</p>
      <p>另一个主要段落。</p>
      <p slot="footer">这里有一些联系信息</p>
    </app-layout>
    渲染结果为：
    <div class="container">
      <header>
        <h1>这里可能是一个页面标题</h1>
      </header>
      <main>
        <p>主要内容的一个段落。</p>
        <p>另一个主要段落。</p>
      </main>
      <footer>
        <p>这里有一些联系信息</p>
      </footer>
    </div>
#### 动态组件
is 特性。多个组件使用同一个挂载点，并且动态切换

    var vm = new Vue({
      el: '#example',
      data: {
        currentView: 'home'
      },
      components: {
        home: { /* ... */ },
        posts: { /* ... */ },
        archive: { /* ... */ }
      }
    })
    <component v-bind:is="currentView">
      <!-- 组件在 vm.currentview 变化时改变！ -->
    </component>    
##### keep-alive
动态切换组件的状态缓存保留
    
    <keep-alive>
      <component :is="currentView">
        <!-- 非活动组件将被缓存！ -->
      </component>
    </keep-alive>
####编写可复用组件
 在编写组件时，记住是否要复用组件有好处。一次性组件跟其它组件紧密耦合没关系，但是可复用组件应当定义一个清晰的公开接口。
 
 Vue 组件的 API 来自三部分 - props, events 和 slots ：   
 * Props 允许外部环境传递数据给组件
 * Events 允许组件触发外部环境的副作用
 * Slots 允许外部环境将额外的内容组合在组件中。   
使用 v-bind 和 v-on 的简写语法，模板的缩进清楚且简洁：  
    
    
    <my-component
      :foo="baz"
      :bar="qux"
      @event-a="doThis"
      @event-b="doThat"
    >
      <img slot="icon" src="...">
      <p slot="main-text">Hello!</p>
    </my-component>


-----

好了，经过艰苦卓绝的探索实践过程，Vue官方教程的基础篇完成了。其实组件还有一些杂项，不过大多属于心得方面的吧，以后开发可以参考。
经过这次Vue的探索之旅，真实良心官方教程啊。外国的坑爹教程，目不忍视。
不管怎么样，基础里面还有一些涉及到进阶篇的内容。之后会补充上。
好了，起飞！

---------------
    
    
    
    