---
layout: post
title: 'PHP Attempted to call function "mcrypt_get_iv_size" from the global namespace'
date: 2018-11-04 13:01 -0300
categories: php
---

When I try to change a Prestashop ecommerce hosted on a ubuntu server i give the error “Attempted to call function \"mcrypt_get_iv_size\" from the global namespace”:

To solve this problem I installed the php7 mcrypt pachage in the server.
{% highlight bash %}
sudo apt install php7.0-mcrypt
{% endhighlight %}
and finally restarted fpm  service
{% highlight bash %}
sudo service php7.0-fpm restart
{% endhighlight %}
