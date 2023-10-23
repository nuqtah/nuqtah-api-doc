---
description: How to retrieve the tokens/NFTs of one of your user
---

# Retrieve User Tokens

This function can return all nfts. It has optional params and optional pagination as well.\
For the RedeemAPI you must have "email" and "type" ="online" params set with the request to be able to retrieve tokens that relate to your end user. Its your responsiblity to authenticate&#x20;

{% swagger method="get" path="/nfts" baseUrl="https://api.itsnuqtah.com/v1" summary="Retrieve online redeemable user tokens " expanded="false" %}
{% swagger-description %}
This endpoint will return all tokens that are eligible for online redeeming for the email provided. Its your responsibility to provide an authenticated  email.&#x20;
{% endswagger-description %}

{% swagger-parameter in="query" name="email" required="true" %}
${USER\_EMAIL} \*REQUIRED for third party integration
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization " required="true" %}
apiKey ${NUQTAH\_API\_KEY}
{% endswagger-parameter %}

{% swagger-parameter in="query" name="type" required="true" %}
${NFT\_TYPE} \*REQUIRED for third party integration with value: "online"



Possible values: "template" | "normalOrRedeemable" | "normal" | "redeemable" | "minted" | "online"
{% endswagger-parameter %}

{% swagger-parameter in="query" name="creatorID" %}
${USER\_ID} gets all nfts that this user has created
{% endswagger-parameter %}

{% swagger-parameter in="query" name="userID" %}
${USER\_ID} gets all nfts that are owned by this user
{% endswagger-parameter %}

{% swagger-parameter in="query" name="search" %}
${NFT\_NAME}
{% endswagger-parameter %}

{% swagger-parameter in="query" name="after" %}
${NFT\_ID}
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="Int" %}
Number of nfts you want returned in the response
{% endswagger-parameter %}

{% swagger-parameter in="query" name="minPrice" type="Int" %}
Minimum price for an NFT ( if has  a price)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="maxPrice" type="Int" %}
Max price for an NFT ( if it has a price)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="collecionID" %}
${COLLECTION\_ID}
{% endswagger-parameter %}

{% swagger-response status="500: Internal Server Error" description="wrong nft id from "after" query param" %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="error getting user email not found" %}

{% endswagger-response %}

{% swagger-response status="200: OK" description="" %}
<pre class="language-json"><code class="lang-json"><strong>// Will respond with an array of nfts and a "last" property. 
</strong><strong>// This property returns the last id of the last nft in the response 
</strong><strong>// if you send a limit with the request.
</strong><strong>// This can be used in pagination by sending the param "after" = "NFT_ID"
</strong><strong>// Keep in mind these are all optional param
</strong><strong>{
</strong>    "last":"",
    nfts:[
  
{
            "id": "xsbBmmp5lhq8TNDnsJpd",
            "updatedAt": "2023-10-17T10:39:26.08836Z",
            "createdAt": "2023-10-09T14:50:29.523834Z",
            "userID": "rAKWjuZVxOOBlVjKP1ywJ6w9pVA2",
            "attributes": null,
            "cloudflare": {
                "id": "bebb00c7-0abb-4f21-7006-1b13454ea800",
                "status": "ready",
                "code": "",
                "message": "",
                "readyToStream": true
            },
            "creatorID": "41aJNPz5tEQoTFtlSzQ4Ddq0Xmy2",
            "collectionID": "universal-matic",
            "network": "MATIC",
            "contractAddress": "0x8A2d6670F0aa700573b63c1997eC42fBd7414e9B",
            "tokenID": "5841506696755060887",
            "mintTx": "0x5e07531e73d51ccb659e9e660ee821a4a10f62c0743f47861b48b9af340331b3",
            "mintedAt": "2023-10-09T14:51:13.125752Z",
            "isMinted": true,
            "tokenURI": "",
            "ownerAddress": "0x9e52F9b6e5598DC91F3175C8D7f75035f466FaA2",
            "linkedID": "",
            "status": "completed",
            "categories": null,
            "name": "yes yes yes",
            "description": "asdddddddddddddddddddddddddddddd",
            "image": "https://imagedelivery.net/MZAYIl9e1rxrwu_5UaRBFw/bebb00c7-0abb-4f21-7006-1b13454ea800/public",
            "imageFull": "https://firebasestorage.googleapis.com/v0/b/nuqtah-dev.appspot.com/o/nfts%2FxsbBmmp5lhq8TNDnsJpd%2Fimage.jpg?alt=media",
            "type": "",
            "preview": "",
            "mediaStatus": "ready",
            "price": "0",
            "priceSymbol": "",
            "royalty": "0",
            "symbol": "",
            "visibility": "public",
            "copiesMax": 0,
            "copiesNum": 0,
            "copyNum": 1,
            "originalID": "eZNeuaj4keLvKzYSpnguh",
            "numLikes": 0,
            "featured": false,
            "imported": false,
            "expiresAt": "1970-01-01T00:00:00Z",
            "user": {
                "id": "rAKWjuZVxOOBlVjKP1ywJ6w9pVA2",
                "updatedAt": "2023-10-09T13:12:03.887717Z",
                "createdAt": "2023-10-09T13:12:03.887717Z",
                "username": "",
                "usernameCanonical": "",
                "name": "Mo atef",
                "image": "",
                "email": "druidoftheclaw420+++@gmail.com",
                "bannerImage": "",
                "address": "0x9e52F9b6e5598DC91F3175C8D7f75035f466FaA2",
                "selfAddress": "",
                "description": "",
                "websiteURL": "",
                "location": "",
                "socials": null,
                "nonce": "",
                "signinMethod": "",
                "supportEmail": "",
                "didRequestVerification": false,
                "isCreator": true,
                "isVerified": false,
                "isTermsAccepted": false,
                "roles": null
            },
            "tokenType": "redeemable",
            "redeemDescription": "",
            "redeemURL": "http://localhost:3001",
            "redeemType": "online",
            "discountValue": "",
            "numRedeemed": 10,
            "maxRedeemed": 10,
            "isRedeemable": false
        },{// Another NFT Object}
    ]
}
</code></pre>
{% endswagger-response %}
{% endswagger %}
