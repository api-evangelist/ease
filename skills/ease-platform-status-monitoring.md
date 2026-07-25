---
name: Monitor Ease platform status
description: Check whether the Ease benefits platform is up, read its component health and incident history, and subscribe to incident webhooks - all anonymously through the public Ease Status API.
api: openapi/ease-status-openapi.yml
operations:
  - getStatusSummary
  - getStatusRollup
  - listStatusComponents
  - listUnresolvedIncidents
  - listIncidents
generated: '2026-07-25'
method: generated
source: openapi/ease-status-openapi.yml
---

# Monitor Ease platform status

Ease runs a public status page at `https://status.ease.com/` (Atlassian Statuspage, page id
`13zw4w6v89nk`) and Ease itself documents the JSON endpoints at `https://status.ease.com/api`.
This is the only first-party, self-serve, machine-readable *operational* API Ease publishes.

Base URL: `https://status.ease.com/api/v2`

## Before you start

- Every operation is a `GET`, anonymous, JSON. No key, no account, no headers required.
- The page publishes exactly **three components**: `Web Application`, `API`, `Support`. The `API`
  component refers to Ease's internal/partner API plumbing - there is no public developer API
  behind it.
- Prefer webhooks over tight polling (step 5).

## Steps

1. **One call for everything.** Call `getStatusSummary` (`GET /summary.json`). It returns the page
   identity, the rollup `status` object, all components, unresolved incidents, and scheduled
   maintenances in one response. Use this as your default poll.

2. **Cheap up/down check.** Call `getStatusRollup` (`GET /status.json`) when you only need the
   indicator. `status.indicator` is one of `none`, `minor`, `major`, `critical`;
   `status.description` is the human string, e.g. `All Systems Operational`.

3. **Per-component health.** Call `listStatusComponents` (`GET /components.json`) and read
   `status` on each component: `operational`, `degraded_performance`, `partial_outage`,
   `major_outage`, `under_maintenance`. Match on the component `id` (stable) rather than `name`.

4. **Open and historical incidents.** Call `listUnresolvedIncidents`
   (`GET /incidents/unresolved.json`) for anything currently investigating/identified/monitoring,
   and `listIncidents` (`GET /incidents.json`) for the recent history. Each incident carries
   `impact` (`none|minor|major|critical`) and an `incident_updates[]` array of dated posts -
   iterate those newest-first for the narrative. At capture time the page held 26 incidents, the
   most recent being the AWS `us-east-1` outage of 2025-10-19/20.

5. **Stop polling: subscribe.** `https://status.ease.com/` offers anonymous webhook subscription
   (`POST /subscriptions/webhook.json` behind a reCAPTCHA form) that fires whenever Ease creates,
   updates or resolves an incident, or changes a component status. Atom and RSS feeds are also
   published at `/history.atom` and `/history.rss`. Details in
   `asyncapi/ease-status-webhooks.yml`.

## Conventions

No pagination, no rate-limit headers, no request-id header, no structured error body - unknown
paths return an HTML 404. `access-control-allow-origin: *`, so browser clients can call it
directly. See `conventions/ease-conventions.yml`.

## Context that changes how you use this

Ease is in announced end-of-life: no new companies from **2027-01-01**, read-only from
**2027-07-01**, with integrations and support discontinued at that point
(`lifecycle/ease-lifecycle.yml`). A monitor built on this page should carry that expiry.
