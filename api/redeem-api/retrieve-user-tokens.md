---
description: How to retrieve the tokens/NFTs of one of your user
---

# Retrieve User Tokens

TODO: there are a lot of paramters that can be used here since this is using our original getNFT method (searching, filitering,etc..) we need to discuss which filters should we tell our users about and add them below to the endpoint doc

{% swagger method="get" path="/nfts" baseUrl="https://api.itsnuqtah.com/v1" summary="Retrieve online redeemable user tokens " expanded="false" %}
{% swagger-description %}
This endpoint will return all tokens that are eligible for online redeeming for the email provided. Its your responsibility to provide an authenticated  email.&#x20;
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization " required="true" %}
apiKey ${NUQTAH\_API\_KEY}
{% endswagger-parameter %}

{% swagger-parameter in="path" name="email" required="true" %}
${USER\_EMAIL}
{% endswagger-parameter %}

{% swagger-parameter in="path" name="type" required="true" %}
online
{% endswagger-parameter %}
{% endswagger %}
