API Overview
============

Wiliot's API allows developers to access and interact with the Wiliot ecosystem of IoT devices, sensors, and data. The API provides endpoints for querying device data, managing devices and sensors, and integrating with other third-party applications and services.

Base URL
--------

The base URL for all Wiliot API requests is:



> `https://api.wiliot.com/v1/`

All endpoints in the API are relative to this base URL.

Authentication
--------------

Wiliot's API uses API key-based authentication to ensure secure and authorized access to its services. To use the API, you will need to obtain an API key by registering for a developer account on the [Wiliot Developer Portal](https://developer.wiliot.com/). Once you have an API key, you can use it to authenticate all API requests by including it in the `Authorization` header.

For more information on API key authentication, see the [Authentication Overview](../authentication/authentication-overview.md)

Endpoints
---------

The Wiliot API provides the following endpoints:

-   Device Endpoints: These endpoints allow you to manage and interact with Wiliot IoT devices and sensors, including registering new devices, querying device data, and updating device settings.
-   Data Endpoints: These endpoints allow you to access and analyze data collected from Wiliot devices, including raw sensor data and aggregated analytics.
-   Integration Endpoints: These endpoints allow you to integrate Wiliot data and services with other third-party applications and services, such as cloud storage providers and data visualization tools.

For detailed information on each endpoint and its available methods, see the [API Reference](https://chat.openai.com/api-reference.md).

API Versions
------------

The current version of the Wiliot API is `v1`. The API is designed to be backwards-compatible, meaning that new features and functionality will be added over time without breaking existing integrations. However, if significant changes or updates are made to the API, a new version number will be introduced to ensure compatibility with existing integrations.

Developers should always use the latest available version of the API to take advantage of the newest features and bug fixes. However, if you are integrating with an older version of the API, you should refer to the corresponding version-specific documentation for accurate endpoint and parameter information.

Rate Limiting
-------------

To ensure the stability and performance of the Wiliot API, requests are subject to rate limiting. The current rate limit is 100 requests per minute per API key. If you exceed this limit, you will receive a `429 Too Many Requests` response code. To avoid rate limiting, ensure that your API usage is within reasonable limits and optimize your API requests for efficiency.