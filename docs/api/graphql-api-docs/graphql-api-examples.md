# GraphQL API Examples

Here are simple query examples for assets, zones, categories, and locations using GraphQL and REST API metadataFetch.

## 1. Assets:

```bash
curl --location 'https://api.wiliot.com/v1/traceability/owner/607737204301/metadataFetch' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--header 'X-REQUEST-TYPE: GraphQL' \
--header 'Content-Type: application/json' \
--data '{
    "query": "{ assetFilter(pageSize: 2) { page { id name } pageInfo { cursor hasNext totalPages } } }"
}'

```

## 2. Zones:

```bash
curl --location 'https://api.wiliot.com/v1/traceability/owner/607737204301/metadataFetch' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--header 'X-REQUEST-TYPE: GraphQL' \
--header 'Content-Type: application/json' \
--data '{
    "query": "{ zoneFilter(pageSize: 2) { page { id name } pageInfo { cursor hasNext totalPages } } }"
}'
```

## 3. Categories:

```bash
curl --location 'https://api.wiliot.com/v1/traceability/owner/607737204301/metadataFetch' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--header 'X-REQUEST-TYPE: GraphQL' \
--header 'Content-Type: application/json' \
--data '{
    "query": "{ categoryFilter(pageSize: 2) { page { id name } pageInfo { cursor hasNext totalPages } } }"
}'
```

## 4. Locations:

```bash
curl --location 'https://api.wiliot.com/v1/traceability/owner/607737204301/metadataFetch' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--header 'X-REQUEST-TYPE: GraphQL' \
--header 'Content-Type: application/json' \
--data '{
    "query": "{ locationFilter(pageSize: 2) { page { id name } pageInfo { cursor hasNext totalPages } } }"
}'
```