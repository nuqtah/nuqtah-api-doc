---
description: API KEY
---

# Before we start

Before using the application you should create ApiKey on the business console. An API key is a unique identifier used to authenticate and authorize access to an API. It serves as a token that grants access to specific resources or functionalities within the API.&#x20;

\
For every API request generated **ApiKey** should be included in the request header. Here is an example:\


```
HTTP Method: POST
Endpoint: https://api.itsnuqtah.com/v1/nfts
Request Headers: 
    Content-Type: application/json
    Authorization: apiKey YOUR_API_KEY
```
