---
layout: post
title: 'PHP message: PHP Notice:  Use of undefined constant PHPEXCEL_ROOT'
date: 2018-11-03 11:02 -0300
categories: symfony
---

When I try to upgrade an Prestashop ecommerce hosted on a ubuntu server i give the error “PHP message: PHP Notice:  Use of undefined constant PHPEXCEL_ROOT”:

To solve this problem I installed the PHP7 zip pachage in the server.
{% highlight bash %}
sudo apt install php7.0-zip
{% endhighlight %}
and finally restarted fpm  service
{% highlight bash %}
sudo service php7.0-fpm restart
{% endhighlight %}
