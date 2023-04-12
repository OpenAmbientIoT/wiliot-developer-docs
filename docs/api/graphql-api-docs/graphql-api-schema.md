# GraphQL Schema for Assets , Category , Zones and Locations

## Asset

```graphql
type Asset {
  id: ID
  name: String
  location: Location
  category: Category
  temperature: Float
  connectivity: Int
}
```
## Location

```graphql
type Location {
  id: ID
  name: String
  type: String
  zones: [Zone]
}
```

## Zone

```graphql

type Zone {
  id: ID
  name: String
  location: Location
}
```

## Category

```graphql

type Category {
  id: ID
  name: String
  type: String
}

```

## AssetPageInfo

```graphql
type AssetPageInfo {
  page: [Asset]
  pageInfo: PageInfo
}
```

## LocationPageInfo
    
```graphql
type LocationPageInfo {
  page: [Location]
  pageInfo: PageInfo
}
```

## ZonePageInfo

```graphql

type ZonePageInfo {
  page: [Zone]
  pageInfo: PageInfo
}
```

## CategoryPageInfo

```graphql
type CategoryPageInfo {
  page: [Category]
  pageInfo: PageInfo
}
```

## PageInfo

```graphql

type PageInfo {
  cursor: String
  hasNext: Boolean
}

``` 


## Schema Types

```graphql

type Asset {
  id: ID
  name: String
  location: Location
  category: Category
  temperature: Float
  connectivity: Int
}

type Location {
  id: ID
  name: String
  type: String
  zones: [Zone]
}

type Zone {
  id: ID
  name: String
  location: Location
}

type Category {
  id: ID
  name: String
  type: String
}

type AssetPageInfo {
  page: [Asset]
  pageInfo: PageInfo
}

type LocationPageInfo {
  page: [Location]
  pageInfo: PageInfo
}

type ZonePageInfo {
  page: [Zone]
  pageInfo: PageInfo
}

type CategoryPageInfo {
  page: [Category]
  pageInfo: PageInfo
}

type PageInfo {
  cursor: String
  hasNext: Boolean
}
```
