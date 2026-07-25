---
name: Discover Ease Marketplace partners
description: Search, filter and read the Ease Marketplace partner directory - carriers, general agencies, TPAs, payroll providers and agency-management vendors - through the public, anonymous Ease Content API.
api: openapi/ease-content-openapi.yml
operations:
  - listPartners
  - getPartner
  - listPartnerTypes
  - listBenefitTypes
generated: '2026-07-25'
method: generated
source: openapi/ease-content-openapi.yml
---

# Discover Ease Marketplace partners

The Ease Marketplace is published as a public WordPress custom post type. It is the only
substantive Ease business data available without a login: **110 partner records**, classified by
**16 partner types** and **23 benefit types**. No API key, no account, no OAuth.

Base URL: `https://www.ease.com/wp-json`

## Before you start

- Every operation is anonymous. Do not send an `Authorization` header; Ease publishes no
  developer credentials and the write routes are site administration, not a developer program.
- There is **no idempotency contract and no rate-limit signalling**. Be conservative: this is a
  marketing site on shared hosting, not a metered API.
- Ease is in announced end-of-life. New companies stop 2027-01-01, and the platform goes
  read-only 2027-07-01 (`lifecycle/ease-lifecycle.yml`). Anything built on this directory should
  assume it disappears.

## Steps

1. **Load the classification vocabularies first.** Call `listPartnerTypes` and `listBenefitTypes`
   with `per_page=100` and `_fields=id,name,slug,count`. You need the term **ids** to filter, and
   the `count` tells you how many partners each term carries.

   ```
   GET /wp/v2/partner_types?per_page=100&_fields=id,name,slug,count
   GET /wp/v2/benefit_types?per_page=100&_fields=id,name,slug,count
   ```

   The `benefit_types` vocabulary is where the Ease integration idiom lives: `EaseConnect`
   (self-service X12 834 file mapping), `EaseConnect+` (privately negotiated direct carrier
   connection), `COBRA Integration`, `HSA HRA & FSA Integration`, `Premium Billing Services`.

2. **List partners, filtered.** Call `listPartners`. Filter by term id, page with `per_page`
   (maximum 100) and `page`, and trim the payload with `_fields` - the raw record carries a very
   large `yoast_head` SEO block you almost never want.

   ```
   GET /wp/v2/partner?per_page=100&_fields=id,slug,link,title,partner_types,benefit_types,modified
   GET /wp/v2/partner?partner_types=343&per_page=100        # e.g. Agency Management
   ```

3. **Page correctly.** Read `X-WP-Total` and `X-WP-TotalPages` from the response headers, or
   follow the `Link: <...>; rel="next"` header until it is absent. Requesting a page past the end
   returns **400 `rest_post_invalid_page_number`**; `per_page` above 100 returns **400
   `rest_invalid_param`** with the reason in `data.details.per_page`.

4. **Read one partner in full.** Call `getPartner` with the record id when you need the listing
   body. `content.rendered` is HTML describing the Ease/partner integration; `link` is the public
   marketplace page, for example `https://www.ease.com/marketplace/voya/`.

   ```
   GET /wp/v2/partner/14132
   ```

5. **Resolve the logo if you need it.** `featured_media` is a media id (`0` when absent). Either
   call `getMediaItem`, or re-request the partner with `_embed=1` and read
   `_embedded['wp:featuredmedia']`.

6. **Sort and window.** `orderby` accepts `date`, `modified`, `title`, `slug`, `id`, `include`;
   `order` is `asc` or `desc`. `modified_after` / `modified_before` take ISO 8601 timestamps, so
   an incremental sync is `?modified_after=<last-run>&orderby=modified&order=asc`.

## Error handling

Errors are the WordPress envelope, **not** RFC 9457: `{"code": "...", "message": "...",
"data": {"status": 400}}`. Full catalog in `errors/ease-problem-types.yml`. The ones you will
actually hit are `rest_invalid_param`, `rest_post_invalid_page_number` and `rest_no_route`.

## What this skill cannot do

Nothing in the Ease benefits platform is reachable here. There is no public operation for
employers, employees, enrollments, plans, ACA filings or EDI 834 transmissions - those move over
EaseConnect, EaseConnect+ and partner-portal SFTP behind a login. Do not attempt to construct
such calls.
