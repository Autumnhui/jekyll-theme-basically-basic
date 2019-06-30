---
layout: post
title: 旋转跳跃，我可以！——使用animation的SVG
author: Autumnhui
date: 2019-6-28
categories:
     - svg
---

# 让SVG自己动起来！

在[上一篇文章《图片高糊？在SVG的世界不存在的！ 》](https://autumnhui.github.io/svg/2019/06/27/svgpractice_intro.html)中，我们成功让一辆自行车违背能量守恒定律自己跑起来，这都要归功于 **CSS3的animation和@keyframes属性！** 

> Animation属性从字面上就可以知道是指“动画”；其实它是一个简写属性，包括以下这些属性：
- animation-name——选择需要进行动画效果的对象。
- animation-duration——整个动画持续的时长。
- animation-timing-function——动画的速度曲线。
- animation-delay——动画在加载出来的几秒后开始（延迟）。
- animation-iteration-count——动画的播放次数。
 -animation-direction——可选择是否轮流反向播放动画。

<br>

> @Keyframes属性是指关键帧，通过这个属性，我们就可以为所欲为啦~我们就可以让指定的对象<s>唱跳rap</s>动起来啦！通常我们用整个动画的百分比来确定动画的过程。

---

# 实例操作

说了这么多理论，是时候来点操作了！

我们的大体步骤是——
1. 先找一个SVG，并给它定义名字
2. 在```<style>```中给对应的对象添加属性。
3. 使用```animation```给动画个名字还有时长什么的。
3. 记得使用```@Keyframes```属性时要链接到动画（对应的名字）！后面再加关键帧及动画。

<hr color:white>

![kunkun](/assets/images/kunkunplaybasketball.gif)

我们找不来坤坤，只好找来了坤坤的篮球！我们来让它自己动起来！（此svg使用了两种以上的动画效果——X轴位移、Y轴位移、缩放、旋转）

<svg class="ball" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
	 width="200px" height="200px" viewBox="0 0 24 24" enable-background="new 0 0 24 24" xml:space="preserve">
<path path fill="brown" d="M12,0C5.4,0,0,5.4,0,12c0,6.6,5.4,12,12,12c6.6,0,12-5.4,12-12C24,5.4,18.6,0,12,0z M21.835,10.245
	c-0.081,0.076-1.997,1.814-6.64,2.405c0.059-3.724,2.574-6.369,3.996-7.572C20.537,6.477,21.479,8.261,21.835,10.245z
	 M12.797,21.881c-0.023-0.027-2.089-2.57-2.552-7.789c0.559,0.034,1.136,0.059,1.755,0.059c0.707,0,1.361-0.03,1.99-0.074
	c0.438,3.047,2.738,4.807,4.314,5.668c-1.52,1.24-3.406,2.041-5.467,2.214C12.823,21.934,12.816,21.904,12.797,21.881z M10.15,12
	c0-6.605,2.593-9.815,2.646-9.88c0.021-0.023,0.026-0.052,0.042-0.077c2.021,0.17,3.874,0.946,5.378,2.147
	c-1.646,1.407-4.329,4.353-4.317,8.587C13.3,12.82,12.676,12.85,12,12.85c-0.651,0-1.252-0.027-1.831-0.066
	C10.161,12.523,10.15,12.27,10.15,12z M11.275,2.037C10.423,3.41,8.85,6.667,8.85,12c0,0.227,0.011,0.439,0.016,0.658
	c-1.043-0.131-1.95-0.316-2.73-0.531c-0.107-3.733-0.878-6.163-1.25-7.132C6.542,3.312,8.786,2.218,11.275,2.037z M3.909,6.159
	C4.248,7.24,4.698,9.12,4.817,11.701c-1.79-0.677-2.598-1.405-2.652-1.456C2.435,8.74,3.043,7.353,3.909,6.159z M2,12
	c0-0.082,0.01-0.162,0.012-0.244c0.578,0.385,1.503,0.891,2.834,1.344c-0.021,3.274-1.035,4.569-1.04,4.576
	c-0.004,0.006-0.005,0.012-0.009,0.018C2.668,16.074,2,14.111,2,12z M4.587,18.678c0.076-0.037,0.147-0.087,0.206-0.154
	c0.053-0.062,1.231-1.517,1.337-5.041c0.814,0.207,1.753,0.377,2.803,0.496c0.324,4.166,1.602,6.791,2.342,7.984
	C8.63,21.771,6.268,20.54,4.587,18.678z M19.307,18.795c-1.302-0.645-3.599-2.15-4.021-4.844c3.556-0.438,5.675-1.511,6.7-2.194
	C21.988,11.838,22,11.918,22,12C22,14.621,20.971,17.007,19.307,18.795z"/>

<style>
.ball {
 animation: ball 5s infinite;
 animation-timing-function:linear;
}

@keyframes ball {
   0% {transform: rotate(-180deg);}
  5%{transform:scale(1,1.2)}
  10%{transform:translateY(200PX);}
  20%{transform:translateX(300PX);}
  30%{transform:translateY(200PX);}
  35%{transform: rotate(177deg);}
  40%{transform:translateY(0PX);}
  45%{transform:scale(1,1.2)}
  50%{transform:translateY(200PX);}
  60%{transform:translateX(300PX);}
  65%{transform: rotate(177deg);}
  70%{transform:translateY(200PX);}
  90%{transform: rotate(-177deg);}
  100%{transform:translateY(0PX);}
}  
</style>
</svg>

<br>
<br>
<br>
<br>
<br>
<br>
<br>


！！球动了！！怎么做到的呢？我们先上代码~
```
<svg class="ball" aria-hidden="true" width=200px height=200px  focusable="false" data-prefix="fas" data-icon="basketball-ball" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 496 512"><path fill="brown" d="M212.3 10.3c-43.8 6.3-86.2 24.1-122.2 53.8l77.4 77.4c27.8-35.8 43.3-81.2 44.8-131.2zM248 222L405.9 64.1c-42.4-35-93.6-53.5-145.5-56.1-1.2 63.9-21.5 122.3-58.7 167.7L248 222zM56.1 98.1c-29.7 36-47.5 78.4-53.8 122.2 50-1.5 95.5-17 131.2-44.8L56.1 98.1zm272.2 204.2c45.3-37.1 103.7-57.4 167.7-58.7-2.6-51.9-21.1-103.1-56.1-145.5L282 256l46.3 46.3zM248 290L90.1 447.9c42.4 34.9 93.6 53.5 145.5 56.1 1.3-64 21.6-122.4 58.7-167.7L248 290zm191.9 123.9c29.7-36 47.5-78.4 53.8-122.2-50.1 1.6-95.5 17.1-131.2 44.8l77.4 77.4zM167.7 209.7C122.3 246.9 63.9 267.3 0 268.4c2.6 51.9 21.1 103.1 56.1 145.5L214 256l-46.3-46.3zm116 292c43.8-6.3 86.2-24.1 122.2-53.8l-77.4-77.4c-27.7 35.7-43.2 81.2-44.8 131.2z"></path>
<style>
.ball {
 animation: ball 5s infinite;
 animation-timing-function:linear;
}

@keyframes ball {
  0% {transform: rotate(-180deg);}
  5%{transform:scale(1,1.2)}
  10%{transform:translateY(200PX);}
  20%{transform:translateX(300PX);}
  30%{transform:translateY(200PX);}
  35%{transform: rotate(177deg);}
  40%{transform:translateY(0PX);}
  45%{transform:scale(1,1.2)}
  50%{transform:translateY(200PX);}
  60%{transform:translateX(300PX);}
  65%{transform: rotate(177deg);}
  70%{transform:translateY(200PX);}
  90%{transform: rotate(-177deg);}
  100%{transform:translateY(0PX);}
}  
</style>
</svg>
```

首先，我们前面说的，先给svg个名字~我们把它叫做“ball” --> ``` class="ball"```，接着给它定义了大小为 ```width=200px height=200px ``` ，这样球球就不会看起来怪怪的；对了，篮球嘛，给它来个棕色~ ```path fill="brown" ```。到这里我们对SVG的修改就差不多了，重点是下面的CSS！

#### 给SVG的动画

**我们对代码进行逐句分析——**

``` animation: ball 5s infinite;``` ：前面提到，animation是动画，这里是对SVG进行动画的描述，“ball”是给它安的 **名字** ，我们后面的@keyframes要跟它连接上；“5s”是动画的持续时长，这里我们让kunkun的篮球自己动了5s。

```animation-timing-function``` 是整段运动的速度，我们用了“linear”表示全程的速度是相同的。

```@keyframes ball``` ：这里开始，我们动用了关键帧了！后面的“ball”就是我们前文提到的对应的名字。我们可以随便取，只要两个地方对应上就好了。

```0% {transform: rotate(-180deg);}

  5%{transform:scale(1,1.2)}
  
  10%{transform:translateY(200PX);}
  
  20%{transform:translateX(300PX);}
  
  30%{transform:translateY(200PX);}
  
  ......
  ......
  
  100%{transform:translateY(0PX);}```
  
  这里上面的一大段都是我们对kunkun篮球运动过程的描述。我们可以自己去尝试变化过程，就无需多言了。


还是那句话——

 **结合css的svg的玩法很多，好好玩。**
