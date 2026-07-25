---
name: Research Ease content and events
description: Search Ease's published content and pull blog posts, marketing pages, events, testimonials and media through the public, anonymous Ease Content API.
api: openapi/ease-content-openapi.yml
operations:
  - search
  - listPosts
  - getPost
  - listEvents
  - listPages
  - listMedia
  - listTypes
generated: '2026-07-25'
method: generated
source: openapi/ease-content-openapi.yml
---

# Research Ease content and events

Everything Ease publishes on `www.ease.com` is readable as JSON, anonymously, from the
WordPress REST API at `https://www.ease.com/wp-json`. Useful when you need Ease's own words -
product positioning, carrier and payroll integration announcements, event schedule - as
structured data rather than scraped HTML.

Base URL: `https://www.ease.com/wp-json`

## Steps

1. **Discover what exists.** Call `listTypes` (`GET /wp/v2/types`) to enumerate the registered
   content types and their `rest_base`. On ease.com the publicly readable ones are `posts`,
   `pages`, `media`, `event`, `testimonials` and `partner`.

2. **Cross-type search.** Call `search` (`GET /wp/v2/search?search=<term>`). It returns lightweight
   `{id, title, url, type, subtype}` hits across every public type - the fastest way to locate a
   page before fetching it in full.

3. **Blog posts.** Call `listPosts`. Filter with `search`, `categories`, `tags`, `after`,
   `before`, `modified_after`; sort with `orderby=date|modified|relevance` and `order`. Then
   `getPost` for a single record. Bodies come back as rendered HTML in `content.rendered`, with a
   plain-text-ish summary in `excerpt.rendered`.

   ```
   GET /wp/v2/posts?search=EaseConnect&per_page=20&_fields=id,slug,link,title,date,excerpt
   ```

4. **Marketing and product pages.** Call `listPages` the same way. `parent` gives you the page
   hierarchy, so you can walk `/product/platform/...` as a tree.

5. **Events.** Call `listEvents` (`GET /wp/v2/event`, 33 records) and filter by `event_cat` term
   ids to separate in-person from virtual.

6. **Media.** Call `listMedia` and read `source_url`, `mime_type`, `alt_text` and
   `media_details.sizes` - or attach media inline to any record with `_embed=1`.

## Working efficiently

- Always pass `_fields` to trim the response. Every record carries a `yoast_head` /
  `yoast_head_json` SEO block that dominates the payload.
- `per_page` maxes at 100. Read `X-WP-Total` and `X-WP-TotalPages`, or follow
  `Link: rel="next"`.
- `_embed=1` materialises author, featured media and terms into `_embedded`, saving a round trip.
- `_envelope=1` wraps the response as `{body, status, headers}` when you cannot read response
  headers.
- Errors are `{"code","message","data":{"status"}}`, not RFC 9457 - see
  `errors/ease-problem-types.yml`.

## Scope

This is the marketing site. It is not the Ease benefits administration API, and it exposes no
customer, employer, employee or enrollment data. Administrative routes (`users`, `settings`,
`plugins`) exist on the host but return `401` anonymously - leave them alone.
