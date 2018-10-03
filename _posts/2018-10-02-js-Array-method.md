---
layout: post
title: "JS数组方法整理"
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
  var arr = [1, 2, 3];  
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
### <label style="color:tomato">sort()</label>  
  **sort()**： 按升序排列数组项————即最小值位于最前面，最大值排列在最后面。  
               在排序时，sort()方法会调用每个数组项的toString()转型方法，
			   然后比较得到的字符串，以确定如何排序，即使数组中的每一项都是数值，
			   sort()方法比较的也是字符串，因此会出现以下的这种情况：  
{% highlight js %}
  var arr1 = ["a", "d", "c", "bc"];  
  var arr2 = ["52", "1", "3", "27"];  
  console.log(arr1.sort());  
  console.log(arr2.sort());  
  console.log(arr2);  
{% endhighlight %}
  输出结果为：  
{% highlight js %}
  ["a", "bc", "c", "d"]  
  ["1", "27", "3", "5"]  
  ["1", "27", "3", "5"]  
{% endhighlight %}
  可知：**该方法改变原数组**  
  为了解决上述问题，sort()方法可以接收一个比较函数作为参数，以便我们指定哪个值位于哪个值得前面。
  比较函数接收两个参数，如果第一个参数应该位于第二个之前则返回一个负数，如果两个参数相等则返回0，
  如果第一个参数应该位于第二个之后则返回一个正数，以下就是一个简单的比较函数：  
{% highlight js %}
  function compare(value1, value2){  
    return value1-value2;  
  }  
  arr = ["21", "5", "32", "12"];  
  console.log(arr.sort(compare));  
{% endhighlight %}
  输出结果为：  
{% highlight js %}
  ["5", "12", "21", "32"]  
{% endhighlight %}
  如果需要通过比较函数产生降序排列的结果，只要交换比较函数返回的值即可：  
{% highlight js %}
  function compare(value1, value2){  
    return value2-value1;  
  }  
{% endhighlight %}
  
---  
### <label style="color:tomato">reverse()</label>  
  **reverse()**：反转数组项的顺序。  
{% highlight js %}
  var arr = [13, 24, 51, 3];  
  console.log(arr.reverse());  
  console.log(arr);    
{% endhighlight %}
  输出结果为：  
{% highlight js %}
  [3, 51, 24, 13]  
  [3, 51, 24, 13]  
{% endhighlight %}
  可知：**该方法改变原数组**  
  
---  
### <label style="color:tomato">concat()</label>  
  **concat()**：将参数添加到原数组中。这个方法先创建当前数组一个副本，然后将接收到的参数添加到这个副本的末尾，
                最后返回新构建的数组。在没有给**concat()**方法传递参数的情况下，它只是复制当前数组并且返回副本。  
{% highlight js %}
  var arr = [1, 3];  
  var arrCopy = arr.concat(4, [2, 5], 10);  
  console.log(arrCopy);  
  console.log(arr);  
{% endhighlight %}
  输出结果为：  
{% highlight js %}
  [1, 3, 4, 2, 5, 10]  
  [1, 3]   
{% endhighlight %}
  可知：**该方法不改变原数组**  
  从上面测试结果可以发现：传入的不是数组，则直接把参数添加到数组后面，如果传入的是数组，
  则将数组的各个项添加到数组中。但如果传入的是一个二维数组呢？  
{% highlight js %}
  var arr = [1, 3];  
  var arrConcat = arr.concat([0,[2, 3]]);  
  console.log(arrConcat);  
  console.log(arrConcat[arrConcat.length-1]);  
{% endhighlight %}
  输出结果为：  
{% highlight js %}
  [1, 3, 0, Array(2)]  
  [2, 3]  
{% endhighlight %}
  上述代码中，arrConcat数组的最后一项是一个包含两项的数组，
  也就是说**concat**方法只能传入数组中的每一项添加到数组中，
  如果传入数组中有些项是数组，那么也会把这一数组项当做一项添加到arrConcat中。  
  
