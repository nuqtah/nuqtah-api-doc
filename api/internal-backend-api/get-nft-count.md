---
description: Returns the number of NFTs related to a certain user
---

# GET NFT Count

This endpoint returns the number of NFTs and it has an array of optional filters to tailor the count to a specific user you want, or just general count.



{% swagger method="get" path="" baseUrl="https://api.itsnuqtah.com/v1" summary="Returns count of NFTs" %}
{% swagger-description %}
Only for userID will the endpoint throw an error, for the rest will just return 0 NFTs. (might need to change that in the future)

So please make sure the other params passed are correct and test them.
{% endswagger-description %}

{% swagger-parameter in="path" name="userID" %}
Firebase ID of an NFT owner
{% endswagger-parameter %}

{% swagger-parameter in="path" name="creatorID" %}
Firebase ID of an NFT creator
{% endswagger-parameter %}

{% swagger-parameter in="path" name="collectionID" %}
Firebase ID of a collection
{% endswagger-parameter %}

{% swagger-parameter in="path" name="type" type="Enum" %}
"template" | "normalOrRedeemable" | "minted"\
\| "redeemable"
{% endswagger-parameter %}

{% swagger-parameter in="path" name="mintedAt" type="Timestamp/String" %}
combine this with type "minted" to get the count of NFTs minted at a certain timestamp. e.g. "2006-01-2T15:04"
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Returns nft count" %}
```json
// Some code

{
    "nftCount": 4610
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Wrong user ID " %}
```json

"error": {
        "message": "error getting user asd: not found",
        "status": 404
    }
```
{% endswagger-response %}
{% endswagger %}

