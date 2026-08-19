---
name: Pull RevContent publisher widget reporting
description: Enumerate publisher widgets, pull geo and Sub ID performance, and manage publisher-owned internal content.
api: openapi/revcontent-widgets-api-openapi.yml
operations: [getOauthAccess, getAllWidgets, getAllWidgetsGeo, getSubIDStats, getWidgetInternalContent, postWidgetInternalContentAdd, postWidgetInternalContentUpdate]
generated: '2026-08-13'
method: generated
source: openapi/ (derived from https://api.revcontent.io/docs/stats/api_data.json)
---

# Pull RevContent publisher widget reporting

The publisher side of the API. Same token, same envelope, different objects.

Authenticate first (`getOauthAccess`, 24-hour bearer token).

## 1. Enumerate widgets

`getAllWidgets` — `GET /stats/api/v1.0/widgets`. Your placement inventory with performance for the
window. `date_from` / `date_to` in `Y-m-d`; default window is first-of-month → today.

## 2. Geo breakdown

`getAllWidgetsGeo` — `GET /stats/api/v1.0/widgets_geo`.

**Watch the page ceiling here.** Most list operations allow `limit` up to 1000; this one documents
**max 100**. A client that assumes a global 1000 will silently under-read this endpoint. Page with
`offset` until a page returns fewer than `limit` rows.

## 3. Sub ID attribution

`getSubIDStats` — `GET /stats/api/v1.0/widgets/{widget_id}/revsub`.

Sub IDs are set on the embed side, in the ad code (`adcode-devkit`, "Using Subids"), and read back
here. This is the only join between what a publisher deployed on-page and what the API reports, so
if Sub IDs are missing from the report the fix is in the widget markup, not the API call.

## 4. Publisher-owned internal content

Internal content lets a publisher inject their own articles into their own widget alongside
RevContent demand.

- `getWidgetInternalContent` — `GET /stats/api/v1.0/widgets/{widget_id}/internal_content`
- `postWidgetInternalContentAdd` — `POST /stats/api/v1.0/widgets/{widget_id}/internal_content/add`
- `postWidgetInternalContentUpdate` — `POST /stats/api/v1.0/widgets/{widget_id}/internal_content/update`

Read before every write. The add operation has no idempotency key and no de-duplication, so a
retried add produces a duplicate content row rather than a no-op.

## Reporting hygiene

- Always set `date_from` and `date_to`. The defaults roll forward daily and will make two runs of
  the same job disagree.
- `aggregate=yes` returns a by-date rollup alongside the rows on the operations that support it —
  use it instead of summing pages client-side.
- No response carries a total count. Never compute "percent of total" from a single page.
- No rate limit is published and no `RateLimit-*` or `Retry-After` header is returned. Pace bulk
  pulls conservatively and treat a `500` as a signal to back off, since it is the only feedback the
  API gives.
