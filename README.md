# Ease

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

Ease (legally Enrollease, Inc., San Francisco, with offices in Las Vegas and Omaha) is a United States benefits administration and HR platform sold through insurance brokers to small and mid-sized employers of roughly 2-250 employees. It covers online benefits enrollment, benefits and plan management, ACA reporting, onboarding and offboarding, and a partner marketplace spanning carriers, general agencies, third-party administrators, payroll providers and agency management systems. Ease is a group-benefits distribution platform rather than a risk carrier, so its lines of business are medical, dental, vision, life, AD&D, STD, LTD and voluntary/supplemental products written by its carrier partners. It was acquired by Employee Navigator in April 2023 and is now in announced end-of-life: Employee Navigator published a dated two-phase sunset on 2026-06-03 under which no new companies can be added to Ease from 2027-01-01 and the platform goes read-only, with integrations and support discontinued, on 2027-07-01. Its benefits API posture is partner-gated and closed: Ease publishes no public developer portal and no API reference for the product. developer.ease.com, developers.ease.com, api.ease.com and docs.ease.com all resolve through wildcard DNS to the Ease application sign-in page, and ease.com/developers, /api, /developer and /integrations return 404. The real integration surface is EaseConnect (self-service mapping of ANSI X12 EDI 834 enrollment files to carriers), EaseConnect+ (privately negotiated direct carrier data connections, which in the Principal integration include an Evidence of Insurability API and a Member Benefits API that Ease never documents publicly), marketplace API integrations with payroll and HRIS vendors such as ADP Workforce Now, ADP RUN, BambooHR, Paycor and Paylocity, and a partner portal whose data leaves by scheduled report or SFTP. Ease does however operate two real, anonymous, machine-readable read surfaces that this record captures: the WordPress REST API behind www.ease.com, which serves the full Ease Marketplace partner directory (110 partners, 16 partner types, 23 benefit types) alongside blog, page, event and testimonial content; and the Atlassian Statuspage v2 API on status.ease.com, which serves platform status, component health, incident history and an anonymous incident-webhook subscription. No ACORD, AL3, NGDS or IVANS reference appears anywhere on the site - Ease operates in the group-benefits ANSI X12 834 idiom, not the P&C ACORD idiom.

**Areas:** Insurance · United States · Employee Benefits · Benefits Administration · Group Benefits · Health Insurance · Insurtech · Brokerage · Enrollment · EDI · Payroll · Human Resources

## Ease on APIs.io

Everything profiled for Ease is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/ease/](https://apis.io/providers/ease/)** — or go straight to one of the APIs or properties below.

### APIs (4)

- [Ease Website (WordPress REST)](https://apis.io/apis/ease/ease-com-website-wordpress-rest/) — The public WordPress REST API (wp-json) of the Ease website at www.ease.com: the route index of the site's content management system, catalogued as one site…
- [Ease Incidents API](https://apis.io/apis/ease/ease-incidents-api/) — Unresolved and historical incidents, each composed of dated incident updates.
- [Ease Maintenance API](https://apis.io/apis/ease/ease-maintenance-api/) — Upcoming, active and historical scheduled maintenance windows.
- [Ease Status API](https://apis.io/apis/ease/ease-status-api/) — Rollup status indicator and per-component status for the Ease platform.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Ease Status Webhooks](https://apis.io/asyncapis/ease/ease-status-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [ease-mcp.yml](https://apis.io/servers/ease/ease-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Ease Agentic Access](https://apis.io/agentic-access/ease/ease-agentic-access/)

#### Examples (5)

Example requests and responses.

- [Ease Content Types](https://apis.io/examples/ease/ease-content-types/)
- [Ease Status Components](https://apis.io/examples/ease/ease-status-components/)
- [Ease Status Incidents](https://apis.io/examples/ease/ease-status-incidents/)
- [Ease Status Status](https://apis.io/examples/ease/ease-status-status/)
- [Ease Status Summary](https://apis.io/examples/ease/ease-status-summary/)

#### Collections (3)

Postman and Open Collection request collections.

- [Moved to /providers/ease/](https://apis.io/collections/ease/open-ease-content/)
- [API Collection](https://apis.io/collections/ease/open-ease-content-wp-routes-original/)
- [Ease Status API](https://apis.io/collections/ease/open-ease-status/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Ease Status Overlay](https://apis.io/overlays/ease/ease-status-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Ease Authentication](https://apis.io/security/ease/ease-authentication/)
- [Ease Domain Security](https://apis.io/security/ease/ease-domain-security/)
- [Ease Trust Center](https://apis.io/security/ease/ease-trust-center/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.ease.com/)
- [Documentation](https://help.ease.com/)
- [API reference](https://status.ease.com/api)
- [Pricing](https://www.ease.com/pricing/)
- [Support](https://www.ease.com/support/)
- [Blog](https://www.ease.com/blog/)
- [Security](https://www.ease.com/product/security/)
- [Compliance](https://www.ease.com/product/security/sso/)
- [Terms of service](https://www.ease.com/terms/)
- [Privacy policy](https://www.ease.com/privacy/)
- [Status](https://status.ease.com/)

## API Evangelist rating

**Kin Score 39.2** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 57.1 |
| Contract quality | 24.3 |
| Contract governance | 18.2 |
| Operational transparency | 42.1 |
| Developer ergonomics | 37.5 |
| Access clarity | 53.9 |

**Agent readiness 35.2** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | na |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | na |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | — |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | na |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 26.3** — Insurance

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/ease/](https://apis.io/providers/ease/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Ease: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/ease/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
