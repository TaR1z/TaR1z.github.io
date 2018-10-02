---
layout: post
title: "js数组方法整理"
date: 2018-10-02
excerpt: "转载：https://www.cnblogs.com/obel/p/7016414.html"
tags: [Js, Array]
comments: false
jsNotes: true
feature: /assets/img/jsinfo/mid-night.png
---

# JS数组方法  
### <label style="color:tomato">join()</label> 
  将数组的元素组成一个字符串，以**separator**为分隔符，省略的话则用默认用逗号为分隔符，该方法之接受一个参数：分隔符。  
{% highlight js %}
  var arr = [1,2,3];  
  console.log(arr.join());  
  console.log(arr.join("-"));  
  console.log(arr);
{% endhighlight %}  
  输出结果为:  
{% highlight js %}
  1,2,3  
  1-2-3  
  [1, 2, 3]
{% endhighlight %}  
  可知：**该方法不改变原数组**  
  
  通过**join()**方法可以实现重复字符串，只需传入字符串以及重复的次数，就能返回重复的字符串，函数如下：  
{% highlight js%}
  function repeatString(str, n){  
     return new Array(n+1).join(str);  
  }  
  console.log(repeatString("abc", 3));  
  console.log(repeatString("Hi", 2));  
{% endhighlight %}  
  输出结果为：  
{% highlight js %}    
  abcabcabc  
  HiHi  
{% endhighlight %}  

---  
### <label style="color:tomato">push() pop()</label>  
  **push**: 可以接受任意数量的参数，把他们逐个添加到数组末尾，并且返回修改后的数组的长度。  
  **pop**:  数组末尾移除最后一项，减少数组的length值，然后返回移除的项。  
{% highlight js %}  
  var arr = ["a", "b", "c"];  
  var count = arr.push("1", "2");  
  console.log(count);  
  console.log(arr);  
  var arr1 = arr.pop();  
  console.log(arr1);  
  console.log(arr);  
{% endhighlight %}  
  输出结果为：  
{% highlight js %}  
  5  
  ["a", "b", "c", "1", "2"]  
  2  
  ["a", "b", "c", "1"]
{% endhighlight %}  
  可知：**该方法改变原数组**  
  
---  
### <label style="color:tomato">shift() unshift()</label>  
  **shift()**：删除原数组的第一项，并且返回删除元素的值；如果数组为空则返回underfined。  
  **unshift()**: 将参数添加到原数组开头，并且返回原数组的长度。  
  这组方法和上面的**push()**和**pop()**方法正好相对应，一个是操作数组的开头，一个是操作数组的结尾。  
{% highlight js %}  
  var arr = ["a", "b", "c"];  
  var count = arr.unshift("1", "2");  
  console.log(count);  
  console.log(arr);  
  var item = arr.shift();  
  console.log(item);  
  console.log(arr);  
{% endhighlight %}  
  输出结果为：  
{% highlight js %}  
  5  
  ["1", "2", "a", "b", "c"]  
  1  
  ["2", "a", "b", "c"]
{% endhighlight %}  
  可知：**该方法改变原数组**  
  
---  

  
  
  
