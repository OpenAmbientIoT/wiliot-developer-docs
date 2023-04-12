# Introduction to GraphQL Query Usage in Fetch API

The Fetch API now supports GraphQL queries, providing a powerful and flexible way to fetch data related to assets, locations, zones, and categories. GraphQL is a query language for APIs that allows clients to request exactly the data they need, making it more efficient than traditional REST APIs. By utilizing GraphQL with the Fetch API, you can overcome the limitations and restrictions imposed by the REST API, such as the 500 record limit for fetching assets, locations, zones, or categories.

**Using GraphQL with the Fetch API allows you to:**

1.  Request only the fields you need, reducing the amount of data transferred and processed.
2.  Fetch multiple resources in a single request, reducing the number of API calls and improving performance.
3.  Improve the maintainability and scalability of your application by decoupling the data requirements from the API endpoints.

To use GraphQL with the Fetch API, you can send an HTTP request with the GraphQL query as the payload. Here's a sample `curl` command to fetch assets using a GraphQL query:


```shell
curl --location 'https://api.example.com/v1/traceability/owner/{:ownerId}/fetch'\
--header 'Authorization: Bearer <ACCESS TOKEN>'\
--header 'X-REQUEST-TYPE: GraphQL'\
--header 'Content-Type: application/json'\
--data '{
"query": "{ assets (pageSize : 2 ) { page { id name poiId } pageInfo {cursor hasNext totalPages} } }"
}'
```
> **GraphQL**
>is a query language for APIs developed by Facebook, designed to make it easy for clients to request and receive exactly the data they need. It allows clients to define the structure of the response, reducing over- or under-fetching of data. GraphQL is particularly useful for modern, data-driven applications that require flexibility and efficiency in fetching data from APIs.