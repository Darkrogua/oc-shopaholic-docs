{% extends 'docs/modules/examples-default.md' %}

{% block content %}
* [Example 1: Render subscription product](#example-1-render-subscription-product)

## Example 1: Render subscription product

### 1.1 Task

Render product list with subscription variants.

### 1.2 How can i do it?

```plantuml
@startuml
:Create page file;
:Get product list from
ProductCollection class;
:Render product list;
:Get offer list from
ProductItem object;
:Apply sorting by period
to OfferCollection class
object;
:Render offer list;
@enduml
```

### 1.3 Source code

File: **pages/subscription.htm**
{% verbatim %}
```twig
title = "Subscription"
url = "/subscriptions"
layout = "main"
is_hidden = 0

[ProductList]
sorting = "popularity|desc"
==

{# Get active product list #}
{% set obProductList = ProductList.make().active() %}

{% for obProduct in obProductList %}
  {# Get offer list #}
  {% set obOfferList = obProduct.offer.sortByPeriod() %}
  {# Render offer list #}
  {% for obOffer in obOfferList %}
    <div>
      <span>{{ obOffer.name }}</span>
      <span>{{ obOffer.subscription_period.name }}</span>
    </div>
  {% endif %}
{% endfor %}
```
{% endverbatim %}
{% endblock %}