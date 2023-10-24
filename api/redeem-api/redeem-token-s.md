---
description: How to redeem NFT(s)/Token(s) of one of your users
---

# Redeem Token(s)

This endpoint will enable you to redeem the NFTs/Tokens you have issued for your user.

Simply just add an array of NFT IDs to the request with your API key.

Once more, Its your responsibility _<mark style="color:red;">**to authenticate your user's email on your side before you send it to Nuqtah's API**</mark>_. Otherwise, if users hijack the request from the client (frontend) and was somehow able to send a different user email, they could potentially get/redeem other user's nfts that you have issued to them.

<mark style="color:red;">**Please save apiKey**</mark> <mark style="color:red;">**in BackEnd so it is not visible from Developer Tools.**</mark>



{% swagger method="post" path="/nfts/redeem" baseUrl="https://api.itsnuqtah.com/v1" summary="Redeem online tokens of users" %}
{% swagger-description %}
This endpoint will redeem the token(s) of the user you provide the email to.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization " required="true" %}
apiKey ${NUQTAH\_API\_KEY}
{% endswagger-parameter %}

{% swagger-parameter in="body" name="nftIDs" required="true" %}
Array of strings containing the nftIDs \[" ID\_1 ", ID\_2 ",...]
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Expand View" %}
```
// 
{
    "message": "nft redeemed",
    "nft": {
            "id": "xsbBmmp5lhq8TNDnsJpa",
            "updatedAt": "2023-10-17T10:39:26.08836Z",
            "createdAt": "2023-10-09T14:50:29.523834Z",
            "network": "MATIC",
            "contractAddress": "0x8A2d6670F0aa700573b63c1997eC42fBd7414e9B",
            "tokenID": "5841506696755060887",
            "mintTx": "0x5e07531e73d51ccb659e9e660ee821a4a10f62c0743f47861b48b9af340331b3",
            "mintedAt": "2023-10-09T14:51:13.125752Z",
            "isMinted": true,
            "ownerAddress": "0x9e52F9b6e5598DC91F3175C8D7f75035f466FaA2",
            "name":"NFT NAME",
            "description": "NFT Description",
            "image": "https://imagedelivery.net/MZAYIl9e1rxrwu_5UaRBFw/bebb00c7-0abb-4f21-7006-1b13454ea800/public",
            "imageFull": "https://firebasestorage.googleapis.com/v0/b/nuqtah-dev.appspot.com/o/nfts%2FxsbBmmp5lhq8TNDnsJpd%2Fimage.jpg?alt=media",
            "originalID": "eZNeuaj4keLvKzYSpnguh",
            "expiresAt": "1970-01-01T00:00:00Z", // means it never expires
            "tokenType": "redeemable",
            "redeemDescription": "", // set this from Nuqtah console
            "redeemURL": "http://localhost:3001", // set your website URL
            "redeemType": "online", 
            "discountValue": "VANILLA_ICE", // You can set this value however 
            // you like and use it to deteremine the discount logic 
            // you wanna handle on our website
            "numRedeemed": 10,
            "maxRedeemed": 10,
            "isRedeemable": false
        },
        "discountValue":"VANILLA_ICE"

}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="No NFT IDs provided" %}

{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Token(s) not found!" %}

{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Token(s) does not belong to this user" %}

{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="One of the nfts is already redeemed!" %}

{% endswagger-response %}
{% endswagger %}
