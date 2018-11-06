---
layout: post
title: "broSelect"
date: 2018-11-06
excerpt: "兄弟选择器"
tags: [css]
comments: false
cssNotes: true
feature: /assets/img/cssinfo/snowgirl.jpg
---
### 兄弟选择器
**注意点：兄弟标签只能选中紧跟后面的那个标签，不能隔代选择** <br />
{% highlight html %}
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>

		* {
			padding: 0;
			margin: 0;
		}

		div {
			text-align: center;
			line-height: 100px;
			width: 100px;
			height: 100px;
			background-color: indianred;
		}

		.text {
			display: inline-block;
			width: 100px;
			height: 100px;
		}

		.text:hover + .text1 {
			color: skyblue;
			font-size: 20px;
			font-weight: 700;
		}
	</style>
</head>
<body>
	<p class="text">dsadasd</p>
	<p class="text1">12321312</p>
	<div class="box">123</div>
</body>
</html>
{% endhighlight %}
运行结果：<br />
**鼠标移动到text区域，text1样式改变。**<br />
**如果将text1和box调换位置，text1样式不改变。**<br />



