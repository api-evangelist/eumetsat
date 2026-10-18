---
name: eumetsat-customise-products-with-data-tailor
description: Submit a Data Tailor (EPCS) customisation that reformats or subsets an EUMETSAT product, poll it until it finishes, download the outputs and clean up.
api: EUMETSAT Data Tailor Web Service (EPCS)
generated: 2026-10-18
method: generated
operations:
  - GET_info
  - GET_report_quota
  - GET_products
  - GET_chains
  - GET_formats
  - POST_customisations
  - GET_customisations-customisationId
  - GET_customisations-customisationId-log
  - GET_download
  - DELETE_customisations-customisationId
---
# Customise products with the EUMETSAT Data Tailor

Spec: `openapi/eumetsat-data-tailor-openapi.yml` (base `https://api.eumetsat.int/epcs/0.1.0`).

1. **Check the service and your quota**: call `GET_info`, then `GET_report_quota`. Stop if the quota is used up.
2. **Discover options**: `GET_products` (supported product types), `GET_formats` (output formats) and `GET_chains` (saved processing chains).
3. **Submit**: `POST_customisations` with the input product(s) and a chain.
4. **Poll**: `GET_customisations-customisationId` until the status is final. Read `GET_customisations-customisationId-log` if it failed.
5. **Download outputs**: `GET_download` with the output path the customisation reports.
6. **Clean up**: `DELETE_customisations-customisationId` frees quota.

Rules: `POST_customisations` is not idempotent, so a retry creates a second job. Before you resubmit, check `GET_customisations`.
