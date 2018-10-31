---
layout: post
title:  "How I create entities in symfony"
date:   2018-10-30 22:50 -0300
categories: symfony
---
This are the steps that I generally follow to generate new entities in Symfony:

1. I create the Entity map in xml format:

{% highlight xml %}
<?xml version="1.0" encoding="UTF-8" ?>
<doctrine-mapping xmlns="http://doctrine-project.org/schemas/orm/doctrine-mapping"
                  xmlns:gedmo="http://gediminasm.org/schemas/orm/doctrine-extensions-mapping">
    <mapped-superclass name="Estandarte\MercadoLivre\Entity\Product" table="mercadolivre_product">
        <id name="id" column="id" type="integer">
            <generator strategy="AUTO" />
        </id>
        <field name="itemId" column="item_id" type="string" unique="true" nullable="false"/>
        <field name="title" column="title" type="string"/>
        <field name="categoryId" column="category_id" type="string" nullable="true"/>
        <field name="price" column="price" type="float" nullable="true"/>
        <field name="availableQuantity" column="available_quantity" type="integer" nullable="true"/>
        <field name="buyingMode" column="buying_mode" type="string" nullable="true"/>
        <field name="listingTypeId" column="listing_type_id" type="string" nullable="true"/>
        <field name="condition" column="product_condition" type="string" nullable="true"/>
        <field name="warranty" column="warranty" type="string" nullable="true"/>
        <field name="description" column="description" type="string" nullable="true"/>
        <field name="thumbnail" column="thumbnail" type="string" nullable="true"/>
        <many-to-one field="product" target-entity="Sylius\Component\Core\Model\Product">
            <join-column name="product_id" referenced-column-name="id" nullable="true" on-delete="SET NULL"/>
        </many-to-one>
    </mapped-superclass>

</doctrine-mapping>
{% endhighlight %}

2. I create the Entity class in the Entity directory:

{% highlight php %}
<?php

namespace Estandarte\MercadoLivre\Entity;

use Sylius\Component\Resource\Model\ResourceInterface;
use Sylius\Component\Core\Model\Product as CoreProduct;

/**
 * Attribute
 */
class Attribute implements ResourceInterface
{
    private $id;
    private $name;

    /**
     * Get the value of Attribute
     *
     * @return mixed
     */
    public function getId()
    {
        return $this->id;
    }

    /**
     * Set the value of Attribute
     *
     * @param mixed id
     *
     * @return self
     */
    public function setId($id)
    {
        $this->id = $id;

        return $this;
    }

    /**
     * Get the value of Name
     *
     * @return mixed
     */
    public function getName()
    {
        return $this->name;
    }

    /**
     * Set the value of Name
     *
     * @param mixed name
     *
     * @return self
     */
    public function setName($name)
    {
        $this->name = $name;

        return $this;
    }

}
{% endhighlight %}

3. I run the schema update (in dev environment):

{% highlight bash %}
bin/console doctrine:schema:update --force
{% end highlight %}
