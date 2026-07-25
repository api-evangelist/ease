# Ease (ease)

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
