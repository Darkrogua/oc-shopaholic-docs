{% extends 'docs/modules/model-default.md' %}

{% block fields %}
{{ parent() }}

### Price fields

|  Name | Type | Description |
|-------|------|--------|
|price|string|Formatted price string (**"20,10"**)|
|price_value|float|Float price value (**20.1**)|
|price_with_tax|string|Formatted price with tax string (**"20,10"**)|
|price_with_tax_value|float|Float price with tax value (**20.1**)|
|price_without_tax|string|Formatted price without tax string (**"16,75"**)|
|price_without_tax_value|float|Float price without tax value (**16.75**)|
|tax_price|string|Formatted tax price string (**"3,35"**)|
|tax_price_value|float|Float tax price value (**3.35**)|

### Old price fields

|  Name | Type | Description |
|-------|------|--------|
|old_price|string|Formatted old price string (**"21,00"**)|
|old_price_value|float|Float old price value (**21**)|
|old_price_with_tax|string|Formatted old price with tax string (**"21,00"**)|
|old_price_with_tax_value|float|Float old price with tax value (**21**)|
|old_price_without_tax|string|Formatted old price without tax string (**"17,50"**)|
|old_price_without_tax_value|float|Float old price without tax value (**17.5**)|
|tax_old_price|string|Formatted tax old price string (**"3,50"**)|
|tax_old_price_value|float|Float tax old price value (**3.5**)|

### Total price fields

|  Name | Type | Description |
|-------|------|--------|
|total_price|string|Formatted total price string (**"40,20"**)|
|total_price_value|float|Float total price value (**40.2**)|
|old_total_price|string|Formatted old total price string (**"42,00"**)|
|old_total_price_value|float|Float old total price value (**42**)|
|discount_price|string|Formatted discount price string (**"1,80"**)|
|discount_price_value|float|Float discount price value (**1.8**)|
{% endblock %}
