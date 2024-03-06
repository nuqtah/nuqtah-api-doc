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
