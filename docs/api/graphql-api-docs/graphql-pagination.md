# GraphQL Pagination

Pagination in GraphQL APIs is achieved using cursor-based pagination. The cursor represents a specific point in the dataset, and is used to fetch a portion of the data defined by the page size. The pageInfo object in the response provides details about the current page, the next cursor, and the total number of pages.

Here's a step-by-step example of how pagination works for assets using GraphQL API:

1. Start by fetching the first page of assets with a specified pageSize (e.g., 10). Don't provide a cursor in the first query.

```graphql
query {
  assets(pageSize: 10) {
    page {
      id
      name
      location {
        id
        name
      }
      category {
        id
        name
      }
      temperature
      connectivity
    }
    pageInfo {
      cursor
      hasNext
      totalPages
    }
  }
}
```

2. Check the pageInfo object in the response. If hasNext is true, there are more pages available. Note down the cursor value and totalPages.

3. Use the cursor value from the previous response to fetch the next page.
 
```graphql
query {
  assets(cursor: "CURSOR_VALUE_FROM_PREVIOUS_RESPONSE", pageSize: 10) {
    page {
      id
      name
      location {
        id
        name
      }
      category {
        id
        name
      }
      temperature
      connectivity
    }
    pageInfo {
      cursor
      hasNext
      totalPages
    }
  }
}
```

4. Repeat step 2 and 3 until hasNext is false.