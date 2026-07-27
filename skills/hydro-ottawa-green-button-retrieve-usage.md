---
name: Retrieve a customer's Green Button usage data from Hydro Ottawa
description: >-
  With a registered and certified third-party application, obtain a Hydro Ottawa customer's
  consent through the Green Button Connect My Data authorization flow, verify the resulting
  Authorization resource, walk to the customer's UsagePoint records, and pull bulk data.
  Handles the consent-revocation reality that makes a 403 an expected steady state rather
  than a client defect.
api: openapi/hydro-ottawa-green-button-espi-openapi.yml
operations:
  - findAuthorizations
  - getAuthorization
  - findUsagePoints
  - getUsagePoint
  - downloadBulkData
generated: '2026-07-27'
method: generated
---

# Retrieve a customer's Green Button usage data from Hydro Ottawa

## Prerequisites

Complete `hydro-ottawa-green-button-onboarding.md` first. You need connection details Hydro
Ottawa issues only after third-party onboarding and Green Button Alliance certification.
There is no base URI to discover — it is not published, and no anonymously served OpenID
Connect discovery document exists on any Hydro Ottawa or Savage Data host.

The referenced OpenAPI is the Green Button Alliance's, not Hydro Ottawa's. Operation names
and parameter shapes are real; the `servers[]` host is the GBA sandbox and must be replaced
with the base URI Hydro Ottawa issues you.

## Steps

1. **Initiate the authorization from inside your application.** Hydro Ottawa is explicit
   that the flow must start in the third-party app, which then redirects the customer into
   Hydro Ottawa's Green Button authentication. The customer-facing half of that flow lives
   at <https://hydroottawa.savagedata.com/Connect/Authorize>.

2. **Let the customer set the terms.** The customer selects the data types, the duration
   and the frequency, and can revoke at any time from account settings. Personally
   identifiable information is transmitted separately from usage data — do not assume the
   usage feed carries customer identity.

3. **Exchange the code for a token.** OAuth 2.0 authorization code. The spec also declares
   a `clientCredentials` flow. The `scopes` object in the source document is **empty** and
   Hydro Ottawa publishes no scope reference, so do not hard-code scope strings — use what
   your onboarding packet specifies. See `scopes/hydro-ottawa-scopes.yml`.

4. **Verify the Authorization resource.**
   - `findAuthorizations` — `GET /espi/1_1/resource/Authorization`
   - `getAuthorization` — `GET /espi/1_1/resource/Authorization/{authorizationId}`

   Read `status` (0=Revoked, 1=Active, 2=Denied), `expires_at` (Unix timestamp),
   `grant_type`, `scope` and `token_type`. Persist `resourceURI` (where the authorized data
   lives), `authorizationURI` (where to update or delete this authorization) and
   `customerResourceURI` (the separately-transmitted PII). **Treat `status` and
   `expires_at` as the authority on whether you may still call** — not the age of your
   token.

5. **Walk to the meter.**
   - `findUsagePoints` — `GET /espi/1_1/resource/UsagePoint`
   - `getUsagePoint` — `GET /espi/1_1/resource/UsagePoint/{usagePointId}`

   `ServiceCategory` is an integer enum (0=electricity, 1=gas, 2=water); Hydro Ottawa is an
   electricity distributor, so expect 0. `status` is 0=off / 1=on. `isSdp` marks a service
   delivery point and `isVirtual` marks a logical usage point — do not treat a virtual
   usage point as a physical meter.

6. **Pull bulk data.**
   - `downloadBulkData` — `GET /espi/1_1/resource/Batch/Bulk/{bulkId}`

   This is the asynchronous path. A `202 Accepted` here is the expected first answer — poll
   for the Atom feed rather than treating it as a failure.

7. **Scope your time window.** Use `published-min` / `published-max` and `updated-min` /
   `updated-max` (RFC 3339 instants) with `start-index` and `max-results`. Hydro Ottawa
   makes up to **24 months** available at the meter's own interval (15-minute, hourly or
   daily); the regulation requires intervals of one hour or less and at least 24 months.
   Anything older is a human form:
   <https://hydroottawa.com/en/accounts-services/services/request-additional-electricity-meter-data>

## Handling failures

- **`403 Forbidden` is an expected steady state.** Green Button consent is
  customer-granted, scoped and revocable. A 403 on a call that worked yesterday most likely
  means the customer revoked or the authorization expired. **Re-obtain consent; do not
  retry.** Confirm by reading `status` on the Authorization resource.
- **`400 Bad Request`** is almost always a malformed timestamp (not RFC 3339) or a
  non-integer `start-index`, `max-results` or `depth`.
- **Errors carry no body.** No schema, no `application/problem+json`. You will not get a
  machine-readable reason — log the request parameters yourself.
- **No `401`, `404`, `429` or `5xx` is declared** anywhere in the contract, and no rate
  limits are published. Do not assume they cannot occur; build backoff regardless.

## Notes an agent should carry

- Responses are **Atom XML**, never JSON.
- The ESPI resources that carry actual interval consumption values (`MeterReading`,
  `IntervalBlock`, `IntervalReading`, `ReadingType`, the usage summaries) are **not defined
  in this specification** and Hydro Ottawa publishes no schema for them. Expect them on the
  wire; do not expect this document to describe them.
- Hydro Ottawa's Green Button conformance could not be verified from outside — no base URI,
  no reference, no discovery document, and no public Green Button Alliance certified-products
  register naming Hydro Ottawa. See `review.yml`.

## Related artifacts

`conventions/hydro-ottawa-conventions.yml` · `authentication/hydro-ottawa-authentication.yml` ·
`scopes/hydro-ottawa-scopes.yml` · `errors/hydro-ottawa-problem-types.yml` ·
`data-model/hydro-ottawa-data-model.yml` · `lifecycle/hydro-ottawa-lifecycle.yml`
