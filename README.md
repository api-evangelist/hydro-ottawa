# Hydro Ottawa (hydro-ottawa)

Hydro Ottawa Holding Inc. is a private corporation 100 percent owned by the City of Ottawa, and the parent of Hydro Ottawa Limited — the regulated local distribution company that delivers electricity to roughly 372,000 customers in Ottawa and Casselman, Ontario — alongside Portage Power, Envari and Hiboo Networks. Its API posture exists because Ontario legislated it: O. Reg. 633/21 (Energy Data) compels covered Ontario utilities to implement Green Button Download My Data and Connect My Data to NAESB REQ.21 ESPI v3.3 and certify with the Green Button Alliance. Hydro Ottawa runs both services on live, branded portals — and publishes no base URI, no endpoint, no specification and no scope list, so the mandated API cannot be verified from outside the utility.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/hydro-ottawa/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/hydro-ottawa/refs/heads/main/apis.yml)

## Tags

- Energy
- Canada
- Ontario
- Utilities
- Electricity
- Electricity Distribution
- Smart Metering
- Green Button
- ESPI
- Municipal Utility
- Renewables
- Hydroelectric
- Solar
- Demand Response
- Grid

## Timestamps

- **Created:** 2026-07-27
- **Modified:** 2026-07-27

## APIs

### Hydro Ottawa Green Button Connect My Data (CMD) API

Hydro Ottawa's mandated Green Button Connect My Data surface — the OAuth-authorized channel through which a customer grants a third-party application ongoing access to their smart meter interval consumption and billing data in NAESB REQ.21 ESPI XML. Required by Ontario Regulation 633/21. The customer-facing half of the flow was confirmed live (HTTP 200) on 2026-07-27. No base URL is recorded because Hydro Ottawa publishes no ESPI base URI, no API reference and no first-party specification — a developer receives connection details only after onboarding and Green Button Alliance certification.

- **Human URL:** [https://hydroottawa.com/en/residential/rates-billing/track-your-usage/green-button](https://hydroottawa.com/en/residential/rates-billing/track-your-usage/green-button)
- **Base URL:** not published

#### Tags

- Green Button
- Connect My Data
- ESPI
- Energy Usage
- Smart Metering
- Consumer Data
- Ontario
- Canada

#### Properties

- [OpenAPI](openapi/hydro-ottawa-green-button-espi-openapi.yml) — Green Button Alliance ESPI specification, harvested verbatim with provenance. Not authored by Hydro Ottawa.
- [Documentation](https://hydroottawa.com/en/residential/rates-billing/track-your-usage/green-button)
- [Documentation](https://hydroottawa.com/en/accounts-services/services/green-button/green-button-and-third-party-registration)
- [Registration](https://ottawaonboarding.savagedata.com/)
- [Authentication](https://hydroottawa.savagedata.com/Connect/Authorize)
- [Certification](https://www.greenbuttonalliance.org/testing)
- [Regulation](https://www.canlii.org/en/on/laws/regu/o-reg-633-21/latest/o-reg-633-21.html)
- [OEB Guidance](https://www.oeb.ca/sites/default/files/OEB-Staff-Guidance-for-Implementation-of-Green-Button-20211101.pdf)

## Mandate

| Field | Value |
| --- | --- |
| Regime | `green-button-ontario` — O. Reg. 633/21 (Energy Data), Electricity Act, 1998 |
| Status | `live-claimed-unverified` |
| Data standard | NAESB REQ.21 ESPI v3.3 (Green Button), mandated version |
| Consumer data API | Yes — Green Button Connect My Data |
| Open market data | No |
| Access gate | `application-approval` — Hydro Ottawa onboarding, then Green Button Alliance certification |
| Home market | Canada |

Two live surfaces were confirmed by anonymous HTTP on 2026-07-27: a customer Green Button authorization portal and a third-party developer registration application. What could not be confirmed is the ESPI API itself — no base URI, no endpoint list, no OpenID Connect discovery document, and no public Green Button Alliance certificate naming Hydro Ottawa. Every HTTP 200 returned by the vendor host was control-tested against a deliberately invented path and discarded as catch-all SPA behaviour. Full probe log in [review.yml](review.yml).

## Common

- [Website](https://hydroottawa.com/)
- [Website](https://hydroottawagroup.com/)
- [Documentation](https://hydroottawa.com/en/residential/rates-billing/track-your-usage/green-button)
- [Registration](https://ottawaonboarding.savagedata.com/)
- [Support](https://hydroottawa.com/en/faq)
- [Status Page](https://outages.hydroottawa.com/)
- [GitHub Organization](https://github.com/hydroottawa)
- [LinkedIn](https://www.linkedin.com/company/hydro-ottawa)
- [Bluesky](https://bsky.app/profile/hydroottawa.bsky.social)
- [YouTube](https://www.youtube.com/user/hydroottawalimited/)

## Maintainers

- Kin Lane — kin@apievangelist.com
