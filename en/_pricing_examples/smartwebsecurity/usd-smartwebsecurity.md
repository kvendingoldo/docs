For example, the total cost of sending 315.04 million requests per month to {{ sws-name }} for analysis will be:
> 0.01 × ${{ sku|USD|sws.requests.v1|number }} + 0.99 × {{ sku|USD|sws.requests.v1|pricingRate.0.01|string }} + 9 × {{ sku|USD|sws.requests.v1|pricingRate.1|string }} + 90 × {{ sku|USD|sws.requests.v1|pricingRate.10|string }} + 215.04 × {{ sku|USD|sws.requests.v1|pricingRate.100|string }} = {% calc [currency=USD] 0.01 × {{ sku|USD|sws.requests.v1|number }} + 0.99 × {{ sku|USD|sws.requests.v1|pricingRate.0.01|number }} + 9 × {{ sku|USD|sws.requests.v1|pricingRate.1|number }} + 90 × {{ sku|USD|sws.requests.v1|pricingRate.10|number }} + 215,04 × {{ sku|USD|sws.requests.v1|pricingRate.100|number }} %} excluding VAT.

Where:

* 0.01 × ${{ sku|USD|sws.requests.v1|number }}: Non-billable threshold of 0.01 million requests.
* 0.99 × {{ sku|USD|sws.requests.v1|pricingRate.0.01|string }}: Cost of the subsequent 0.99 million requests.
* 9 × {{ sku|USD|sws.requests.v1|pricingRate.1|string }}: Cost of the subsequent 9 million requests.
* 90 × {{ sku|USD|sws.requests.v1|pricingRate.10|string }}: Cost of the subsequent 90 million requests.
* 215.04 × {{ sku|USD|sws.requests.v1|pricingRate.100|string }}: Cost of the remaining 215.04 million requests.