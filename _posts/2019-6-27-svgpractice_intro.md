---
layout: post
title: 图片高糊？在SVG的世界不存在的！
author: Autumnhui
date: 2019-6-27
categories:
     - svg
---

# 为什么是SVG？

> 大家都知道，在计算机图形学中，有**两种主要的图像类型**：矢量和位图。
 1. 位图，也叫做点阵图，栅格图象，像素图，简单地说，就是最小单位由像素构成的图，缩放会失真。
 2. 矢量图，简单地说，就是缩放不失真的图像格式。


 随着响应式网页的发展，对于内容呈现的要求也越来越高，尤其是图像。为了在各种设备上能实现自然伸缩或扩展而不影响图片质量，所以矢量图形（SVG）正变得越来越受欢迎。

- 所以，SVG是个什么玩意？
> SVG 指可伸缩矢量图形，英文全称为Scalable Vector Graphics.简单来说就是用数学定义点位后出来的图形。它可以用文本来描述，并且在放大的情况下也可以保持图片质量。

- SVG有什么特点？
1. **小！** 它是直接用数学定义表达，相对比JPEG、GIF等位图的大小的差距，就像hanteng与我的差距。
2. **无损！** 因为它是用数学定义的，即使放大也不会出现马赛克！（图片质量一如既往的高）
3. **可编辑性强！** 我们可以通过修改定义svg的文本，进而去修改这个图形。
4. **还会动！** 结合强大的css3，我们甚至可以让SVG自己动！

---

# SVG结合CSS实例

<center>

<div>
<svg class=chrome-icon1 focusable="false" width="200" height="200" data-prefix="fab" data-icon="chrome" fill="#4586F3" class="svg-inline--fa fa-chrome fa-w-16" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 496 512"><path fill="#4586F3" d="M131.5 217.5L55.1 100.1c47.6-59.2 119-91.8 192-92.1 42.3-.3 85.5 10.5 124.8 33.2 43.4 25.2 76.4 61.4 97.4 103L264 133.4c-58.1-3.4-113.4 29.3-132.5 84.1zm32.9 38.5c0 46.2 37.4 83.6 83.6 83.6s83.6-37.4 83.6-83.6-37.4-83.6-83.6-83.6-83.6 37.3-83.6 83.6zm314.9-89.2L339.6 174c37.9 44.3 38.5 108.2 6.6 157.2L234.1 503.6c46.5 2.5 94.4-7.7 137.8-32.9 107.4-62 150.9-192 107.4-303.9zM133.7 303.6L40.4 120.1C14.9 159.1 0 205.9 0 256c0 124 90.8 226.7 209.5 244.9l63.7-124.8c-57.6 10.8-113.2-20.8-139.5-72.5z"></path></svg>
</div>

<style>
.chrome-icon1 {
 animation: hahaha 2s infinite;
 animation-timing-function:linear;
}

@keyframes hahaha{
0% { transform:rotate(0deg);}

100% { transform : rotate(360deg)}
}  
</style>
</center>


## 上面的例子如何实现？
就如上面的例子，我们只要用一个对图形的定义，再给它个css属性，ok~

**代码如下：**
```
//以下是对svg图形的数学定义。
<svg class=chrome-icon1 focusable="false" width="200" height="200" data-prefix="fab" data-icon="chrome" fill="#4586F3" class="svg-inline--fa fa-chrome fa-w-16" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 496 512"><path fill="#4586F3" d="M131.5 217.5L55.1 100.1c47.6-59.2 119-91.8 192-92.1 42.3-.3 85.5 10.5 124.8 33.2 43.4 25.2 76.4 61.4 97.4 103L264 133.4c-58.1-3.4-113.4 29.3-132.5 84.1zm32.9 38.5c0 46.2 37.4 83.6 83.6 83.6s83.6-37.4 83.6-83.6-37.4-83.6-83.6-83.6-83.6 37.3-83.6 83.6zm314.9-89.2L339.6 174c37.9 44.3 38.5 108.2 6.6 157.2L234.1 503.6c46.5 2.5 94.4-7.7 137.8-32.9 107.4-62 150.9-192 107.4-303.9zM133.7 303.6L40.4 120.1C14.9 159.1 0 205.9 0 256c0 124 90.8 226.7 209.5 244.9l63.7-124.8c-57.6 10.8-113.2-20.8-139.5-72.5z"></path></svg>
//以上是对svg图形的数学定义，以下是给svg图形的动画属性。
<style>
.chrome-icon1 {
 animation: hahaha 2s infinite;
 animation-timing-function:linear;
}

@keyframes hahaha{
0% { transform:rotate(0deg);}

100% { transform : rotate(360deg)}
}  
</style>
//以上是给svg图形的动画属性。
```

---

这就没了？是啊！

 **结合css的svg的玩法很多，好好玩。**