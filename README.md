# CMS Blue Button 2.0 (cms-blue-button)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
