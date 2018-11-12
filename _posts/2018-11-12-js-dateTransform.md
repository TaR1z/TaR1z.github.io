---
layout: post
title: "数据类型转换（Number、String、Boolean）"
date: 2018-10-05
excerpt: "一些小归纳和注意点"
tags: [Js]
comments: false
jsNotes: true
feature: /assets/img/jsinfo/balloon.jpg
---

## 数据类型转换
---
### Number 
{% highlight js %}
// 1.parseInt
console.log(parseInt("12")); // 12
console.log(parseInt("12dsadas")); // 12
console.log(parseInt("dsads12"));  // NaN
console.log(parseInt("1dsa2"));    // 1
// 2.parseFloat
console.log(parseFloat("12")); // 12
console.log(parseFloat("12dsadas")); // 12
console.log(parseFloat("dsads1.2"));  // NaN
console.log(parseFloat("1.2dsa2"));    // 1.2
// 3.Number
console.log(Number("12")); // 12
console.log(Number("12dsadas")); // NaN
console.log(Number("dsads1.2"));  // NaN
console.log(Number("1.2dsa2"));    // NaN
/*
* 总结：
*		整形：ParseInt
*		数字：Number(严格)
*		浮点：parseFloat
*/
{% endhighlight %}

### String 
{% highlight js %}
// 1.toString
var num = 10;
var num1 = 10;
var num2;
var num3;
var num4 = null;
var num5 = null;
console.log(num.toString()); // 10(黑色字体)
console.log(num2.toString()); // 报错
console.log(num4.toString()); // 报错
// 2.String
console.log(String(num)); // 10(黑色字体)
console.log(String(num3)); // undefined(黑色字体)
console.log(String(num5)); // null(黑色字体)
/*
* 总结：
*		变量有意义调用toString
*		变量没意义调用String
*/
{% endhighlight %}

### Boolean
{% highlight js %}
// 1.Boolean
console.log(Boolean("")); // false
console.log(Boolean(null)); // false
console.log(Boolean(undefined)); // false
console.log(Boolean(1)); // true
console.log(Boolean(0)); // false
console.log(Boolean(NaN)); // false
/*
* 总结：
*		Boolean(): null、NaN、undefined、""、0 => false
*		
*/
{% endhighlight %}
