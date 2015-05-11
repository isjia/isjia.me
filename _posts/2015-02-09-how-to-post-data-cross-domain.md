---
layout: post
category: 程序媛
tags: [rails, web]
title: 关于跨域提交在rails中的实现方法
subtitle: How to post data cross domain in rails
writer: Jia
bg-image: Bay_Bridge_from_Yerba_Buena_Island.jpg
photo-credit: Graham Gibson
---

刚好这周碰到一个项目，需要将前端页面和后端数据库部署到不同域名的服务器上下，所以开始寻觅有哪些解决跨域数据提交的方案。

另外最近的几个网站项目都采用了jekyll架构的静态网站形式，主要是维护方便，对环境的依赖几乎是零，可以很方便的部署到任意web服务器中，对于更新量不大的网站来说是非常合适的。现在看起来使用静态页面生成器开发和部署静态网站也是一个趋势，目前在github有很好的支持，对于重前端轻内容的展示型企业门户也非常适合。

那么问题来了，一个全静态的网站是交互的，即使是一个最简单留言也不能提交，为了给自己的blog和公司的网站加上contact us功能，查了一下网上的可用资源，最后选定用[FormKeep](https://formkeep.com)这个应用，可以免费（会有一些功能限制），也可以选择1$-99$的付费方案。因为数据量不大，目前还是选择免费就够用了。除了FormKeep以外，现在很多网站的comments都使用了[Disqus](https://disqus.com/)这个解决方案来补充静态网站的留言功能。

所有这些方案背后应该都需要解决一个跨域提交数据的基本问题，考虑到安全性的原因Ajax默认是不支持跨域提交的。google一圈之后大致确认了目前常见的方案有一下几种：

- CORS：Cross-Origin Resource Sharing，W3C标准支持方案，移动端支持较好，IE9以上桌面浏览器支持
- jsonp：是get形式的规避解决方案，承载的信息量有限，所以信息量较大时不适合
- ajax：开启跨域模式：crossDomain: true

结合项目的需求，以可以跨域post为主，以内对安全性几乎没有要求，暂时就是用ajax直接跨域提交，在服务端开启CORS允许接受跨域信息，具体方案如下：
<!-- break -->

1. 客户端代码, 设置Ajax请求参数crossDomain为true

{% highlight javascript linenos %}
$.ajax({
  type: 'POST',
  crossDomain: true, // sert crossDomain true
  url: 'http://localhost:3000/sub_emails',
  data: data ,
  dataType: 'json',
  success: function(responseData) {
    //省略
  }
});
{% endhighlight %}

2. 修改Rails Controller代码，去除token验证并设置 CORS ACCESS HEADER

{% highlight ruby linenos %}
class SubEmailsController < ApplicationController

  skip_before_filter :verify_authenticity_token

  before_filter :cors_preflight_check
  after_filter :cors_set_access_control_headers

  def create
    SubEmail.create(email: params[:email])
    render status: 200, json: { message: "Sub Successful" }
  end

  private 

  def cors_set_access_control_headers
    headers['Access-Control-Allow-Origin'] = '*'
    headers['Access-Control-Allow-Methods'] = 'POST, GET, PUT, DELETE, OPTIONS'
    headers['Access-Control-Allow-Headers'] = 'Origin, Content-Type, Accept, Authorization, Token'
    headers['Access-Control-Max-Age'] = "1728000"
  end

  def cors_preflight_check
    if request.method == 'OPTIONS'
      headers['Access-Control-Allow-Origin'] = '*' //允许来自任意域的提交
      headers['Access-Control-Allow-Methods'] = 'POST, GET, PUT, DELETE, OPTIONS'
      headers['Access-Control-Allow-Headers'] = 'X-Requested-With, X-Prototype-Version, Token'
      headers['Access-Control-Max-Age'] = '1728000'

      render :text => '', :content_type => 'text/plain'
    end
  end
end
{% endhighlight %}

简单验证可以实现跨域提交，目前暂时采用次方案。方案中关闭了CSRF Token验证，所以很容易被人CSRF攻击。可以限制Access-Control-Allow-Origin的来源，做有限准入。
