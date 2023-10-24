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
{
    "message": "nfts redeemed",
 
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
