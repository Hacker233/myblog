---
title: Vue2.x生命周期详解
author: 小猪课堂
img: /medias/images/001.png
top: true
cover: true
toc: true
mathjax: false
summary: 一个Vue应用和一个人一样，人有生老病死，Vue应用也是这样.
categories: Vue
tags:
  - Vue2.x
---
# Vue2.x生命周期详解

## 1.何为生命周期

​	一个Vue应用和一个人一样，人有生老病死，Vue应用也是这样，也有生老病死，只不过在Vue里面换了一种说法，叫做生命周期。

​	一个Vue应用主要分为四个阶段：创建、渲染、更新、销毁。这就好比人生的各个阶段，在每一个阶段都会做一些事。在Vue里面，每一个阶段都会自动执行一些函数，无需我们操作，这些函数官方给它们定义叫生命周期函数或者钩子函数。

## 2.生命周期函数的用法

![](https://cn.vuejs.org/images/lifecycle.png)

​	上面的图就完整诠释了一个Vue应用的整个生命周期，从创建到销毁。其中有8个函数分别是：beforeCreate、created、beforeMount、mounted、beforeUpdate、updated、beforeDestroy、destroyed。

​	这8个函数其实就分别对应了一个Vue应用的四个阶段：创建、渲染、更新、销毁。这8个函数会在各个阶段分别自动执行，所以也叫做自动执行函数，我们写在methods里面的方法基本上是被动执行函数。

​	下面我们就来看一看这8个函数具体什么情况下执行：

#### 2.1 beforeCreate

​	该生命周期函数在实例生成之前自动执行，也就是在数据观测和事件配置之前执行，此时选项对象还未创建，el（节点）和data还没有初始化，因此无法访问methods、data、computed上面的方法和数据。

#### 2.2 created

​	该生命周期函数在实例生成之后自动执行，此时我们的实例已经完成了如下配置：数据观测、属性和方法的运算，watch/event事件回调，完成了data 数据的初始化，el还未初始化。这个生命周期函数是我们常用的，因为我们可以调用methods中的方法，并且改变data中的数据，有很多小伙伴都会选择在这个周期函数里面发送ajax请求，但是有一点需要注意：如果有些数据必须要获取才能进入页面的话，不建议在此函数中发送请求，因为在这个函数中我们无法对实例化的过程进行拦截。

#### 2.3 beforeMount

​	该生命周期函数在模板渲染之前自动执行，此时的data和el都已经初始化完成，但是还并没有渲染到页面上。

#### 2.4 mounted

​	该生命周期函数在模板渲染之后自动执行，此时我们模板中的HTML已经渲染到了HTML页面上，我们也可以在此函数中发送ajax请求。

#### 2.5 beforeUpdate

​	当data中的数据发生变化时会自动执行该生命周期函数。

#### 2.6 beforeUpdate

​	当data中的数据发生变化且页面重新渲染后会自动执行该生命周期函数。

#### 2.7 beforeDestroy

​	当Vue应用失效时，该生命周期函数会自动执行。

#### 2.8 destroyed

​	当Vue应用失效时，并且DOM也完全销毁后，该生命周期函数会自动执行。

## 3.生命周期函数代码示例

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>生命周期</title>
  <script type="text/javascript" src="vue.js"></script>
</head>
<body>
    <div id="app">
      {{msg}}
    </div>
</body>
<script type="text/javascript">
  new Vue({
    el: '#app',
    data: {
      msg: "hello world"
    },
    beforeCreate() {
      console.log('beforeCreate()')
    },
    created() {
      console.log('created()')
    },
    beforeMount() {
      console.log('beforeMount()')
    },
    mounted () {
      console.log('mounted()')
    },
    beforeUpdate() {
      console.log('beforeUpdate()')
    },
    updated () {
      console.log('updated()')
    },
    beforeDestroy() {
      console.log('beforeDestroy()')
    },
    destroyed() {
      console.log('destroyed()')
    }
  })
</script>
</html>
```

