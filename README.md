# Ease (ease)

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

Ease (legally Enrollease, Inc., San Francisco, with offices in Las Vegas and Omaha) is a United States benefits administration and HR platform sold through insurance brokers to small and mid-sized employers of roughly 2-250 employees. It covers online benefits enrollment, benefits and plan management, ACA reporting, onboarding and offboarding, and a partner marketplace spanning carriers, general agencies, third-party administrators, payroll providers and agency management systems. Ease is a group-benefits distribution platform rather than a risk carrier, so its lines of business are medical, dental, vision, life, AD&D, STD, LTD and voluntary/supplemental products written by its carrier partners. It was acquired by Employee Navigator in April 2023 and the two products continue to run side by side.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/ease/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/ease/refs/heads/main/apis.yml)

## Tags

- Insurance
- United States
- Employee Benefits
- Benefits Administration
- Group Benefits
- Health Insurance
- Insurtech
- Broker
- Enrollment
- EDI
- Payroll
- Human Resources

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## APIs

**None.** Ease publishes no public, self-serve API, no developer portal, no API reference, and no machine-readable specification. This is an honest stub, and it is the correct record for this company.

Probed 2026-07-25:

| Surface | HTTP | Verdict |
| --- | --- | --- |
| `https://developer.ease.com` | 200 → `secure.ease.com` (title "Sign In") | Login wall (wildcard DNS to the Ease app), not a developer portal |
| `https://developers.ease.com` | 200 → `secure.ease.com` (title "Sign In") | Login wall |
| `https://api.ease.com` | 200 → `secure.ease.com` (title "Sign In") | Login wall |
| `https://docs.ease.com` | 200 (title "Login") | Login wall — serves the Ease admin login, not docs |
| `https://ease.com/developers` | 404 | — |
| `https://ease.com/developer` | 404 | — |
| `https://ease.com/api` | 404 | — |
| `https://ease.com/integrations` | 404 | — |
| `https://ease.com/partners` | 200 | Marketing partner program; contact form, no technical onboarding |
| `https://status.ease.com` | 200 | Real public status page |

Every spec path probed — `/openapi.json`, `/swagger.json`, `/api-docs`, `/api`, `/api/v1`, `/docs` across `www.`, `secure.`, `api.` and `developer.` — returned 404 or HTML. No public Postman workspace. No GitHub organization. No OIDC or OAuth discovery document.

## The real integration surface

Ease integrates constantly; none of it is public.

- **EaseConnect (834)** — self-service mapping of ANSI ASC X12 **EDI 834** benefit enrollment and maintenance files to carriers, done inside the customer application.
- **EaseConnect+** — privately negotiated direct data connections between Ease and a carrier, stood up by Ease implementation analysts. The Principal connection is the only place Ease names its own APIs in public: an *Evidence of Insurability (EOI) API* and a *Member Benefits API*. Neither is documented, versioned, or self-serve.
- **Marketplace payroll/HRIS integrations** — ADP Workforce Now, ADP RUN, BambooHR, Paycor, Paylocity. Ease is the API *consumer* here, not the publisher.
- **Partner portal** — data leaves by scheduled report download or SFTP. Batch, not events.

## ACORD posture

**No ACORD reference found; ANSI X12 EDI 834 idiom instead.**

No occurrence of ACORD, AL3, ACORD XML, NGDS, IVANS, Applied Epic or Vertafore AMS360 appears anywhere on ease.com. That is not an oversight — Ease sits in the group-employee-benefits lane, where the exchange standard is ANSI ASC X12 834, not the property-and-casualty ACORD/AL3 agency-download stack. The marketplace lists an "Agency Management" partner category, but that is a directory of partner software, not an ACORD transport claim.

## Quote / Bind / Issue / FNOL

None of the four P&C verbs is publicly exposed. The nearest analogue to *issue* is transmitting enrollment and maintenance records to a carrier over EaseConnect 834 or EaseConnect+ — customer- and partner-gated, never open.

## Auth

No public API authentication scheme is documented. The application itself uses username/password with mandatory two-factor authentication, plus SAML single sign-on via **Okta** on the Enterprise package. Ease claims HIPAA, SOC 2 Type II and HITRUST compliance. `/.well-known/openid-configuration` and `/.well-known/oauth-authorization-server` are not served on `secure.ease.com` (404 HTML).

## Links

- [Website](https://www.ease.com/)
- [Blog](https://www.ease.com/blog/)
- [Partner Program](https://www.ease.com/partners/join-us/)
- [Marketplace](https://www.ease.com/marketplace/)
- [Carrier & Partner Connections](https://www.ease.com/product/platform/marketplace/connections/)
- [Published 834 File Carriers](https://www.ease.com/product/platform/benefits-administration/managing-medical/834-files/)
- [Security](https://www.ease.com/product/security/)
- [Status](https://status.ease.com/)
- [LinkedIn](https://www.linkedin.com/company/ease)

## Review

See [review.yml](review.yml) for the full probe log, transports, and sources, reviewed by API Evangelist on 2026-07-25.
