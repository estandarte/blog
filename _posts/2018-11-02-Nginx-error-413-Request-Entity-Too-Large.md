---
layout: post
title: 'Nginx error “413 Request Entity Too Large”'
date: 2018-11-01 16:45 -0300
categories: symfony
---

When I try to upload files in an Prestashop ecommerce hosted on a nginx server i give the nginx error “413 Request Entity Too Large”:

To solve this problem I changed the client_max_body_size in nginx.
{% highlight nginx %}
server {
    listen 443 ssl;

    root /var/www/;
    index index.php index.html index.htm;
    server_name example.com.br;

    client_max_body_size 128M;
}
{% endhighlight %}
and in php-fpm php.ini I changed upload_max_filesize, post_max_size and memory_limit:
{% highlight apache %}
upload_max_filesize = 128M
post_max_size = 128M
memory_limit = 256M
{% endhighlight %}
and finally restarted fpm  service
{% highlight bash %}
sudo service php7.0-fpm restart
{% endhighlight %}
