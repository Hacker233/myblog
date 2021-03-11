---
title: CSS定位的原理及应用
author: 小猪课堂
img: /medias/images/001.png
top: true
cover: true
toc: true
mathjax: false
summary: 你确定你都了解CSS定位及其原理.
categories: CSS
tags:
  - CSS
---
# 1.position属性
* static 默认值
* relative 相对定位
* absolute 绝对定位
* fixed 固定定位
* sticky 粘性定位
# 2.static 属性值
简介：static是position属性的默认值，如果过省略position属性，那么元素默认就是static定位。

特点：设置了该属性后，top、left、bottom属性性值无效。

```plain
div {
            width: 100px;
            height: 100px;
            background-color: red;
            margin-bottom: 100px;
            position: static;
            top: 10px;
            left: 20px;
        }
```
# 3.relative
简介：相对定位，相对与自己本身。

特点：设置该属性之后同样占据文档位置。

```plain
<style>
    div {
        width: 100px;
        height: 100px;
        background-color: red;
        margin-bottom: 100px;
    }
    .div-relative {
        margin-top: 30px;
        position: relative;
        top: 20px;
        left: 20px;
    }
</style>
```
# 3.absolute
简介：相对于上级设置了relative或者absolute的父级元素，如果没有设置，则相对于整个页面进行定位。

特点：脱离文档流，不在占据文档位置。

```plain
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS定位的原理及应用？</title>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: red;
            margin-bottom: 100px;
        }
        .div-relative {
            margin-top: 30px;
            position: relative;
            top: 20px;
            left: 20px;
        }
        .div-box {
            width: 200px;
            height: 200px;
            background-color: blue;
            position: relative;
        }
        .div-absolute {
            background-color: yellow;
            position: absolute;
            top: 10px;
        }
    </style>
</head>
<body>
    <div class="div-relative"></div>
    <div class="div-box">
        <div class="div-absolute"></div>
    </div>
</body>
```
# 4.fixed
简介：相对与浏览器窗口进行偏移。

特点：会导致元素的位置不随页面滚动而变化，脱离了文档流。

```plain
.div-fixed {
    width: 20px;
    height: 20px;
    background-color: pink;
    position: fixed;
    top: 300px;
    right: 20px;
}
```
# 5.sticky
简介：粘性定位，可以说它是relative和fixed的结合体。

特点：必须结合top等属性。

```plain
.div-sticky {
    width: 100px;
    height: 100px;
    background-color: violet;
    position: sticky;
    top: 0px;
}
```
