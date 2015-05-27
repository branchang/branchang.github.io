---
layout:post
title:uwsig,nginx部署基于Django的cms开源项目mezzanine
---

系统，趁着休假期间时间充裕前后后用了几天时间终于勉强可以访问.
vps使用的linode，10$每月，也曾经考虑DigtalOcean,不过网上评价不高,也不想冒险.
cms系统的选择问题，之前自己使用github提供的静态页面blog，想现看看基于Django的开源搭建，发现这样的项目不多而且使用的人也不少，直接导致了后面的一路坑.(会不会后悔没有使用wordpress : \ )
Mezzanine is a powerful, consistent, and flexible content management platform. Built using the Django framework, Mezzanine provides a simple yet highly extensible architecture that encourages diving in and hacking on the code.

Django建议使用apache,mod_python部署，这里用ngnix,uwsgi,数据库选择postgres.
vps系统为ubuntu14.04lts.
##Mezzanine安装

{% highlight bash %}
$ pip install mezzaniz
{% endhighlight %}
或源码安装
{% highlight bash %}
$ python setup.py install
{% endhighlight %}
创建一个新的mezzanine项目
{% highlight bash %}
$ mezzanine-project project_name
$ cd project_name
{% endhighlight %}

创建和配置对应的数据库,执行下面的步骤之前要安装和配置好所使用的数据库，这里使用的是postgres
{% highlight bash %}
$ python manage.py createdb --noinput
{% endhighlight %}

运行development mode，模式访问http://127.0.0.1:8000，用于调试开发
{% highlight bash %}
$ python manage.py runserver
{% endhighlight %}

##postgres 安装配置

{% highlight bash %}
apt-get install postgresql-9.4
{% endhighlight %}

