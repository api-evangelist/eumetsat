---
name: eumetsat-search-and-download-products
description: Find EUMETSAT Data Store products in a collection with OpenSearch, inspect them, and download the product, a single entry file or its metadata.
api: EUMETSAT Data Store
generated: 2026-10-18
method: generated
operations:
  - getCollections
  - getCollectionByID
  - descriptionDocument
  - searchProducts
  - getProductByID
  - downloadProductsMetadataByID
  - downloadProductByID
  - downloadProductFileByID
---
# Search and download EUMETSAT Data Store products

Specs: `openapi/eumetsat-data-store-browse-openapi.yml`, `openapi/eumetsat-data-store-search-openapi.yml`, `openapi/eumetsat-data-store-download-openapi.yml`.
Auth: OAuth2 security scheme on the EUMETSAT API gateway (`https://api.eumetsat.int`). Send the bearer token on each call.

1. **List collections**: `getCollections` (Browse API `GET /collections`). Pick a collection ID (`collID`).
2. **Inspect a collection**: `getCollectionByID` (`GET /collections/{collID}`).
3. **Learn the search parameters**: `descriptionDocument` (Search API `GET /osdd`) returns the OpenSearch description document.
4. **Search**: `searchProducts` (`GET /os`) with the collection and the time/space filters taken from the description document. Page through the results.
5. **Inspect a product**: `getProductByID` (`GET /collections/{collID}/products/{prodID}`).
6. **Fetch metadata first**: `downloadProductsMetadataByID` (`GET /collections/{collID}/products/{prodID}/metadata`).
7. **Download**: use `downloadProductByID` for the whole product, or `downloadProductFileByID` (`/entry`) for one file in it.

Rules: every call here is a read (GET), so retrying is safe. Products can be large, so stream the downloads to disk.
