---
layout: post
title: "面试题（杂）"
date: 2018-10-12
excerpt: "查阅了一些资料"
tags: [数据结构, sql, js, java]
comments: false
other: true
feature: /assets/img/otherinfo/saber.jpg
---

### 零碎知识

* 多播IP
> 属于D类地址  

* 磁盘读写单位
> 扇区

* 系统抖动
> 刚被调出的帧又立即被调入所形成的频发调入调出的现象

* mysql innodb 引擎隔离
> 默认的事务隔离级别为repeatable-read（可重复读）

* 重绘（repaints）和回流（reflows）是什么？如何避免？
>  回流：当render tree中的一部分（或全部）因为元素的规模尺寸、布局、隐藏等改变而需要重新构建。
> 重绘：当render tree中的一些元素需要更新属性，而这些属性只是影响元素的外观、风格、而不会影响布局的，比如background-color
> 注意： 回流必将引起重绘，而重绘而不一定引起回流
> > 避免:
1.直接改变className，如果动态改变样式，则使用css Text（考虑没有优惠的浏览器)
2.让要操作的元素进行“离线处理“，处理完后一起更新
3.不要经常访问会引起浏览器flush队列的属性，如果你确实要访问，利用缓存
4.让元素脱离动画流，减少回流的reader tree的规模

---
### js小知识
{% highlight js %}
var a = [];
var b = {};
var c = "";
if(a){
  console.log("a1");
}
if(a == false){
  console.log("a2");
}
if(b){
  console.log("b1");
}
if(b == false){
  console.log("b2");
}
if(c){
  console.log("c1");
}
if(c == false){
  console.log("c2");
}
{% endhighlight %}
输出结果为:
{% highlight js%}
a1
a2
b1
c2
{% endhighlight %}
