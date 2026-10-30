# Hydro Ottawa

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

Hydro Ottawa Holding Inc. is a private corporation 100 percent owned by the City of Ottawa, and the parent of Hydro Ottawa Limited — the regulated local distribution company (LDC) that delivers electricity to roughly 372,000 customers in Ottawa and Casselman, Ontario — alongside Portage Power (Ontario's largest municipally-owned renewable generator, with run-of-river hydroelectric plants at Chaudière Falls and elsewhere in Ontario, Quebec and New York plus solar installations across Ottawa), Envari (energy solutions) and Hiboo Networks (fibre). It sits at the wires-and-meter end of the Canadian value chain: it does not run the market — that is IESO — and it is not a competitive retailer, it is the monopoly distributor that owns the smart meter, the interval data and the billing relationship. Its API posture exists because Ontario legislated it. Ontario Regulation 633/21 (Energy Data) under the Electricity Act, 1998 compels roughly sixty electricity and natural gas utilities in the province to implement Green Button Download My Data and Green Button Connect My Data to the NAESB REQ.21 ESPI v3.3 standard and to have those implementations certified by the Green Button Alliance — a province-level, standard-specific consumer data mandate with no Canadian national equivalent. Hydro Ottawa states on its own site that it offers both services free of charge and that third parties must complete its onboarding process and certify with the GBA. Two live surfaces back that up: a customer Green Button authorization portal at https://hydroottawa.savagedata.com/Connect/Authorize (HTTP 200) and an anonymously reachable third-party developer registration application at https://ottawaonboarding.savagedata.com/ (HTTP 200), both operated by the North Bay vendor Savage Data Systems. What could NOT be verified is the thing the mandate actually requires: no ESPI base URI is published anywhere, the vendor host is a catch-all Blazor SPA that returns HTTP 200 with identical HTML for every path including invented ones, no OpenID Connect discovery document is served anonymously, and no public Green Button Alliance certificate register listing Hydro Ottawa by name could be found. The mandate is recorded here as claimed-and-plausibly- operating, not as verified. Everything else is closed: hydroottawa.com returns 404 for /developers, /api, /docs, /data, /openapi.json and /swagger.json; developers.hydroottawa.com does not resolve and developersdev.hydroottawa.com answers HTTP 530 through Cloudflare; api.hydroottawa.com exists but returns 403 at root and 404 on every path; the github.com/hydroottawa organization has existed since 2015 with zero public repositories; and the City of Ottawa open data portal carries 682 datasets, none of them Hydro Ottawa's. The one genuinely open, anonymous, machine-readable feed carrying Hydro Ottawa data — live outage counts under the KUBRA StormCenter instance behind outages.hydroottawa.com — is undocumented vendor infrastructure that Hydro Ottawa does not publish as a product, and it is deliberately not listed as an API here. Hydro Ottawa is therefore a utility with a mandated consumer data API it does not document, and no open market data at all.

**Areas:** Energy · Canada · Ontario · Utilities · Electricity · Electricity Distribution · Smart Metering · Green Button · ESPI · Municipal Utility · Renewables · Hydroelectric

## Hydro Ottawa on APIs.io

Everything profiled for Hydro Ottawa is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/hydro-ottawa/](https://apis.io/providers/hydro-ottawa/)** — or go straight to one of the APIs or properties below.

### APIs (4)

- [Hydro Ottawa Application Information API](https://apis.io/apis/hydro-ottawa/hydro-ottawa-applicationinformation-api/) — Application Information endpoints
- [Hydro Ottawa Authorization API](https://apis.io/apis/hydro-ottawa/hydro-ottawa-authorization-api/) — Authorization endpoints
- [Hydro Ottawa Batch API](https://apis.io/apis/hydro-ottawa/hydro-ottawa-batch-api/) — Batch data transfer endpoints
- [Hydro Ottawa Usage Point API](https://apis.io/apis/hydro-ottawa/hydro-ottawa-usagepoint-api/) — Usage Point endpoints

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Collections (1)

Postman and Open Collection request collections.

- [Green Button API Documentation](https://apis.io/collections/hydro-ottawa/open-hydro-ottawa-green-button-espi/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Hydro Ottawa Green Button Espi Overlay](https://apis.io/overlays/hydro-ottawa/hydro-ottawa-green-button-espi-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Hydro Ottawa Authentication](https://apis.io/security/hydro-ottawa/hydro-ottawa-authentication/)
- [Hydro Ottawa Domain Security](https://apis.io/security/hydro-ottawa/hydro-ottawa-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Hydro Ottawa Scopes](https://apis.io/scopes/hydro-ottawa/hydro-ottawa-scopes/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://hydroottawa.com/)
- [Documentation](https://hydroottawa.com/en/residential/rates-billing/track-your-usage/green-button)
- [Getting started](https://hydroottawa.com/en/accounts-services/services/green-button/green-button-and-third-party-registration)
- [Sign up](https://ottawaonboarding.savagedata.com/)
- [Support](https://hydroottawa.com/en/faq)
- [Blog](https://hydroottawa.com/en/about-us/blogs-articles)
- [Terms of service](https://hydroottawa.com/en/about-us/policies-and-terms/terms-use)
- [Privacy policy](https://hydroottawa.com/en/about-us/policies-and-terms/privacy-notice)
- [GitHub](https://github.com/hydroottawa)
- [Status](https://outages.hydroottawa.com/)

## API Evangelist rating

**Kin Score 22.8** — emerging · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 57.1 |
| Contract quality | 11.1 |
| Contract governance | 4.5 |
| Operational transparency | 2.6 |
| Developer ergonomics | 30.4 |
| Access clarity | 21.1 |

**Agent readiness 25.6** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | na |
| MCP Server | — |
| Auth Clarity | negotiable (partial credit) |
| Idempotency | na |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | — |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | na |
| Delegated Identity | documented (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 34.4** — Energy & Utilities

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/hydro-ottawa/](https://apis.io/providers/hydro-ottawa/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Hydro Ottawa: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/hydro-ottawa/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
