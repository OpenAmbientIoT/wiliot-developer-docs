Pixels API
----------

Wiliot's Pixels API allows developers to manage and retrieve data from IoT Pixels, which are small wireless sensors that can be attached to objects to provide real-time data about their location, temperature, and other environmental conditions.

### Endpoint List:

-   `GET /v1/owner/{ownerId}/tag`: Retrieves a list of tags associated with a specific owner.

Label API
---------

The Label API allows developers to manage and retrieve data related to labels, which are used to categorize and organize data associated with assets.

### Endpoint List:

-   `POST /v1/traceability/owner/{ownerId}/project/{projectId}/asset/{assetId}/label`: Creates a new label for an asset.
-   `DELETE /v1/traceability/owner/{ownerId}/project/{projectId}/asset/{assetId}/label`: Deletes all labels associated with an asset.
-   `GET /v1/traceability/owner/{ownerId}/project/{projectId}/asset/{assetId}/label`: Retrieves all labels associated with an asset.
-   `POST /v1/traceability/owner/{ownerId}/project/{projectId}/asset/label/{label}`: Renames a label.
-   `DELETE /v1/traceability/owner/{ownerId}/project/{projectId}/asset/{assetId}/label/{label}`: Deletes a specific asset label.

Asset Label API
---------------

The Asset Label API allows developers to manage and retrieve data related to asset labels, which are used to categorize and organize data associated with assets.

### Endpoint List:

-   `POST /v1/traceability/owner/{ownerId}/project/{projectId}/asset/{assetId}/label`: Creates a new label for an asset.
-   `DELETE /v1/traceability/owner/{ownerId}/project/{projectId}/asset/{assetId}/label`: Deletes all labels associated with an asset.
-   `GET /v1/traceability/owner/{ownerId}/project/{projectId}/asset/{assetId}/label`: Retrieves all labels associated with an asset.
-   `POST /v1/traceability/owner/{ownerId}/project/{projectId}/asset/label/{label}`: Renames a label.
-   `DELETE /v1/traceability/owner/{ownerId}/project/{projectId}/asset/{assetId}/label/{label}`: Deletes a specific asset label.

Asset API
---------

The Asset API allows developers to manage and retrieve data related to assets, which are objects that are being monitored by IoT Pixels.

### Endpoint List:

-   `POST /v2/traceability/owner/{ownerId}/asset`: Creates a new asset.
-   `GET /v2/traceability/owner/{ownerId}/asset`: Retrieves a list of all assets.
-   `DELETE /v2/traceability/owner/{ownerId}/asset/{assetId}`: Deletes a specific asset.
-   `PUT /v2/traceability/owner/{ownerId}/asset/{assetId}`: Updates an existing asset.
-   `GET /v2/traceability/owner/{ownerId}/asset/{assetId}`: Retrieves data for a specific asset.
-   `POST /v1/traceability/owner/{ownerId}/asset/{assetId}/tag/{tagId}`: Associates a tag with an asset.
-   `DELETE /v1/traceability/owner/{ownerId}/asset/{assetId}/tag/{tagId}`: Dissociates a tag from an asset.


Zone
----

Zones are areas defined within a location where assets can be assigned. In the Wiliot API, you can create, update, and delete zones as needed.

### Endpoint List:

-   `POST /v1/traceability/owner/{ownerId}/location/{locationId}/zone`: Create a new zone within a location.
-   `GET /v1/traceability/owner/{ownerId}/location/{locationId}/zone`: Get a list of all zones within a location.
-   `GET /v1/traceability/owner/{ownerId}/location/{locationId}/zone/{zoneId}`: Get details for a specific zone within a location.
-   `PUT /v1/traceability/owner/{ownerId}/location/{locationId}/zone/{zoneId}`: Update a specific zone within a location.
-   `DELETE /v1/traceability/owner/{ownerId}/location/{locationId}/zone/{zoneId}`: Delete a specific zone within a location.


Category API
------------
The Category API allows users to manage categories, which are used to classify assets. Categories can be created, retrieved, updated, and deleted using this API.

-   `POST /v1/traceability/owner/{ownerId}/category`: Creates a new category
-   `GET /v1/traceability/owner/{ownerId}/category`: Retrieves all categories
-   `DELETE /v1/traceability/owner/{ownerId}/category/{categoryId}`: Deletes a category
-   `PUT /v1/traceability/owner/{ownerId}/category/{categoryId}`: Updates an existing category
-   `GET /v1/traceability/owner/{ownerId}/category/{categoryId}`: Retrieves a category by its ID


Association
-----------

The Association API enables users to create and manage associations between assets, zones, and locations within the Wiliot ecosystem. It includes the following endpoints:

-   `POST /v1/traceability/owner/{ownerId}/location/{locationId}/association`: Create a new association for a location
-   `DELETE /v1/traceability/owner/{ownerId}/location/{locationId}/association`: Delete all associations of a location
-   `GET /v1/traceability/owner/{ownerId}/location/{locationId}/association`: Get all associations by location ID
-   `DELETE /v1/traceability/owner/{ownerId}/location/{locationId}/association/{associationValue}`: Delete a location association by association value
-   `POST /v1/traceability/owner/{ownerId}/location/{locationId}/zone/{zoneId}/association`: Create a new association for a zone
-   `DELETE /v1/traceability/owner/{ownerId}/location/{locationId}/zone/{zoneId}/association`: Delete all associations of a zone
-   `GET /v1/traceability/owner/{ownerId}/location/{locationId}/zone/{zoneId}/association`: Get all associations by zone ID
-   `DELETE /v1/traceability/owner/{ownerId}/location/{locationId}/zone/{zoneId}/association/{associationValue}`: Delete a zone association by association value


Location
--------

The Location API provides endpoints for creating, updating, and managing locations within the Wiliot ecosystem. It includes the following endpoints:

-   `POST /v1/traceability/owner/{ownerId}/location`: Create a new location
-   `GET /v1/traceability/owner/{ownerId}/location`: Get all locations
-   `DELETE /v1/traceability/owner/{ownerId}/location/{locationId}`: Delete a location
-   `PUT /v1/traceability/owner/{ownerId}/location/{locationId}`: Update an existing location
-   `GET /v1/traceability/owner/{ownerId}/location/{locationId}`: Get a location by ID

Asset Type
----------

The Asset Type API provides endpoints for retrieving asset types within the Wiliot ecosystem. It includes the following endpoint:

-   `GET /v1/traceability/owner/{ownerId}/asset-type`: Get all asset types

Metadata
--------

The Metadata API provides an endpoint for fetching metadata for a particular asset. It includes the following endpoint:

-   `POST /v1/traceability/owner/{ownerId}/metadataFetch`: Fetch metadata for a particular asset

Note: The Metadata API is currently in beta and subject to change.
