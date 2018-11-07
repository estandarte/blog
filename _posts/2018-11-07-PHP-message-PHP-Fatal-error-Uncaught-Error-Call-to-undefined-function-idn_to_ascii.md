---
layout: post
title: 'PHP message: PHP Fatal error:  Uncaught Error: Call to undefined function idn_to_ascii'
date: 2018-11-07 18:50 -0300
categories: php
---
When I try to install a Prestashop ecommerce hosted on a ubuntu server i give the error "PHP message: PHP Fatal error:  Uncaught Error: Call to undefined function idn_to_ascii":

To solve this problem I installed the php7 intl pachage in the server.
{% highlight bash %}
sudo apt install php7.0-intl
{% endhighlight %}
and finally restarted fpm  service
{% highlight bash %}
sudo service php7.0-fpm restart
{% endhighlight %}
