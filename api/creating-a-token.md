# Creating a Token

This function is a monolith that gets used in a few places in our app to create an NFT/Token.

It is very flexible in terms of input meaning depending on the data send in its body it will accept it and create the NFT/Token accordingly.

Lets jump in!



{% swagger method="post" path="/nfts" baseUrl="https://api.itsnuqtah.com/v1" summary="" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="collectionID" required="false" %}
Collection id that this NFT will belong to once minted. If this field is empty, it will  mint by default to Nuqtah's universal collection
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="String" required="true" %}
The name of the nft
{% endswagger-parameter %}

{% swagger-parameter in="body" name="image" type="File" required="true" %}
Image, audio or video file
{% endswagger-parameter %}

{% swagger-parameter in="body" name="description" type="String" required="true" %}
Description of the nft/token
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type=""multipart/form-data"" required="true" %}
Must be a form data part contains the data and part contains the media file
{% endswagger-parameter %}

{% swagger-parameter in="body" name="network" type="String" %}
Supported Networks atm:\
"ETH" | "MATIC" | "GO"
{% endswagger-parameter %}

{% swagger-parameter in="body" name="tokenType" type="Enum" %}
"template" | "normal" | "redeemable". There are backend checks to validate this, but the best practice would be to set this via the FE as well, needed for search and retrieval and other BE operations
{% endswagger-parameter %}

{% swagger-parameter in="body" name="copiesMax" type="Int" %}
Number of copies/children you can send to users of this NFT
{% endswagger-parameter %}

{% swagger-parameter in="body" name="price" type="Int" %}
NFT price on marketplace
{% endswagger-parameter %}

{% swagger-response status="201: Created" description="Returns the NFT object of the created NFT" %}
```json
// Some code
{"nft":{NFT_OBJECT}
}
```
{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="No Auth Token Provided" %}

{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="cannot verify token: ID token has expired at:" %}

{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="bad input EOF" %}

{% endswagger-response %}
{% endswagger %}

### &#x20;Sample Request

Request method: **POST**

Request headers:&#x20;

* **Authorization**: "apiKey YOUR\_API\_KEY"
* **Content-Type:** "multipart/form-data"

Request body:

```postman_json
{
    "json": {
        "nft": {
            "name": "Your token name",
            "description": "Some description for testing",
            "copiesMax": 1000,
            "network": "MATIC",
            "tokenType": "template",
            "attributes": [
                {
                    "trait_type": "Event name",
                    "value": "Leap"
                },
                {
                    "trait_type": "Year",
                    "value": "2024"
                }
            ]
        }
    },
    "image": "binary file"
}
```

**json**: This appears to be a nested object containing the information related to the NFT being created.

**nft**: This object contains details specific to the NFT.

* **copiesMax**: The maximum number of copies of this NFT that can exist, set to 1000 in this example.
* **network**: The blockchain network associated with this NFT, which is "MATIC" (Polygon) in this example.
* **tokenType**: The type of token, which is "template" in this example.
* **attributes**: An array containing additional attributes or traits associated with the NFT.
  * Each attribute object in the array contains a "trait\_type" and a "value".
  * In this example, there are two attributes: "Event name" with a value of "Leap", and "Year" with a value of "2024".

**image**: This appears to be a binary file representing the image associated with the NFT. It is likely the visual representation or artwork that corresponds to the NFT.

### &#x20;Response

\
The above request returns a newly created token with the provided data.&#x20;

```
{
    "nft": {
        "id": "Up6XSfOdbLlPDno9bXBt0",
        "updatedAt": "2024-03-06T12:45:27.806368+05:00",
        "createdAt": "2024-03-06T12:45:27.806368+05:00",
        "userID": "VUc1dhFMX8XeHTM23BQGbRPFHGN2",
        "attributes": [
            {
                "trait_type": "Event name",
                "display_type": "",
                "value": "Leap"
            },
            {
                "trait_type": "Year",
                "display_type": "",
                "value": "2024"
            }
        ],
        "logs": null,
        "cloudflare": {
            "id": "36aed7a3-4edf-48cd-7a89-91a2769b9000",
            "status": "ready",
            "code": "",
            "message": "",
            "readyToStream": true
        },
        "creatorID": "VUc1dhFMX8XeHTM23BQGbRPFHGN2",
        "collectionID": "universal-matic",
        "network": "MATIC",
        "contractAddress": "0x8A2d6670F0aa700573b63c1997eC42fBd7414e9B",
        "tokenID": "",
        "mintTx": "",
        "mintedAt": "0001-01-01T00:00:00Z",
        "isMinted": false,
        "tokenURI": "",
        "ownerAddress": "0x08132428682F41dc7E746809726FB8CCb851C5a3",
        "linkedID": "",
        "status": "",
        "categories": null,
        "name": "Your token name",
        "description": "Some description for testing",
        "image": "https://storage.googleapis.com/nuqtah-dev.appspot.com/nfts%2FUp6XSfOdbLlPDno9bXBt0%2Fimage.jpeg",
        "imageFull": "",
        "standard": "ERC721",
        "preview": "",
        "mediaStatus": "ready",
        "price": "0",
        "priceSymbol": "",
        "royalty": "0",
        "symbol": "",
        "visibility": "public",
        "copiesMax": 1000,
        "copiesNum": 0,
        "copyNum": 0,
        "originalID": "",
        "numLikes": 0,
        "featured": false,
        "imported": false,
        "expiresAt": "0001-01-01T00:00:00Z",
        "user": null,
        "type": "dgift",
        "tokenType": "template",
        "mediaType": "",
        "redeemDescription": "",
        "redeemURL": "",
        "redeemType": "",
        "discountValue": "",
        "numRedeemed": 0,
        "maxRedeemed": 0,
        "isRedeemable": false,
        "orgID": "u9JE2Uf898ofMn33khhl",
        "animationURL": "",
        "settings": null
    }
}
```
