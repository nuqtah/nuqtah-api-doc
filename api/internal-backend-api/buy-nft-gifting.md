---
description: For buying NFTs / GIfting to users
---

# Buy NFT (Gifting)

This endpoint handles all the logic of buying NFTs or gifting it to users. It handles creation and minting on the blockchain with appropriate metadata and all other nuanced operations.



{% swagger method="get" path="/buy" baseUrl="http://localhost:8080/v1/nfts/${NFT_ID}" summary="" %}
{% swagger-description %}
Handles logic of buying or gifting an NFT/Digital token. To ping this endpoint you must be an authorized user. You must have an active subscription on the Nuqtah platform in the case of gifting.
{% endswagger-description %}

{% swagger-parameter in="header" name="Bearer Token" required="true" %}
${AUTH\_TOKEN}
{% endswagger-parameter %}

{% swagger-parameter in="path" name="nftID" required="true" %}
ID of the NFT
{% endswagger-parameter %}

{% swagger-response status="403: Forbidden" description="Must be logged in" %}
```json
// Some code

  "error": {
        "message": "No auth token provided",
        "status": 403
    }

```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="NFT/Token not found" %}
```json
"error": {
        "message": "not found",
        "status": 404
    }
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="User not found" %}
```json
"error": {
        "message": "not found",
        "status": 404
    }

```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Invalid User ID" %}
```json
  "error": {
        "message": "Invalid json: EOF",
        "status": 500
    }

```
{% endswagger-response %}
{% endswagger %}

