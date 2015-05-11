---
layout: post
category: 程序媛
tags: [jekyll, tutorial]
title: Jekyll中使用Pygments设置代码高亮显示
subtitle: Using Pygments to highlight codes in Jekyll
writer: Jia
bg-image: 2015-01-10-bg-image.jpg
photo-credit: 来自网络
---

- blog已经可以在github.io的域名上跑起来了，
- 也发布了一些内容，
- 那么接着下来程序员就免不了需要发布一些带有程序代码的文章，
- 为了让blog看起来更Hack一点，我要把代码高亮显示。

<!-- break -->

## 步骤如下

### 修改_config.yml
这里要注意Jekyll已经将`pygments`的设置修改为`highlighter`了，因此如果还是设置为：`pygments: true`的话会看到错误提示：

       Deprecation: The 'pygments' configuration option has been renamed to 'highlighter'. Please update your config file accordingly. The allowed values are 'rouge', 'pygments' or null.

正确的设置是：`highlighter: pygments`

### 在本地机器上安装pygments，并生成css样式文件
- Pygments是基于Python的，机器上需要先安装Python
- Mac已经自带了python，这里以mac为例：
  - 命令行运行：`sudo easy_install pygments`
  - `cd yourJekyllProject/css`
  - `pygmentize -S default -f html > ./highlights.css` ，这里的vim是一种代码高亮style，pygments支持的style在这里看[demo](http://pygments.org/demo/)，选择你喜欢的样式。更多说明请看官网的[QuickStart](http://pygments.org/docs/quickstart/)。
  - 在页面引用前面生成的highlights.css文件。
  - 另外也可以使用跟github一样的样式：[syntax.css](https://github.com/mojombo/tpw/blob/master/css/syntax.css)

### 在文章中使用代码高亮显示
<p><pre>
  {<span>% highlight css linenos %</span>}
    div{
        height:50px;/*是width的一半*/
        width:100px;
        background:#9da;
        border-radius:50px 50px 0 0;/*半径至少设置为height的值*/
    }
  {<span>% endhighlight %</span>}
</pre></p>

其中第一个参数css是语法名，第二个参数linenos会强制显示行号，效果如下：

{% highlight css linenos %}
div{
    height:50px;/*是width的一半*/
    width:100px;
    background:#9da;
    border-radius:50px 50px 0 0;/*半径至少设置为height的值*/
}
{% endhighlight %}
