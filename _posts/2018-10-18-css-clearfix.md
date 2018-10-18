---
layout: post
title: "clear float"
date: 2018-10-18
excerpt: "清除浮动"
tags: [css, float]
comments: false
cssNotes: true
feature: /assets/img/cssinfo/midnight.jpg
---

## 清除浮动(五种)
**1.父元素设置height**
> 不推荐使用，父元素高度固定  

**2.父元素设置overflow属性**
> `overflow:hidden` 超出父元素将会隐藏<br/>
  `overflow:auto` 超出父元素会出现滚动条<br/>
  不推荐使用  
  
**3.结尾处加块级元素，并且设置clear：both属性**
{% highlight html %}
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		div {			
			background-color: skyblue;
		}

		.fly {
			float: left;
			width: 100px;
			height: 100px;
			background-color: tomato;
		}

		.clearfix {
			clear: both;
		}

	</style>
</head>
<body>
	<div>
		<div class="fly"></div>
		<div class="clearfix"></div>
	</div>
</body>
</html>
{% endhighlight %}
> 不推荐使用  

**4.after和zoom清除浮动**
{% highlight html %}
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		div {			
			background-color: skyblue;
		}

		.fly {
			float: left;
			width: 100px;
			height: 100px;
			background-color: tomato;
		}

		.clearfix {
			*zoom: 1;
		}
			
		.clearfix:after {
			content: "";
			display: block;
			height: 0;
			visibility: hidden;
			clear: both;
		}

	</style>
</head>
<body>
	<div class="clearfix">
		<div class="fly"></div>
	</div>
</body>
</html>
{% endhighlight %}
> 推荐使用 *zoom用来触发IE8以下浮动问题  

**5.after、before、zoom清除浮动**
{% highlight html %}
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		div {			
			background-color: skyblue;
		}

		.fly {
			float: left;
			width: 100px;
			height: 100px;
			background-color: tomato;
		}

		.clearfix {
			*zoom: 1;
		}

		.clearfix:before,.clearfix:after{
			content: "";
			display: table;
		}
			
		.clearfix:after {
			clear: both;
		}

	</style>
</head>
<body>
	<div class="clearfix">
		<div class="fly"></div>
	</div>
</body>
</html>
{% endhighlight %}
> 推荐使用
