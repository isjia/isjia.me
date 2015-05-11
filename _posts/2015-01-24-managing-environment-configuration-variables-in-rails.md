---
layout: post
category: 程序媛
tags: [jekyll, rails]
title: Rails生产环境变量管理的工具/方法
subtitle: Managing Environment Configuration Variables in Rails
writer: Jia
bg-image: 2015-01-24-bg-image.png
photo-credit: 来自网络
---

部署rails app到生产环境，通常需要配置一些只在production env才会用到的变量，而这些设置是需要保密的，可以用一下几种解决方案：


### 方案

- 方案一：直接写在Bash或者Zsh的profile中

- 方案二：使用dotenv这个gem

- 方案三：使用Figaro这个gem，heroku部署推荐用这个

- 方案四：使用scecret.yml

- 其他：使用private.yml

<!-- break -->

### Figaro实例

我用的是方案三：Figaro，步骤很简单，如下：

Gemfile中加入：`gem 'figaro'`

执行：`figaro install`

运行后会生成一个：config/application.yml文件，并且加入.gitignore中

在生产环境中编辑application.yml，加入需要的ENV变量：

比如我的：

{% highlight yaml linenos %}
production:
  RAILS_APP_DATABASE_PASSWORD: 123456
  SECRET_KEY_BASE: sDBKkdi689Hruvxpw8HrBHYTuVp8PTatgYG
{% endhighlight %}

原文参考：<http://www.gotealeaf.com/blog/managing-environment-configuration-variables-in-rails>