# Unity Bank (unity-bank)

Unity Bank Limited (ABN 72 087 650 637, AFSL & Australian Credit Licence 238311, BSB 659 000) is an Australian member-owned mutual bank that consolidated the Unity Bank and Reliance Bank brands under a single Unity Bank identity. As an authorised deposit-taking institution (ADI) it offers transaction and savings accounts, term deposits, home loans, personal loans, credit cards, business banking, and wealth services to its members across Australia. Under the Australian Consumer Data Right (CDR / open banking), Unity Bank exposes a public, unauthenticated Product Reference Data (PRD) API conforming to the DSB Consumer Data Standards.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/unity-bank/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/unity-bank/refs/heads/main/apis.yml)

## Tags

- Financial
- Banks
- Open Banking
- CDR
- Consumer Data Right
- Consumer Banking
- Australia
- Mutual Bank
- Product Reference Data

## Timestamps

- **Created:** 2026-07-20
- **Modified:** 2026-07-20

## APIs

### Unity Bank CDR Product Reference Data API

Public, unauthenticated Consumer Data Right (CDR) Product Reference Data API exposing Unity Bank's deposit, transaction, and credit card products — eligibility, features, pricing, and links to terms and conditions — via `GET /banking/products` and `GET /banking/products/{productId}`. Conforms to the DSB Consumer Data Standards (banking brand code UBL); confirmed live with HTTP 200 responses negotiating standards versions x-v 4 and 5 across 74 published products.

- **Human URL:** [https://www.unitybank.com.au/about-us/corporate-information/public-apis/](https://www.unitybank.com.au/about-us/corporate-information/public-apis/)
- **Base URL:** `https://ibank.gcmutualbank.com.au/openbanking/cds-au/v1`

#### Tags

- CDR
- Open Banking
- Product Reference Data
- Banking
- Australia

#### Properties

- [Documentation](https://www.unitybank.com.au/about-us/corporate-information/public-apis/)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#get-products)
- [OpenAPI](openapi/unity-bank-cds-banking-products-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Common Properties

- [Website](https://www.unitybank.com.au/)
- [Portal](https://www.unitybank.com.au/about-us/corporate-information/public-apis/)
- [Documentation](https://www.unity.bank/about-us/corporate-information/open-banking/)
- [Blog](https://www.unitybank.com.au/latest-news-blog/articles/)
- [Pricing](https://www.unitybank.com.au/help/rates-fees/view-all-rates-fees/)
- [Terms of Service](https://www.unitybank.com.au/about-us/corporate-information/disclosure-documents/)
- [Privacy Policy](https://www.unitybank.com.au/about-us/privacy/)
- [Support](https://www.unitybank.com.au/talk-to-us/contact-us/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
