# GraphQL API Examples

Here are simple query examples for assets, zones, categories, and locations using GraphQL and REST API metadataFetch.

## 1. Assets:

```bash
curl --location 'https://api.wiliot.com/v1/traceability/owner/{:ownerID}/metadataFetch' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--header 'X-REQUEST-TYPE: GraphQL' \
--header 'Content-Type: application/json' \
--data '{
    "{
   "query": "{ assets (pageSize : 2 ) { page { id name poiId } pageInfo {cursor hasNext totalPages} } }"
}'
```

Response:

```json
{
    "data": {
        "assets": {
            "page": [
                {
                    "id": "sample_009aT0758",
                    "name": "sample_009aT0758",
                    "poiId": "66ad3e7d-a1de-4dce-bdf6-b4aecbbf08fe"
                },
                {
                    "id": "sample_009aT0756",
                    "name": "sample_009aT0756",
                    "poiId": "f5843751-ad86-4c25-bf4b-ec8a56a7d719"
                }
            ],
            "pageInfo": {
                "cursor": "MV9fU0VQX19zYW1wbGVfMDA5YVQwNzU4",
                "hasNext": true,
                "totalPages": 3
            }
        }
    }
}
```

## 2. Categories:

```bash
curl --location 'https://api.wiliot.com/v1/traceability/owner/{:ownerID}/metadataFetch' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--header 'X-REQUEST-TYPE: GraphQL' \
--header 'Content-Type: application/json' \
--data '{
    "query": "{ categories (pageSize : 2 ) { page { id name } pageInfo {cursor hasNext totalPages} } }"
}'
```

Response:

```json
{
    "data": {
        "categories": {
            "page": [
                {
                    "id": "loose",
                    "name": "Test Assets"
                },
                {
                    "id": "Default",
                    "name": "Default"
                }
            ],
            "pageInfo": {
                "cursor": "MV9fU0VQX19sb29zZQ==",
                "hasNext": true,
                "totalPages": 2
            }
        }
    }
}
```

## 3. Locations:

```bash
curl --location 'https://api.wiliot.com/v1/traceability/owner/{:ownerID}/metadataFetch' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--header 'X-REQUEST-TYPE: GraphQL' \
--header 'Content-Type: application/json' \
--data '{
    "query": "{ locations (pageSize : 2 ) { page { id name } pageInfo {cursor hasNext totalPages} } }"
}'
```

Response: 

```json
{
    "data": {
        "locations": {
            "page": [
                {
                    "id": "b95ceecd-1749-4396-a4a0-54525ce3ace8",
                    "name": "My Home"
                },
                {
                    "id": "a5d391d8-37cf-4998-896e-12eed51c4a20",
                    "name": "Neighbour-1"
                }
            ],
            "pageInfo": {
                "cursor": "MV9fU0VQX19iOTVjZWVjZC0xNzQ5LTQzOTYtYTRhMC01NDUyNWNlM2FjZTg=",
                "hasNext": true,
                "totalPages": 2
            }
        }
    }
}
```



## 4. Zones:

>>**Warning:** Zones are not supported in the REST API metadataFetch. Make sure to use Fetch API endpoint



```bash

curl --location 'https://api.wiliot.com/v1/traceability/owner/{:ownerID}/fetch' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--header 'X-REQUEST-TYPE: GraphQL' \
--header 'Content-Type: application/json' \
--data '{
    "query": "{ zones (pageSize : 2 ) { page { id name } pageInfo {cursor hasNext totalPages} } }"
}'

```

Response:

```json
{
    "data": {
        "zones": {
            "page": [
                {
                    "id": "f5843751-ad86-4c25-bf4b-ec8a56a7d719",
                    "name": "garage"
                },
                {
                    "id": "9bfdb4af-7d24-4590-9326-799c9b426dbe",
                    "name": "living room"
                }
            ],
            "pageInfo": {
                "cursor": "MV9fU0VQX19mNTg0Mzc1MS1hZDg2LTRjMjUtYmY0Yi1lYzhhNTZhN2Q3MTk=",
                "hasNext": false,
                "totalPages": 1
            }
        }
    }
}
```


## Using Flitering and Sorting

You can use filtering and sorting in GraphQL queries. For example, to get the first 2 assets sorted by creation date in ascending order, use the following query:

```bash
curl --location 'https://api.wiliot.com/v1/traceability/owner/{:ownerID}/metadataFetch' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--header 'X-REQUEST-TYPE: GraphQL' \
--header 'Content-Type: application/json' \
--data '{
    "{
    "query": "{ assets (pageSize : 2  orderBy: {field: \"createdAt\" direction: \"asc\" } )  { page { id name poiId } pageInfo {cursor hasNext totalPages} } }"
}
```



```bash
curl --location 'https://api.wiliot.com/v1/traceability/owner/{:ownerID}/metadataFetch' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--header 'X-REQUEST-TYPE: GraphQL' \
--header 'Content-Type: application/json' \
--data '{
    "{
    "query": "{ assets (pageSize : 10 orderBy: {field: \"createdAt\" direction: \"asc\"} categoryId: {equalTo: \"rdc-non-con\"}) { page { id name poiId createdAt categoryId } pageInfo {cursor hasNext totalPages} } }"
}
```