# Using the API

### [Full Swagger docs ↗](http://api.cscale.io/api/cscale-swagger-docs)

Consider the information below a "highlight reel," but the best of the best (and all the rest) is available at the link above.&#x20;

### [API Testing Notebook ↗](https://drive.google.com/drive/u/2/folders/1Q\_\_pMVDnPgzv01aWb-cfakifKtuqyH4K)

Skip the swagger and get right to the good stuff - here's a Python Notebook with a panoply of use cases to help you get started ASAP.&#x20;

## Calculate

The main whole life carbon calculation endpoint.&#x20;

{% swagger src=".gitbook/assets/openapi.json" path="/api/calculate" method="post" %}
[openapi.json](.gitbook/assets/openapi.json)
{% endswagger %}

## Token Data

Get data on your auth token, such as how many calls you've made to date and in the last tracking period.

{% swagger src=".gitbook/assets/openapi.json" path="/api/tokens/token-data" method="get" %}
[openapi.json](.gitbook/assets/openapi.json)
{% endswagger %}

## Payload

Parse your partial payload through the ingress schema. This endpoint is here to help troubleshoot errors related to formatting or schema parsing.&#x20;

{% swagger src=".gitbook/assets/openapi.json" path="/api/payload" method="post" %}
[openapi.json](.gitbook/assets/openapi.json)
{% endswagger %}

## Carbon Intensities

[Documentation of our Carbon Intensities endpoint](readme/reference-data.md#reference-data-via-api) is available in this documentation under reference data.&#x20;
