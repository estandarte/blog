---
layout: post
title:  "Nothing to update - your database is already in sync with the current entity metadata"
date:   2018-11-01 16:45 -0300
categories: symfony
---

Every time I try to update the database schema in symfony and get this response, I follow this steps:

### 1. I check if the bundle is in the AppKernel.php
{% highlight php %}
public function registerBundles(): array
{
    $bundles = [
        new \Sylius\Bundle\AdminBundle\SyliusAdminBundle(),
        new \Sylius\Bundle\ShopBundle\SyliusShopBundle(),
        ...
    ];
}
{% endhighlight %}
### 2. I check if the entities are loaded on doctrine mapping info
{% highlight bash %}
bin/console doctrine:mapping:info
{% endhighlight %}
### 3. I run redis fhush db command
{% highlight bash %}
bin/console redis:flushdb
{% endhighlight %}
