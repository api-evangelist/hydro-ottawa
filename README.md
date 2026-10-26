# Hydro Ottawa (hydro-ottawa)

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
