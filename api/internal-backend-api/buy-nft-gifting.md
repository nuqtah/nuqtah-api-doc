---
description: For buying NFTs / GIfting to users
---

# Buy NFT (Gifting)

This endpoint handles all the logic of buying NFTs or gifting it to users. It handles creation and minting on the blockchain with appropriate metadata and all other nuanced operations.



{% swagger method="get" path="/buy" baseUrl="http://localhost:8080/v1/nfts/${NFT_ID}" summary="Handles logic of buying or gifting an NFT/Digital token. " %}
{% swagger-description %}
To ping this endpoint you must be an authorized user. You must have an active subscription on the Nuqtah platform in the case of gifting.
{% endswagger-description %}

{% swagger-parameter in="header" name="Bearer Token" required="true" %}
${AUTH\_TOKEN}
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="purchase" type="JSON" %}
(FOR GIFTING/CLAIMING) Contains the purchase object.

You can use either "toEmail" or "claimCode".\
\`\`\`\
purchase:{ "toEmail":${RECIEPIENT\_EMAIL},\
"claimCode":${CODE\_GENERATED\_FROM\_NUQTAH\_WEBSITE},

"symbol":"MATIC || ETH || GO"

}

\`\`\`
{% endswagger-parameter %}

{% swagger-parameter in="path" name="nftID" required="true" %}
ID of the NFT
{% endswagger-parameter %}

{% swagger-parameter in="body" name="purchase" type="JSON" %}
( FOR MARKETPLACE BUYING)

Some metamask actions are triggered via Nuqtah's frontend. Probably would need that alongside this.



"claimCode" is optional.\
\
purchase: {

"symbol":"MATIC || ETH || GO",

"to":${RECIPEINT\_WALLET\_ADDRESS},\
"operation":"PURCHASING"

"claimCode":"${CODE\_GENERATED\_FROM\_NUQTAH\_WEBSITE},"

}
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Expand View" %}
```json
// Success! now the NFT is created and minted on the blockchain
// This is purchase information created on Nuqtah's DB
{
    "purchase": {
        "updatedAt": "2023-11-07T15:53:44.216307928+02:00",
        "createdAt": "2023-11-07T15:53:44.216307872+02:00",
        "id": "0O9qtOCInQBVhNhMbEPl",
        "userID": "41aJNPz5tEQoTFtlSzQ4Ddq0Xmy2",
        "to": "0x1305dA077eF4b499843e805C41eD820Aa04B52bD",
        "toEmail": "moatef@itsnuqtah.com",
        "nftID": "vaoUOtPnC7yWPlnu_rXFK",
        "sellerID": "41aJNPz5tEQoTFtlSzQ4Ddq0Xmy2",
        "price": "0",
        "symbol": "MATIC",
        "amountReceived": "0",
        "depositAddress": "",
        "checkUntil": "2023-11-07T16:53:44.216306225+02:00",
        "gasTx": "",
        "transferTx": "",
        "sellerAmount": "0",
        "sellerTx": "",
        "royaltyAmount": "0",
        "royaltyTx": "",
        "feeAmount": "0",
        "feeTx": "",
        "status": "paymentReceived",
        "status2": "transferring",
        "message": "",
        "claimCode": "",
        "operation": ""
    }
}

```
{% endswagger-response %}

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

{% swagger-response status="500: Internal Server Error" description="No or wrong chain/payment token symbol" %}
```json
  "error": {
        "message": "Unsupported payment token: ",
        "status": 500
    }
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Wrong Claim code" %}
```json

"error": {
        "message": "You cant claim the NFT",
        "status": 403
    }

```
{% endswagger-response %}
{% endswagger %}