---  
### <label style="color:tomato">slice()</label>  
  **slice()** :返回从原数组中指定开始下标到结束下标之间的项组成的新数组。
               slice()方法可以接收一或两个参数，即要返回项的起始和结束位置。
               在只有一个参数的情况下，slice()方法返回从该参数指定位置开始
               到当前数组末尾的所有项。如果有两个参数，该方法返回起始和结束
               位置之间的项————**不包括结束位置的项**。  
{% highlight js %}
  var arr = [1, 3, 5, 7, 9];  
  var arrSlice1 = arr.slice(1);  
  var arrSlice2 = arr.slice(2, 4);  
  var arrSlice3 = arr.slice(3, -1);  
  var arrSlice4 = arr.slice(-4, -1);  
  var arrSlice5 = arr.slice(-3, -4);  
  var arrSlice6 = arr.slice(-7, -2);    
  console.log(arr);  
  console.log(arrSlice1);  
  console.log(arrSlice2);  
  console.log(arrSlice3);  
  console.log(arrSlice4);  
  console.log(arrSlice5);  
  console.log(arrSlice6);    
{% endhighlight %}
  输出结果为：  
{% highlight js %}
  [1, 3, 5, 7, 9]  
  [3, 5, 7, 9]  
  [5, 7]  
  [7]  
  [3, 5, 7]  
  []  
  [1, 3, 5]  
{% endhighlight %}
  可知：**该方法不改变原数组**  
  1.传入值负数的绝对值小于arr.length时，该值加上arr.length 的值转换成正数。  
  2.传入值负数的绝对值大于arr.length时，该值转换为0.  
  3.传入值有二个参数，二个参数都已经转换成正数，第一位如果小于第二位，则返回为空数组.  
  
---  
### <label style="color:tomato">splice()</label>  
  **splice()**：实现删除、插入和替换操作。  
  
  **删除**：可以删除任意数量的项，只需要指定2个参数：要删除的第一项的位置和要删除的项数。  
  
> splice(0, 2)会删除数组中的前两项。  
		
  **插入**：可以向指定位置插入任意数量的项，只需要提供三个参数：起始位置、0（要删除的项数）、插入的项。  
  
> splice(2, 0, 4, 6)会从当前数组的位置2开始插入4和6。  
  
  **替换**：可以向指定位置插入任意数量的项，且同时删除任意数量的项，只需要指定3个参数：起始卫视、要删除的项数、插入任意数量的项。
			插入的项数不必与删除的项数相等。  
> splice(2, 1, 4, 6)会删除当前数组位置2的项，然后再从位置2开始插入4和6。  
  
  splice()方法始终返回一个数组，该数组中包含从原始数组中删除的项，如果没有删除任何项，则返回一个空数组。  
{% highlight js %}
  var arr = [1, 3, 5, 7, 9];  
  var arrRemoved1 = arr.splice(0, 2);  
  console.log(arr);  
  console.log(arrRemoved1);  
  var arrRemoved2 = arr.splice(2, 0, 4, 6);  
  console.log(arr);  
  console.log(arrRemoved2);  
  var arrRemoved3 = arr.splice(2, 2, 7, 8);  
  console.log(arr);  
  console.log(arrRemoved3);  
{% endhighlight %}
  输出结果为：  
{% highlight js %}
  [5, 7, 9]
  [1, 3]  
  [5, 7, 4, 6, 9]  
  []  
  [5, 7, 7, 8, 9]  
  [4, 6]  
{% endhighlight %}
  可知：**该方法改变原数组**  
  
---  
### <label style="color:tomato">indexOf() lastIndexOf</label>  
  **indexOf**：接收两个参数：要查找的项和（可选）表示查找起点位置的索引。其中，从数组的开头（位置0）开始向后查找。  
  **lastIndexOf**：上同。其中，从数组开头向后查找变为从数组末尾向前查找。  
  这两个方法都返回要查找的项在数组中的位置，或者在没找到的情况下返回-1。在比较第一个参数与数组中的每一个项时，使用全等操作符。  
{% highlight js %}
  var arr = [1, 3, 5, 7, 9];  
  console.log(arr.indexOf(3));  
  console.log(arr.lastIndexOf(7));  
  console.log(arr.indexOf(3, 5));  
  console.log(arr.lastIndexOf(3, 7));  
  console.log(arr.indexOf(2));  
  console.log(arr.lastIndexOf(2));  
{% endhighlight %}
  输出结果为：  
{% highlight js %}
  1  
  3  
  -1  
  1  
  -1  
  -1  
{% endhighlight %}
  其中第三个为什么返回-1，因为要查找3，初始查找位置是5，从前往后找，所有导致没有找到，3在初始查找位置前面。  
  
