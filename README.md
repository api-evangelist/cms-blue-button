# CMS Blue Button 2.0 (cms-blue-button)

Blue Button 2.0 is the Centers for Medicare & Medicaid Services (CMS) API that lets Medicare beneficiaries share their Parts A, B, and D claims data with applications they trust. It is a FHIR R4 (4.0.1) API conforming to the CARIN Blue Button Implementation Guide (CARIN Consumer Directed Payer Data Exchange), serving ExplanationOfBenefit, Patient, and Coverage resources for 60+ million people with Medicare.

The access model is patient-facing and consent-driven: there is no way to bulk-query beneficiaries. Each Medicare enrollee authorizes an application individually through an OAuth 2.0 authorization-code flow (PKCE S256 is mandatory) using their Medicare.gov login, and can decline to share demographic data during that flow. The API is free at every stage. The sandbox at `sandbox.bluebutton.cms.gov` is fully self-serve, mirrors production endpoints, and ships synthetic data for 10,000 Medicare enrollees. Production access is approval-gated - you draft a public privacy policy and terms of service, apply, and demo your application to the CMS team (a one-hour walkthrough of account creation, authorization, data display, and data-use practices) before production credentials are issued. Access tokens last one hour; one-time-use refresh tokens are only issued to approved 13-month and research application types.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/cms-blue-button/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/cms-blue-button/refs/heads/main/apis.yml)

## Tags

- Blue Button
- CARIN
- Medicare
- FHIR
- Claims Data
- Patient Access
- Healthcare
- Government

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### CMS Blue Button 2.0 Explanation of Benefit API

Returns a beneficiary's Medicare Parts A, B, and D claims as FHIR R4 ExplanationOfBenefit resources in a Bundle, conforming to the CARIN Blue Button (CARIN CDPDE) profiles. Supports filtering by patient, claim type (carrier, pde, dme, hha, hospice, inpatient, outpatient, snf), service-date, `_lastUpdated`, `excludeSAMHSA`, and paging via `_count`/`startIndex`.

- **Human URL:** [https://bluebutton.cms.gov/api-documentation/calling-the-api/](https://bluebutton.cms.gov/api-documentation/calling-the-api/)
- **Base URL:** `https://api.bluebutton.cms.gov/v2/fhir`

#### Tags

- Claims Data
- Explanation of Benefit
- CARIN
- FHIR

#### Properties

- [Documentation](https://bluebutton.cms.gov/api-documentation/)
- [API Reference](https://bluebutton.cms.gov/data/understanding-the-data/)
- [OpenAPI](openapi/cms-blue-button-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/cms-blue-button.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/cms-blue-button.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### CMS Blue Button 2.0 Patient API

Returns the authorized beneficiary's demographic and administrative record as a FHIR R4 Patient resource. Beneficiaries can decline to share demographic data during the Medicare.gov authorization flow, in which case apps fall back to identifiers in the Coverage and ExplanationOfBenefit bundles.

- **Human URL:** [https://bluebutton.cms.gov/api-documentation/calling-the-api/](https://bluebutton.cms.gov/api-documentation/calling-the-api/)
- **Base URL:** `https://api.bluebutton.cms.gov/v2/fhir`

#### Tags

- Patient
- Demographics
- FHIR
- Patient Access

#### Properties

- [Documentation](https://bluebutton.cms.gov/api-documentation/)
- [OpenAPI](openapi/cms-blue-button-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/cms-blue-button.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/cms-blue-button.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### CMS Blue Button 2.0 Coverage API

Returns a beneficiary's Medicare coverage as FHIR R4 Coverage resources in a Bundle - one resource per coverage type (Part A, Part B, Part D) - searched by beneficiary reference with `_lastUpdated`, `_profile`, and paging parameters.

- **Human URL:** [https://bluebutton.cms.gov/api-documentation/calling-the-api/](https://bluebutton.cms.gov/api-documentation/calling-the-api/)
- **Base URL:** `https://api.bluebutton.cms.gov/v2/fhir`

#### Tags

- Coverage
- Medicare
- Enrollment
- FHIR

#### Properties

- [Documentation](https://bluebutton.cms.gov/api-documentation/)
- [OpenAPI](openapi/cms-blue-button-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/cms-blue-button.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/cms-blue-button.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### CMS Blue Button 2.0 Authorization and UserInfo API

OAuth 2.0 authorization-code flow with mandatory PKCE (S256) that beneficiaries use to grant an app access to their Medicare data via Medicare.gov login, plus the `/v2/connect/userinfo` endpoint returning the authorized user's OpenID Connect profile. Access tokens last one hour; one-time-use refresh tokens are issued to approved 13-month and research application types.

- **Human URL:** [https://bluebutton.cms.gov/api-documentation/authorization/](https://bluebutton.cms.gov/api-documentation/authorization/)
- **Base URL:** `https://api.bluebutton.cms.gov/v2`

#### Tags

- OAuth
- OpenID Connect
- Consent
- Patient Access

#### Properties

- [Documentation](https://bluebutton.cms.gov/api-documentation/authorization/)
- [OpenAPI](openapi/cms-blue-button-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/cms-blue-button.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/cms-blue-button.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Website](https://bluebutton.cms.gov)
- [Documentation](https://bluebutton.cms.gov/api-documentation/)
- [GitHub Organization](https://github.com/CMSgov)
- [Sandbox](https://sandbox.bluebutton.cms.gov)
- [Getting Started / Production Access](https://bluebutton.cms.gov/production-access/)
- [Terms of Service](https://bluebutton.cms.gov/terms/)
- [Plans](plans/cms-blue-button-plans-pricing.yml)
- [Rate Limits](rate-limits/cms-blue-button-rate-limits.yml)
- [Fin Ops](finops/cms-blue-button-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
