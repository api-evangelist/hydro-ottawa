---
name: Onboard as a Hydro Ottawa Green Button third party
description: >-
  Get from zero to a registered, certified third-party application against Hydro Ottawa's
  mandated Green Button Connect My Data surface, and confirm the registration by reading
  back the ApplicationInformation resource. Most of this flow is a human approval process,
  not an API call — the skill exists so an agent stops looking for a self-serve key that
  does not exist.
api: openapi/hydro-ottawa-green-button-espi-openapi.yml
operations:
  - findApplicationInformations
  - getApplicationInformation
generated: '2026-07-27'
method: generated
---

# Onboard as a Hydro Ottawa Green Button third party

## Read this before you try anything

Hydro Ottawa publishes **no ESPI base URI, no API reference, no scope list and no
first-party specification**. Do not guess a base URL. `api.hydroottawa.com` resolves but
returns HTTP 403 at root and 404 on every path probed; `developers.hydroottawa.com` does
not resolve. There is no sandbox, no API key form, no trial and no pricing page.

The OpenAPI referenced above is authored by the **Green Button Alliance**, not by Hydro
Ottawa. It describes ESPI 4.0; Ontario Regulation 633/21 mandates **ESPI v3.3**. Its
`servers[]` points at the GBA sandbox. Use it to learn the shape of the contract and the
operation names — never as Hydro Ottawa's live endpoint.

## Steps

1. **Confirm the obligation applies.** Hydro Ottawa Limited is a licensed Ontario
   electricity distributor covered by O. Reg. 633/21 (Energy Data) under the Electricity
   Act, 1998, which compels Green Button Download My Data and Connect My Data to NAESB
   REQ.21 ESPI v3.3, certified by the Green Button Alliance. Hydro Ottawa states both
   services are free of charge. Reference:
   <https://hydroottawa.com/en/residential/rates-billing/track-your-usage/green-button>

2. **Register the application.** Complete Hydro Ottawa's third-party onboarding at
   <https://ottawaonboarding.savagedata.com/> — a live registration application operated
   by Savage Data Systems. It publishes no documentation, no endpoint list and no
   credentials on its public shell. This step is human-gated; there is nothing to
   automate.

3. **Certify with the Green Button Alliance.** Test and certify the solution at
   <https://www.greenbuttonalliance.org/testing>. Hydro Ottawa requires this before it
   will issue connection details.

4. **Receive connection details.** Only after steps 2 and 3 does Hydro Ottawa disclose the
   ESPI base URI, the OAuth authorization and token endpoints, and the client credentials.
   Record them locally — they are not published and must not be inferred.

5. **Read back your registration.** Once credentialed, confirm the Data Custodian's view
   of your application:
   - `findApplicationInformations` — `GET /espi/1_1/resource/ApplicationInformation`,
     returns the Atom feed of application records.
   - `getApplicationInformation` — `GET /espi/1_1/resource/ApplicationInformation/{applicationInformationId}`,
     returns one record.

   Check `dataCustodianApplicationStatus` and `thirdPartyApplicationStatus`, and verify
   that `client_id`, `redirect_uri`, `scope` and `grant_types` match what you registered.
   `thirdPartyApplicationType` is an integer enum: 1=Web, 2=Desktop, 3=Mobile, 4=Device.

## Conventions that apply to every call

- **Media type is `application/atom+xml`, not JSON.** Responses are Atom feeds
  (`AtomFeed` → `AtomEntry` → `AtomContent`) wrapping the ESPI resource. Build an XML path.
- **Pagination** is `start-index` (1-indexed) plus `max-results`.
- **Filtering** is `published-min` / `published-max` / `updated-min` / `updated-max`,
  RFC 3339 instants.
- **`depth`** controls response depth; the spec gives no value range.
- **`202 Accepted` is a normal outcome**, declared on every operation. Poll; do not fail.
- **Errors carry no body.** `400` and `403` are declared with a description only — no
  schema, no `application/problem+json`. See `errors/hydro-ottawa-problem-types.yml`.
- **No idempotency key, no request-id header, no documented rate limits.** Absence of a
  published limit is not absence of a limit; expect to learn them after onboarding.

## Related artifacts

`conventions/hydro-ottawa-conventions.yml` · `authentication/hydro-ottawa-authentication.yml` ·
`conformance/hydro-ottawa-conformance.yml` · `data-model/hydro-ottawa-data-model.yml` ·
`review.yml` (the full probe record, including what could not be verified)
