---
layout: post
category: 程序媛
tags: [web, jekyll, tutorial]
title: 从零开始打造程序员的个人博客
subtitle: Jekyll Tutorial by Example
bg-image: post-bg.jpg
photo-credit: NASA on The Commons
writer: Jia
imgfolder: /assets/2014-01-16/
---
## Jekyll的文件和目录结构

*所有的配置文件都是基于[YAML](https://en.wikipedia.org/wiki/YAML)格式的。*

### _config.yml
  * 创建一个_config.yml文件
  * 加入如下的配置：

{% highlight yaml %}
name:  "A Jekyll Blog"
description:  “Jekyll Tutorial by Example"
url: “http://localhost:4000” #这里与你的域名保持一致，注意没有末尾的/，本地可暂时使用http://localhost:4000
paginate: 10
markdown: rdiscount
permalink: pretty
pygments: true #可选，需要提前安装pygments
{% endhighlight %}


<!-- break -->

### _include 文件夹
  * 创建_include文件夹
  * _include文件夹是用来存放”template partials“，比如网站的一些公用部分header，footer等
  * 注意必须已下滑线开头


### _layouts文件夹
  * 创建_layouts文件夹
  * 存放博文（posts）的layouts文件。可以有多个layouts分别用于不用类型的博文。
  * 这里我们先创建这个文件夹，稍后填充内容。

### _posts文件夹
  * 创建_posts文件夹
  * 存放Markdown或者HTML、Textile等博客内容文件。
  * 完成后现在的目录结构是这样的：

![]({{page.imgfolder}}EEC08E94-9087-4879-9F35-7B1BD206F84E.png)

### 第一次运行
  * 现在可以在终端运行：jekyll build
  * 应该看到successful的提示消息  

![]({{page.imgfolder}}83E20203-B936-4B74-A792-918CD78EECF9.png)

  * 生成的网站页面存放在_site目录中，当然现在还不会实际生成任何文件，因为我们还没有填充内容
  * 现在我们开始给网站填充内容


## 内容填充
  * Jekyll网站中所有的内容都来自文本文件，比如markdown，HTML
  * 这些文本文件会按一定的规则被处理后放入网站相应的位置中
  * 比如有一个index.md在根目录下，相应地会生成一个index.html在网站的根目录下
  * 同样的，如果about/index.html文件将被放入网站的about/index.html中
  * 按照这个方式可以放置好所有的静态页面，下面我们来试试看：
  
    >创建一个index.md文件在根目录中，即_config.yml同样的地方。
    >随意填写一些内容到index.md中
    >添加”front matter“到文件的头部，这也是一种Jekyll会用到的配置信息：  

{% highlight teX %}
---
title: Hello, World!  
---  
{% endhighlight %}

  * 注意front matter一定要放置在两行”—“之间, 填充好的内容大致如下：  

  ![]({{page.imgfolder}}2246E47C-6377-421D-BCC5-A1C7E4FB7B2C.png)

  * 回到命令行窗口，运行jekyll build，现在应该可以看到生成了_site文件夹，_site中包含index.html文件，可以用浏览器打开这个文件，看到markdown文件中的内容已经被加入到index.html中了，形成了一个网页。
  * _site文件夹中的内容就是最终要部署到web服务器端的网站。

## 自动生成
  * 不想每次手动执行jekyll build，可以设置自动build
  * 当项目文件夹中的文件内容发生修改，jekyll build会自动运行
  * 并且在本地的http://localhost:4000可以随时看到修改后的效果
  * 在命令行运行：jekyll server --watch ，自动build生效，并且部署到http://127.0.0.1:4000/
  * 现在可以在(http://localhost:4000/)看到网站的效果了。
  * 如果不希望部署到localhost，仅仅自动build的话：jekyll build --watch 即可
  * 为了验证自动build部署，我们回到index.md，随便修改一些内容，再回到浏览器刷新查看效果。

## 重点：主题制作
  * 我们已经大致了解的Jekyll的工作方式，现在可以开始创建我们自己的网站主题了。
  * 这需要一些HTML和CSS的技术
  * 我这里会使用bootstrap框架来示范一个例子

### 下载Bootstrap
  * 到Bootstrap官网下载：<http://getbootstrap.com/>
  * 将解压后的文件夹放置在项目的根目录中，现在项目文件夹看起来大概是这个样子：  

  ![]({{page.imgfolder}}9D51944F-35B8-491B-A2BC-87075C557564.png)

### 创建一个布局
  * 还记得我们之前创建的_layouts文件夹吗，我们现在来创建一个布局
  * 这个默认布局将用于所有我需要发表的blog文章上。
  * 这个布局将包含一个header，menu，footer，和其他一些页面的样式。
  * 在_layouts创建一个default.html文件，放置如下内容：  

![]({{page.imgfolder}}99585B11-4A13-4A45-B4B8-16D41643DF11.png)

>Liquid Template System

  * 可能你已经发现了在上面的default.html文件中有一些看起来比较奇怪的代码，包含在两个大括号之间  
  * 这是，Liquid Template System，一种由Shopify公司最先创造的一种技术，在Jekyll中我们会用到他
  * 简单的说，如果想在文件中带入一些参数，可将参数名放在两个大括号之间，比如{{ site.name }}
  * Jekyll使用了一些全局变量：site，page，content, paginator等，稍后我们会用到的
  * 其中site变量包含了我们在_config.yml中配置的一些参数，比如我们可以使用site.name来调用_config.yml中设置的name参数。
  * 同样地在front matter中设置的参数也可以通过这个方法来调用：比如每个页面的title，可以通过page.title来调用

### 调用layout
  * 如果现在回到浏览器，你实际上还看不到任何变化，应为我们只是创建了一个布局，还没有真正使用他
  * 回到index.md文件，在front matter中添加：  
layout: default
  * 保持layout的名字与文件名一致，这里是default
  * 回到浏览器，刷新，可以看到首页了吧：  

![]({{page.imgfolder}}24B77BB2-1C4A-40F2-981B-F02683C1755B.png)

### 使用Includes
  * 现在我们要将网站中通用的一些页头页脚等布局模块放置到include中
  * 将_layouts/default.html文件中{{ content }} *之前*的代码放入到新的文件_includes/header.html中
  * 将_layouts/default.html文件中{{ content }} *之后*的代码放入到新的文件_includes/footer.html中
  * 现在有3个文件，_includes/header.html, _includes/footer.html, _layouts/default.html
  * 此时，如果你刷新浏览器，只剩下文本内容了，布局全部不见了，因为我们还没有加入inclues中的布局模板
  * 加入相应的header和footer到default中：  

![]({{page.imgfolder}}3F44AFE1-CFFD-448F-BEA6-F8A449ED077D.png)

  * 回到浏览器刷新，布局又回来了
  * 简单来说includes就是将对应的文件copy到当前的位置使用

### 创建一个边栏
  * 在_includes中创建一个叫sidebar.html的文件
  * 随意填写一些aboutme的内容：
  * 对default.html中的content部分进行调整，加入sidebar

### 编写Blog
  * Blog的布局框架搭建好了，接着下来我们来处理发布博客这件事
  * 所有要发布的博文内容都会被放到_posts这个目录下
  * 目录中的内容可以使用markdown和html或者其他格式，jekyll会自动处理
  * 也就是说对于复杂内容可以使用`html`来格式化，简单内容推荐用`markdown`
  * 文件命名格式：YYYY-MM-DD-[POST SLUG].[FORMAT]，比如：2014-12-12-taobao-da-jian-jia.md
  * 小写，连字符（-），不能包含空格
  * 试着创建几个post，随意填写一些内容，参考样例：
  * 注意每个post的front matter：我们设置了两个参数：title，和layout
  * 日期在文件名中指定了，所以在front matter里不再需要设置了

遍历post loops

  * 现在我们已经有了2篇博文需要发布，接下来就是要添加到页面上去，让他们显示出来
  * 首先我们在边栏中创建最新发布的博文链接，添加下面的代码到sidebar.html中
  * 在这个loop中主要包括：1）遍历5个post 2）显示每个post的标题，并加上链接

Main Loop

  * 简单的loop我们已经了解了，接下来我想在首页上显示我的全部的blog信息
  * 我们先删除临时的index.md，重新创建一个index.html的文件
  * 添加for循环，读取10个posts
  * 显示每个post的内容，标题，日期，等
  * 刷新页面，可以看到主页上显示的posts。

添加筛选条件，Filters

  * Filters是一个很有用的工具，用来挑选出满足一定条件的posts来
  * 编写filters需要一点Ruby语言的基础，这里给几个常用的范例，大家参考:
  <pre>
    {<span>{ post.title | truncatewords: 10 | capitalize }</span>}
    {<span>{ post.date | date: "%m-%d-%Y" }</span>}  
  </pre>
  * filter可以叠加使用

博文页面，post content pages

  * 在首页上点击read more，进入post page
  * 看起来一切正常
  * 丰富我们的post页面，添加comment system（Disqus，LiveFyre）和social share buttons，我们需要为post单独创建一个layout

post layout

  * 在_layouts中创建一个空白的post.html模板: 代码如下
  * 修改posts的layout参数：为post

分页

  * 需要用到global设置：paginator
  * 分页仅在homepage有效
  * 修改_config.yml中paginator参数，这里我们修改为1，为了便于测试，修改config配置后需要重启jekyll server
  * 修改一些首页的loop条件：paginator.posts，删除limit设置，因为这里会调用config中的设置
  * 添加上一页，下一页链接：代码如下
  * _sites中新增了page2目录

创建一个aboutme的静态页面

  * 创建about/index.md文件
  * 添加一些内容介绍你自己，注意在front matter中使用default布局
  * 现在可以在http://localhost:4000/about/中访问这个静态页面

完成

  * 到这里一个完整的jekyll网站就完成了
  * 鼓掌

**参考原文: <https://www.andrewmunsell.com/tutorials/jekyll-by-example/tutorial>**
