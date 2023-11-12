---
description: Creating/Deploying a collection on the blockchain
---

# POST Collection

This function creates a collection then mints it to the blockchain. If the request has a wallet address it mints it to that, if not then it mints it to Nuqtah's Internal wallet.





{% swagger method="post" path="/collections/" baseUrl="https://api.itsnuqtah.com/v1" summary="Creates a collection and mints it to the blockchain" %}
{% swagger-description %}
Just like Post NFT, this function accepts a multipart form data object.

It accepts the "json" part and three image files:\
&#x20;"image", "imageHeader" & "imageHeader" for the three images that get displayed on the nuqtah website
{% endswagger-description %}

{% swagger-parameter in="header" name="Bearer Token" required="true" %}
Auth token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Name" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="Network" required="true" type="Enum" %}
Supported Networks atm:\
"ETH" | "MATIC" | "GO"
{% endswagger-parameter %}

{% swagger-parameter in="body" name="contractAddress" %}
Wallet address to mint contract to, if this is empty it will mint to Nuqtah's internal wallet
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Description" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="image" type="image/file" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="imageHeader" type="image/file" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" type="image/file" name="imageFeatured" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="royalty" type="String" %}
Percentage of sales that go to the creator
{% endswagger-parameter %}

{% swagger-parameter in="body" name="categories" type="Enum" %}
can have more than one:\
"art" | "collectibles" | "music" | "photography" | "sport" | "utility" | 'metaverse"
{% endswagger-parameter %}

{% swagger-parameter in="body" name="visibility" type="Enum" %}
Collection visibilty on Nuqtah's Marketplace:\
"public" | "unlisted" | "private"&#x20;
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Expand View" %}
```json
{
  "collection": {
    "timestamps": [
      "2023-11-12 14:22:56.942320397 +0200 EET m=+15.983997125",
      "2023-11-12 14:22:56.942320079 +0200 EET m=+15.983996823"
    ],
    "pointers": "0xc003854cc0",
    "identifiers": {
      "id1": "Gd1yt1Pu1bC7t6DGYWD9",
      "id2": "41aJNPz5tEQoTFtlSzQ4Ddq0Xmy2"
    },
    "maps": {
      "map1": {},
      "map2": {},
      "map3": {
        "primaryColor": "#cf2555",
        "secondaryColor": "#dd3332"
      }
    },
    "collections": {
      "type": "ERC721",
      "name": "ASDD asddsasafasfasfa",
      "description": "asfasfasfasfasfasfasfasf",
      "imageURL": "https://firebasestorage.googleapis.com/v0/b/nuqtah-dev.appspot.com/o/collections%2FUxDBOU4Pf2gK_UJIs6Gha%2Fimage.jpg?alt=media",
      "headerImageURL": "https://firebasestorage.googleapis.com/v0/b/nuqtah-dev.appspot.com/o/collections%2FUxDBOU4Pf2gK_UJIs6Gha%2FimageHeader.jpg?alt=media",
      "featuredImageURL": "https://firebasestorage.googleapis.com/v0/b/nuqtah-dev.appspot.com/o/collections%2FUxDBOU4Pf2gK_UJIs6Gha%2FimageFeatured.jpg?alt=media",
      "quantity": 5,
      "remaining": 5,
      "platform": "MATIC",
      "visibility": "public",
      "isApproved": false,
      "attributes": [],
      "tags": []
    }
  }
}

```
{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="No auth token provided" %}

{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Empty body " %}
```

{
    "error": {
        "message": "Invalid json: EOF",
        "status": 500
    }
}
```
{% endswagger-response %}
{% endswagger %}
