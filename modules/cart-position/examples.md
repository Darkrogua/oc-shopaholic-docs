{% extends 'docs/modules/examples-default.md' %}

{% block content %}
* [Example 1: Render block with mini-cart](#example-1-render-block-with-mini-cart)
* [Example 2: Render block with cart positions on checkout page](#example-2-render-block-with-cart-positions-on-checkout-page)

## Example 1: Render block with mini-cart

### 1.1 Task

Render block with mini-cart.

> Block with mini-cart is often located in the header of your site.

![](./../../../assets/images/fronend-cart-1.png)

### 1.2 How can i do it?

> Example uses {{ get_component('cart').link('cart') }} component.
Component method returns {{ collection.link() }} class object.
All available fields and methods of **{{ collection.class }}** class you can find in {{ collection.link('section') }}

```plantuml
@startuml
:Create page file;
note left
    For example: **pages/index.htm**
end note
:Attach **Cart** component;
:Get CartPositionCollection object
from Cart component;
:Render cart positions
and total price of positions;
@enduml
```

### 1.3 Source code

{% verbatim %}
```twig
title = "Index page"
url = "/"
layout = "main"
is_hidden = 0


[Cart]
==

{# Get cart positions #}
{% set obCartPositionList = Cart.get() %}
{% if obCartPositionList.isNotEmpty() %}
    <ul>
    {% for obCartPosition in obCartPositionList %}
        <li>{% partial 'product/cart-position/cart-position' obCartPosition=obCartPosition %}</li>
    {% endfor %}
    </ul>
    
    <div>Total price: {{ obCartPositionList.getTotalPrice() }} {{ obCartPositionList.getCurrency() }}</div>
{% else %}
    <div>Cart is empty</div>
{% endif %}
```
{% endverbatim %}

File: **product/cart-position/cart-position.htm**
{% verbatim %}
```twig
{% set obOffer = obCartPosition.item %}
{% set obProduct = obOffer.product %}

<a href="{{ obProduct.getPageUrl('product') }}">
    <div>
        {% if obProduct.preview_image is not empty %}
            <img src="{{ obProduct.preview_image.path }}" itemprop="image" alt="{{ obProduct.preview_image.description }}" title="{{ obProduct.preview_image.title }}">
        {% endif %}
        <h3 itemprop="name">{{ obProduct.name }}</h3>
        {% if obProduct.preview_text is not empty %}
            <div itemprop="description">
                {{ obProduct.preview_text }}
            </div>
        {% endif %}
        <span price="{{ obCartPosition.price_value }}">{{ obCartPosition.price }}</span>
        {% if obCartPosition.discount_price_value > 0 %}
            <span price="{{ obCartPosition.old_price_value }}">{{ obCartPosition.old_price }}</span>
        {% endif %}
        <input type="number" name="quantity" value="{{ obCartPosition.value }}" max="{{ obOffer.quantity }}" min="1">
    </div>
</a>
```
{% endverbatim %}

## Example 2: Render block with cart positions on checkout page

### 2.1 Task

Render block with cart positions on checkout page.

![](./../../../assets/images/fronend-cart-2.png)

### 2.2 How can i do it?

> Example uses {{ get_component('cart').link('cart') }} component.
Component method returns {{ collection.link() }} class object.
All available fields and methods of **{{ collection.class }}** class you can find in {{ collection.link('section') }}

```plantuml
@startuml
:Create page file;
note left
    For example: **pages/checkout.htm**
end note
:Attach **Cart** component;
:Get CartPositionCollection object
from Cart component;
:Render cart positions
and total price of positions;
@enduml
```

### 2.3 Source code

{% verbatim %}
```twig
title = "Checkout page"
url = "/checkout"
layout = "main"
is_hidden = 0

[Cart]
==

{# Get cart positions #}
{% set obCartPositionList = Cart.get() %}
{% if obCartPositionList.isNotEmpty() %}
    <ul>
    {% for obCartPosition in obCartPositionList %}
        <li>{% partial 'product/cart-position/cart-position' obCartPosition=obCartPosition %}</li>
    {% endfor %}
    </ul>
    
    <div>Total price: {{ obCartPositionList.getTotalPrice() }} {{ obCartPositionList.getCurrency() }}</div>
{% else %}
    <div>Cart is empty</div>
{% endif %}
```
{% endverbatim %}

File: **product/cart-position/cart-position.htm**
{% verbatim %}
```twig
{% set obOffer = obCartPosition.item %}
{% set obProduct = obOffer.product %}

<a href="{{ obProduct.getPageUrl('product') }}">
    <div>
        {% if obProduct.preview_image is not empty %}
            <img src="{{ obProduct.preview_image.path }}" itemprop="image" alt="{{ obProduct.preview_image.description }}" title="{{ obProduct.preview_image.title }}">
        {% endif %}
        <h3 itemprop="name">{{ obProduct.name }}</h3>
        {% if obProduct.preview_text is not empty %}
            <div itemprop="description">
                {{ obProduct.preview_text }}
            </div>
        {% endif %}
        <span price="{{ obCartPosition.price_value }}">{{ obCartPosition.price }}</span>
        {% if obCartPosition.discount_price_value > 0 %}
            <span price="{{ obCartPosition.old_price_value }}">{{ obCartPosition.old_price }}</span>
        {% endif %}
        <input type="number" name="quantity" value="{{ obCartPosition.value }}" max="{{ obOffer.quantity }}" min="1">
    </div>
</a>
```
{% endverbatim %}
{% endblock %}
