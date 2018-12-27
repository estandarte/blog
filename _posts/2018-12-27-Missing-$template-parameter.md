---
layout: post
title: 'SmartyException: 0():Missing '$template' parameter'
date: 2018-11-07 18:50 -0300
categories: php
---
I am creating a paymente module for prestashop. When I created the first controller that would not return an html page based on a smarty template I got the following error message "0(): Missing '$template' parameter":

To solve this problem I kill the controller with a die command after change the header of the response.
{% highlight php %}
http_response_code(201);
die();
{% endhighlight %}
