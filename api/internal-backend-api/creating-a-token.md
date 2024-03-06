# Creating a Token

This function is a monolith that gets used in a few places in our app to create an NFT/Token.

It is very flexible in terms of input meaning depending on the data send in its body it will accept it and create the NFT/Token accordingly.

Lets jump in!



{% swagger method="post" path="/nfts" baseUrl="https://api.itsnuqtah.com/v1" summary="Creates an NFT on the DB, it doesn't get minted here yet" %}
{% swagger-description %}
The form data has 2 parts:\
\- Json part which is data represeted as such {"nft":{"name":"blabla", "description":"desc" \}} etc..\
\- The media part which can be image,audio or video as "image"&#x20;
{% endswagger-description %}

{% swagger-parameter in="header" type="${Token}" name="Bearer Token" required="true" %}
Authorization token
{% endswagger-parameter %}

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

{% swagger-parameter in="body" name="visibilty" type="Enum" %}
Visibilty status on marketplace,i.e "forSale","notForSale",etc..
{% endswagger-parameter %}

{% swagger-parameter in="body" name="expiresAt" type="timestamp" %}
For redeemable NFTs, expectes a date-time timestamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="tokenType" type="Enum" %}
"template" | "normal" | "redeemable". There are backend checks to validate this, but the best practice would be to set this via the FE as well, needed for search and retrieval and other BE operations
{% endswagger-parameter %}

{% swagger-parameter in="body" name="redeemType" type="Enum" %}
"online" | "offlineRedeem"\
If this nft is redeemable, setting this value tags the nfts for retriveal sort and other backend operations. Important
{% endswagger-parameter %}

{% swagger-parameter in="body" name="discountValue" %}
For an online redeemable, this is value is decided by the merchant and can use it to handle discount logic on his own website. ex. "20%" or "Free item"
{% endswagger-parameter %}

{% swagger-parameter in="body" name="redeemDescription" type="String" %}
Additonal Desc for redeeemable NFTs
{% endswagger-parameter %}

{% swagger-parameter in="body" name="redeemURL" type="String" %}
For online redeemable NFT, external website url which user can go and redeem NFT there.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="maxRedeemed" type="Int" %}
Max amount of times this NFT can be redeemed. If you create more copies of this NFTs each child gets the same number defined here
{% endswagger-parameter %}

{% swagger-parameter in="body" name="copiesMax" type="Int" %}
Number of copies/children you can send to users of this NFT
{% endswagger-parameter %}

{% swagger-parameter in="body" name="price" type="Int" %}
NFT price on marketplace
{% endswagger-parameter %}

{% swagger-parameter in="body" name="categories" type="String Array" %}
Add attributes to marketplace NFT
{% endswagger-parameter %}

{% swagger-parameter in="body" name="royalty" type="Int" %}
Royalty percentage on the NFT
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="Enum" %}
example "image/png" | "audio/mp4"
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
