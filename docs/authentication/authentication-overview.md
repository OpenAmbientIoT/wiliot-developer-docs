Authentication Overview
=======================

Wiliot's API uses API key-based authentication to ensure secure and authorized access to its services.

API Key Authentication
----------------------

API key authentication involves sending an API key with each request to the server. An API key is a unique identifier that is generated for each developer who registers with Wiliot. It is a secure token that allows access to specific APIs and resources within the Wiliot ecosystem.

API keys can be obtained by registering for a developer account on the [Wiliot Developer Portal](https://developer.wiliot.com/). Once you have a developer account, you can create and manage API keys for each application you build using Wiliot's APIs.

Obtaining an Access Token
-------------------------

To obtain an access token, send a `POST` request to the Wiliot API's token authentication endpoint at `https://api.wiliot.com/v1/auth/token/api`. Include your API key in the `Authorization` header of the request.

Here's an example cURL command for generating an access token:

```shell
curl --request POST \
--url https://api.wiliot.com/v1/auth/token/api \
--header 'Accept: application/json' \
--header 'Authorization: MY_API_KEY' \
--header 'Content-Type: application/json' \
````

Replace `MY_API_KEY` with your actual API key value.

When the server receives this request, it will generate and return an access token that can be used to authenticate subsequent requests to the Wiliot API.

The response will be in JSON format and will look something like this:

```json
{
    "access_token": "<access_token>",
    "expires_in": 1799,
    "scope": "target-entity:<target_entity_id>",
    "token_type": "Bearer"
}
```

Replace `<access_token>` with the actual value of the access token.

Using the Access Token
----------------------

To use the access token, include it in the `Authorization` header of each subsequent API request. Set the value of the `Authorization` header to `Bearer ACCESS_TOKEN`, where `ACCESS_TOKEN` is the actual value of the access token generated in the previous step.

For example, to retrieve a list of locations from the Wiliot API using cURL, include the access token in the `Authorization` header of the request:


```shell
curl --request GET \
--url https://api.wiliot.com/v1/traceability/owner/{OWNERID}/location \
--header 'Accept: application/json' \
--header 'Authorization: Bearer {ACCESS_TOKEN}'
```

Replace `ACCESS_TOKEN` with the actual value of your access token.

Best Practices for API Key Authentication
-----------------------------------------

To ensure the security of your API key, follow these best practices:

-   Do not share your API key with others
-   Do not include your API key in client-side code, such as JavaScript or mobile applications
-   Regenerate your API key if you suspect it has been compromised
-   Use a secure storage mechanism for your API key, such as environment variables or a secure key vault
