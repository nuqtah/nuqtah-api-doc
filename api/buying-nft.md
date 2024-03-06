---
description: For buying NFTs / GIfting to users
---

# Buying NFT

This endpoint handles all the logic of buying NFTs or gifting it to users. It handles creation and minting on the blockchain with appropriate metadata and all other nuanced operations.



### Request

Request method: HTTP

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

"toEmail" please provide here your customer's email who will get NFT
