{% extends 'docs/modules/item-default.md' %}

{% block method_list %}
  {{ parent() }}

### getPageUrl($sPageCode)
  * $sPageCode - page file name

Method returns URL of category page.
Method gets list of {{ component.link('category-page') }} components attached on page and compiles list of parameters :slug to generate page URL.
{{ component.link('category-page') }} components must be attached on page so that child categories are higher than parent categories.

{% verbatim %}
```twig
title = "Catalog"
url = "/catalog/:parent_category/:category"
layout = "default"
is_hidden = 0

[CategoryPage]
slug = "{{ :category }}"
slug_required = 1
smart_url_check = 1
has_wildcard = 0
skip_error = 0

[CategoryPage ParentCategoryPage]
slug = "{{ :parent_category }}"
slug_required = 1
smart_url_check = 0
has_wildcard = 0
skip_error = 0
```
{% endverbatim %}
{% endblock %}