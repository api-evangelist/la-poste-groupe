# La Poste Groupe

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

La Poste Groupe is the French state-owned postal, parcel, banking and digital services group. Its public API programme runs on Okapi, the group's own API management platform, published at developer.laposte.fr: nine APIs covering shipment tracking across mail, Colissimo and Chronopost (Suivi v2), address validation and normalisation (ControlAdresse v2), forward and reverse geocoding, the Digiposte certified digital-safe partner API, online registered mail (Lettre recommandee en ligne), driving-licence exam booking (Code de la route) and an Open Data gateway over data.laposte.fr. Colissimo, the group's parcel arm, additionally publishes SOAP contracts for label generation and pickup-point lookup at ws.colissimo.fr, and GeoPost/DPDgroup sits inside the same group. Access is metered by subscription plans with published quotas and prices, and calls are authenticated with an X-Okapi-Key header against the api.laposte.fr gateway.

**Areas:** Company · Logistics · Shipping · Package Tracking · Postal · Addresses · Geocoding · Open Data · Document Management · Identity · Government · France

## La Poste Groupe on APIs.io

Everything profiled for La Poste Groupe is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/la-poste-groupe/](https://apis.io/providers/la-poste-groupe/)** — or go straight to one of the APIs or properties below.

### APIs (17)

- [La Poste ControlAdresse v2](https://apis.io/apis/la-poste-groupe/la-poste-controladresse-v2/) — Address validation and normalisation against the French Service National de l'Adresse reference base. Autocompletes and corrects addresses as they are typed…
- [La Poste Geolocalisation v1](https://apis.io/apis/la-poste-groupe/la-poste-geolocalisation-v1/) — Forward geocoding over the La Poste address base - resolve a known postal address to the GPS coordinates La Poste holds for it, for mapping, routing and…
- [La Poste Geolocalisation inversee v1](https://apis.io/apis/la-poste-groupe/la-poste-geolocalisation-inversee-v1/) — Reverse geocoding - given a latitude/longitude pair, returns between one and five nearby French postal addresses within a predefined radius.
- [Code de la route v2](https://apis.io/apis/la-poste-groupe/code-de-la-route-v2/) — Booking API for "Passer mon code avec La Poste" - the official La Poste driving-theory examination service. Covers session lookup, candidate validation,…
- [Colissimo Web Services](https://apis.io/apis/la-poste-groupe/colissimo-web-services/) — Colissimo's SOAP web services for e-commerce shipping - shipping-label and return-label generation, pickup planning, deposit-slip (bordereau) generation,…
- [La Poste Groupe Administration API](https://apis.io/apis/la-poste-groupe/la-poste-groupe-administration-api/) — The Administration API from La Poste Groupe — 3 operation(s) for administration.
- [La Poste Groupe Applications API](https://apis.io/apis/la-poste-groupe/la-poste-groupe-applications-api/) — The Applications API from La Poste Groupe — 2 operation(s) for applications.
- [La Poste Groupe Digiposte API](https://apis.io/apis/la-poste-groupe/la-poste-groupe-digiposte-api/) — The Digiposte API from La Poste Groupe — 5 operation(s) for digiposte.
- [La Poste Groupe JDD / Éditable API](https://apis.io/apis/la-poste-groupe/la-poste-groupe-jdd-ditable-api/) — The JDD / Éditable API from La Poste Groupe — 10 operation(s) for jdd / éditable.
- [La Poste Groupe JDD / Données API](https://apis.io/apis/la-poste-groupe/la-poste-groupe-jdd-donn-es-api/) — The JDD / Données API from La Poste Groupe — 18 operation(s) for jdd / données.
- [La Poste Groupe JDD / Métadonnées API](https://apis.io/apis/la-poste-groupe/la-poste-groupe-jdd-m-tadonn-es-api/) — The JDD / Métadonnées API from La Poste Groupe — 12 operation(s) for jdd / métadonnées.
- [La Poste Groupe Jeux de données (JDD) API](https://apis.io/apis/la-poste-groupe/la-poste-groupe-jeux-de-donn-es-jdd-api/) — The Jeux de données (JDD) API from La Poste Groupe — 1 operation(s) for jeux de données (jdd).
- [La Poste Groupe LH PRO resources API](https://apis.io/apis/la-poste-groupe/la-poste-groupe-lh-pro-resources-api/) — The LH PRO resources API from La Poste Groupe — 2 operation(s) for lh pro resources.
- [La Poste Groupe Partner API](https://apis.io/apis/la-poste-groupe/la-poste-groupe-partner-api/) — The Partner API from La Poste Groupe — 4 operation(s) for partner.
- [La Poste Groupe Resend Purl API](https://apis.io/apis/la-poste-groupe/la-poste-groupe-resend-purl-api/) — The Resend Purl API from La Poste Groupe — 1 operation(s) for resend purl.
- [La Poste Groupe Suivi API](https://apis.io/apis/la-poste-groupe/la-poste-groupe-suivi-api/) — Everything about one to 10 trackings with or without account's link
- [La Poste Groupe User API](https://apis.io/apis/la-poste-groupe/la-poste-groupe-user-api/) — The User API from La Poste Groupe — 2 operation(s) for user.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [la-poste-groupe-mcp.yml](https://apis.io/servers/la-poste-groupe/la-poste-groupe-mcp-yml/)

#### Overlays (4)

OpenAPI overlays, including conversational phrasing for each operation.

- [La Poste Groupe Digiposte Overlay](https://apis.io/overlays/la-poste-groupe/la-poste-groupe-digiposte-overlay/)
- [La Poste Groupe Lettre Recommandee En Ligne Overlay](https://apis.io/overlays/la-poste-groupe/la-poste-groupe-lettre-recommandee-en-ligne-overlay/)
- [La Poste Groupe Open Data Overlay](https://apis.io/overlays/la-poste-groupe/la-poste-groupe-open-data-overlay/)
- [La Poste Groupe Suivi Overlay](https://apis.io/overlays/la-poste-groupe/la-poste-groupe-suivi-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [La Poste Groupe Authentication](https://apis.io/security/la-poste-groupe/la-poste-groupe-authentication/)
- [La Poste Groupe Domain Security](https://apis.io/security/la-poste-groupe/la-poste-groupe-domain-security/)
- [La Poste Groupe Vulnerability Disclosure](https://apis.io/security/la-poste-groupe/la-poste-groupe-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [La Poste Groupe Scopes](https://apis.io/scopes/la-poste-groupe/la-poste-groupe-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [La Poste Groupe Plans Pricing](https://apis.io/plans/la-poste-groupe/la-poste-groupe-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [La Poste Groupe Rate Limits](https://apis.io/rate-limits/la-poste-groupe/la-poste-groupe-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.lapostegroupe.com/fr)
- [Documentation](https://documentation-okapi.laposte.fr/)
- [Getting started](https://developer.laposte.fr/getting-started)
- [API reference](https://developer.laposte.fr/catalog-apis)
- [Support](https://faq.developer.laposte.fr)
- [Blog](https://www.lapostegroupe.com/fr/newsroom)
- [Terms of service](https://developer.laposte.fr/cgu)
- [Privacy policy](https://developer.laposte.fr/data-privacy)
- [GitHub](https://github.com/DeveloperLaPoste)
- [Status](https://developer.laposte.fr/status/api)

## API Evangelist rating

**Kin Score 60.5** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 50.9 |
| Contract governance | 0.0 |
| Operational transparency | 60.5 |
| Developer ergonomics | 80.4 |
| Access clarity | 63.2 |

**Agent readiness 35.8** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | yes |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | documented (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | distinct |

**Regulatory alignment 40.2** — Government & Public Sector

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/la-poste-groupe/](https://apis.io/providers/la-poste-groupe/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for La Poste Groupe: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/la-poste-groupe/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
