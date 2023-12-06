---
description: Guideline how to send ERC-20 tokens directly to user
---

# Sending ERC-20 tokens directly

If your organization has no ERC-20 tokens please follow this [steps](create-erc-20-token.md) to create it.

## Send tokens Api

{% swagger method="post" path="/tokens/${tokenID}/claim" baseUrl="https://api.itsnuqtah.com/v1" summary="Using this endpoint you can send any amount of tokens without defining campaign" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization " required="true" %}
apiKey ${NUQTAH\_API\_KEY}
{% endswagger-parameter %}

{% swagger-parameter in="body" name="email" required="true" %}
email of account who will get reward
{% endswagger-parameter %}

{% swagger-parameter required="true" in="body" name="tokenAmount" %}
amount of tokens that gonna be sended
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
{ "data":&#x20;

&#x20;  {

&#x20;       "campaignReward":{\*reward object\*},&#x20;

&#x20;       "tx": \*transaction hash : String\*

&#x20;   }

&#x20;}
{% endswagger-response %}
{% endswagger %}
