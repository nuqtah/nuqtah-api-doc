---
description: How to retrieve the tokens/NFTs of one of your user
---

# Retrieve User Tokens

This function can return all nfts. It has optional params and optional pagination as well.\
For the RedeemAPI you must have "email" and "type" = "online" params set with the request to be able to retrieve tokens that relate to your end user. \
\
Its your responsibility _<mark style="color:red;">**to authenticate your user's email on your side before you send it to the API**</mark>_. Otherwise, if users hijack the request from the client (frontend) and send a different user email, they could potentially get/redeem other user's nfts that you have issued to them.

<mark style="color:red;">**Please save apiKey**</mark> <mark style="color:red;">**in BackEnd so it is not visible from Developer Tools.**</mark>

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
online
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

{% swagger-response status="500: Internal Server Error" description="wrong nft id from "after" query param" %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="error getting user email not found" %}

{% endswagger-response %}

{% swagger-response status="200: OK" description="Expand View" %}
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
        },{// Another NFT Object }
    ]
}
</code></pre>
{% endswagger-response %}
{% endswagger %}
