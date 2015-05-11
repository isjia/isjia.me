---
layout: post
category: 程序媛
tags: [web, css]
title: CSS3 Tips：圆角效果
bg-image: post-bg.jpg
photo-credit: NASA on The Commons
writer: Jia
---

CSS3中使用**border-radius**是向元素添加圆角边框。

## 使用方法

### 10px的圆角
**border-radius:10px;** /* 所有角都使用半径为10px的圆角 */ 

![效果图](http://img.mukewang.com/52e216d2000195ef01110111.jpg)

### 顺时针定义圆角
**border-radius: 5px 4px 3px 2px;** /* 四个半径值分别是左上角、右上角、右下角和左下角，顺时针 */ 

![效果图](http://img.mukewang.com/52e216f9000131a201110111.jpg)

不要以为border-radius的值只能用**px**单位，你还可以用**百分比**或者**em**，但兼容性目前还不太好。

<!-- break -->

### 实心上半圆：

方法：把宽度（width）设为高度(height)的一半，并且只设置左上角和右上角的半径与元素的高度一致（大于也是可以的）。
    
{% highlight css linenos %}
div{
  height:50px;/*是width的一半*/
  width:100px;
  background:#9da;
  border-radius:50px 50px 0 0;/*半径至少设置为height的值*/
}
{% endhighlight %}
    
### 实心圆：

方法：把宽度（width）与高度(height)值设置为一致（也就是正方形），并且四个圆角值都设置为它们值的一半。如下代码：
    
{% highlight css linenos %}  
div{
  height:100px;/*与width设置一致*/
  width:100px;
  background:#9da;
  border-radius:50px;/*四个圆角值都设置为宽度或高度值的一半*/
}
{% endhighlight %}

### 参考资料：
 - iMooc CSS3 教程：<http://www.imooc.com/code/380>
