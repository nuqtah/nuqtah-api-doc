---
description: For buying NFTs / GIfting to users
---

# Buying NFT

This endpoint handles all the logic of buying NFTs or gifting it to users. It handles creation and minting on the blockchain with appropriate metadata and all other nuanced operations.



### Request

Request method: POST

Endpoint: https://api.itsnuqtah.com/v1/nfts/**:id**/buy

Request headers:

* **Authorization**: "apiKey YOUR\_API\_KEY"

Request body:

```postman_json
{
    "purchase": {
        "symbol": "MATIC",
        "toEmail": "customer_email",
    }
}
```

Notes:

* https://api.itsnuqtah.com/v1/nfts/**:id**/buy. Please replace ":id" with your NFT ID.
* "toEmail" please provide here your customer's email who will get NFT



### Response

```
{
    "purchase": {
        "updatedAt": "2024-03-06T13:27:47.981655+05:00",
        "createdAt": "2024-03-06T13:27:47.981655+05:00",
        "id": "QIsm94fvotV8uTWqJIzf",
        "userID": "lv0mY9yK3Nf8SY9sprgaolwf7Dp1",
        "to": "0x962941beA3043c594d24E7d67140DCAA84E39330",
        "toEmail": "serik@itsnuqtah.com",
        "nftID": "dk4dLdI3vX1Eycf8SX9S9",
        "sellerID": "lv0mY9yK3Nf8SY9sprgaolwf7Dp1",
        "price": "0",
        "symbol": "MATIC",
        "amountReceived": "0",
        "depositAddress": "",
        "checkUntil": "2024-03-06T14:27:47.981653+05:00",
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

Success Response (201 Created)&#x20;

Status Code: 201&#x20;

Created Content-Type: application/json



**Error Responses**

* **400 Bad Request**: Invalid request body format or missing required fields.
* **401 Unauthorized**: Authentication credentials are missing or invalid.
* **403 Forbidden**: The user does not have permission to create a new user.
* **409 Conflict**: A user with the specified username or email already exists.
* **500 Internal Server Error**: An unexpected error occurred during user creation.
