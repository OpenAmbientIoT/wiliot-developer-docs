# GraphQL query usage

Here are simple queries for assets, locations, zones, and categories, along with how to use pagination for each:


## Assets

```graphql

query {
  assets(cursor: "CURSOR_VALUE", pageSize: 10) {
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

## Locations

```graphql

query {
  locations(cursor: "CURSOR_VALUE", pageSize: 10) {
    page {
      id
      name
      type
      zones {
        id
        name
      }
    }
    pageInfo {
      cursor
      hasNext
      totalPages
    }
  }
}


```

## Zones

```graphql
query {
  zones(cursor: "CURSOR_VALUE", pageSize: 10) {
    page {
      id
      name
      location {
        id
        name
      }
    }
    pageInfo {
      cursor
      hasNext
      totalPages
    }
  }
}

```

## Categories

```graphql
query {
  categories(cursor: "CURSOR_VALUE", pageSize: 10) {
    page {
      id
      name
      type
    }
    pageInfo {
      cursor
      hasNext
      totalPages
    }
  }
}
```

## Pagination

The `pageInfo` object contains the following fields:

- `cursor` - The cursor value to use in the next query.
- `hasNext` - A boolean value that indicates whether there are more pages to query.
- `totalPages` - The total number of pages.

Replace "CURSOR_VALUE" with the appropriate cursor value for each query. The pageSize argument determines the number of results per page. In these examples, it is set to 10.

The page field within each query contains the fields that can be retrieved for each entity:

For assets: id, name, location, category, temperature, and connectivity
For locations: id, name, type, and zones
For zones: id, name, and location
For categories: id, name, and type
The pageInfo field returns the cursor for the next page (if there is one) and whether there is a next page.