---  
### <label style="color:tomato">forEach()</label>  
  **forEach**：对数组进行遍历循环，对数组中的每一项运行给定函数。这个方法没有返回值。参数都是function类型，
			   默认有传参，参数分别是：遍历数组内容、以及对应的数组值索引、数组本身。  
{% highlight js %}
  var arr = [1, 3, 5];  
  arr.forEach(function(x, index, a){  
    console.log(x + " " + index + " " + a);    
  });    
{% endhighlight %}
  输出结果为：  
{% highlight js %}
  1 0 1,3,5 
  3 1 1,3,5  
  5 2 1,3,5  
{% endhighlight %}
  
---  
### <label style="color:tomato">map()</label>  
  **map()**：指“映射“，对数组中的每一项运行给定函数，返回每次函数调用的结果组成的数组。  
  下面代码利用map方法实现数组每个数求平方。  
{% highlight js %}
  var arr = [1, 2, 3, 4, 5];  
  var arrSquare =  arr.map(function(item){  
    return item * item;  
  });  
  console.log(arrSquare);  
{% endhighlight %}
  输出结果为：  
{% highlight js %}
 [1, 4, 9, 16, 25]
{% endhighlight %}
  
---  
### <label style="color:tomato">filter()</label>  
  **filter()**：“过滤”功能，数组中的每一项运行给定函数，返回满足过滤条件组成的数组。  
{% highlight js %}
  var arr = [1, 2, 3, 4, 5, 6];  
  var arr2 = arr.filter(function(x, index){  
    return index % 2 === 0 && x < 5;  
  });  
  console.log(arr2);
{% endhighlight %}
  输出结果为：  
{% highlight js %}
  [1, 3]  
{% endhighlight %}  
  
---  
### <label style="color:tomato">every()</label>  
  **every()**：判断数组中每一项都是否满足条件，只有所有项都满足条件，才会返回true。  
{% highlight js %}
  var arr = [1, 3, 5, 7];  
  var flag1 = arr.every(function(x){  
    return x % 2 === 0;  
  });    
  var flag2 = arr.every(function(x){  
    return x % 2 === 1;  
  });   
  console.log(flag1);  
  console.log(flag2);  
{% endhighlight %}  
  输出结果为：  
{% highlight js %}
  false  
  true
{% endhighlight %}  
  
---  
### <label style="color:tomato">some()</label>  
  **some()**：判断数组中是否存在满足条件的项，只要有一项满足条件，就会返回true。  
{% highlight js %}
  var arr = [1, 3, 5, 7];  
  var flag1 = arr.some(function(x){  
    return x < 0;  
  });    
  var flag2 = arr.some(function(x){  
    return x > 3;  
  });   
  console.log(flag1);  
  console.log(flag2);  
{% endhighlight %}  
  输出结果为：  
{% highlight js %}
  false  
  true
{% endhighlight %}  
  
---  
### <label style="color:tomato">reduce() reduceRight()</label>  
  这两个方法都会实现迭代数组的所有项，然后构建一个最终返回的值。  
  **reduce()**：从数组的第一项开始，逐个遍历到最后一项。  
  **reduceRight**：从数组的最后一项开始，向前遍历到第一项。  
  这两个方法都接收两个参数：一个在每一项调用的函数、作为归并基础的初始值（可选）。  
  传给reduce()和reduceRight()的函数接收4个参数：前一个值、当前值、项的索引值、数组对象。
  这个函数返回的任何值都会作为第一个参数自动传给下一项。第一次迭代发生在数组的第二项，
  因此第一个参数是数组的第一项，第二个参数就是数组的第二项。  
{% highlight js %}
 var arr = [1, 2, 3, 4];  
 var sum1 = arr.reduceRight(function(prev, cur, index, array){  
   return prev + cur; 
 });  
 var sum2 = arr.reduceRight(function(prev, cur, index, array){  
   return prev + cur; 
 }, 5);  
 console.log(sum1);  
 console.log(sum2); 
{% endhighlight %}
  输出结果为：  
{% highlight js %}
  10
  15  
{% endhighlight %}  
  
          
                 
  

  
  
  
