---
name: Unity Bank product reference lookup
description: Retrieve and inspect Unity Bank's openly-offered banking products (deposit, transaction, credit-card, loan) via the public, unauthenticated CDR Product Reference Data API.
api: openapi/unity-bank-cds-banking-products-openapi.yml
operations: [listBankingProducts, getBankingProductDetail]
method: generated
generated: '2026-07-20'
---

# Unity Bank product reference lookup

Unity Bank exposes a **public, unauthenticated** Consumer Data Right (CDR) Product
Reference Data API. Use it to list the bank's currently offered products and pull
full detail (features, fees, rates, eligibility, terms links) for any one product.

## Base

- Base URL: `https://ibank.gcmutualbank.com.au/openbanking/cds-au/v1`
- Auth: **none** — do not send credentials.
- Required header on every call: `x-v` (payload version). Supported live: `4` and `5`
  for the product list; send `x-v: 5`. Optionally send `x-min-v` for a floor.
- If the version is unsupported the API returns **406** with CDS error code
  `urn:au-cds:error:cds-all:Header/UnsupportedVersion`.

## Steps

1. **List products** — call `listBankingProducts`:
   `GET /banking/products` with header `x-v: 5`.
   - Optional filters: `effective` (`CURRENT` default | `FUTURE` | `ALL`),
     `updated-since` (ISO date-time), `brand`, `product-category`.
   - Paginate with `page` (default 1) and `page-size` (default 25). Read
     `meta.totalRecords` / `meta.totalPages` and follow `links.next` until exhausted.
   - Results are ordered by `lastUpdated` descending.
2. **Get product detail** — for a `productId` from the list, call
   `getBankingProductDetail`: `GET /banking/products/{productId}` with header `x-v: 5`.
   - Inspect embedded arrays: `features`, `constraints`, `eligibility`, `fees`,
     `depositRates`, `lendingRates`, plus `additionalInformation` URIs to the
     hosted terms/eligibility/fees pages.
   - A missing or no-longer-effective product returns **404**
     (`urn:au-cds:error:cds-all:Resource/NotFound`).

## Rules

- Read-only surface: there is **no idempotency key** and no write operations.
- To detect changes cheaply, poll `listBankingProducts` with `updated-since` set to
  your last successful poll time rather than re-pulling the whole catalog.
- Optionally send `x-fapi-interaction-id` (RFC 4122 UUID); the holder echoes it back
  for request correlation.
- Errors arrive as `{ "errors": [ { "code": "<CDS URN>", "title", "detail" } ] }` —
  see `errors/unity-bank-problem-types.yml`. Conventions: `conventions/unity-bank-conventions.yml`.
