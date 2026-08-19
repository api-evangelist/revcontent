---
name: Optimize RevContent campaign spend by widget
description: Read campaign and per-widget performance, set widget-level bid overrides, and blacklist widgets that do not convert.
api: openapi/revcontent-targeting-api-openapi.yml
operations: [getOauthAccess, getBoostPerformance, getWidgetStats, getBoostWidgets, postBoostWidgets, getTargetsOptimizerWidgets, postTargetsWidgetsOptimizerAdd, postTargetsWidgetsOptimizerRemove]
generated: '2026-08-13'
method: generated
source: openapi/ (derived from https://api.revcontent.io/docs/stats/api_data.json)
---

# Optimize RevContent campaign spend by widget

This is the core money loop: RevContent buys traffic across many publisher widgets, and the only
lever an advertiser has is per-widget bidding and exclusion.

Authenticate first — see the launch-campaign skill (`getOauthAccess`, 24-hour bearer token).

## 1. Measure

- `getBoostPerformance` — `GET /stats/api/v1.0/boosts/performance`. Campaign-level spend, clicks,
  impressions and cost per conversion.
- `getWidgetStats` — `GET /stats/api/v1.0/boosts/{boost_id}/widgets/stats`. The per-widget breakdown
  for one campaign. **This is the table you optimize against.**

Both take `date_from` / `date_to` in `Y-m-d`. If you omit them you get *first of the current month →
today*, which silently mixes a partial current month into your comparison — always set them
explicitly. Pass `aggregate=yes` when you want the by-date rollup alongside the rows.

Paging is `limit` (default 100, max 1000) + `offset`. There is no total count and no cursor: keep
requesting until a page returns fewer rows than `limit`. Sort order is not documented, so for a
stable snapshot pull all pages inside one date window rather than paging slowly over a live account.

## 2. Re-bid the widgets worth keeping

- `getBoostWidgets` — `GET /stats/api/v1.0/boosts/{boost_id}/widgets`. Current targets, their
  `enabled` state and their bid overrides, with stats for the window.
- `postBoostWidgets` — `POST /stats/api/v1.0/boosts/{boost_id}/widgets`. Write the overrides back.

Bid floor is **0.01**; the API validates widget-target bids the same way it validates campaign bids
(changelog 2021-09-13). A value below the floor fails the whole request.

## 3. Blacklist the widgets that never convert

The widget optimizer is a separate surface from targeting — a widget can be enabled as a target and
still be blacklisted.

- `getTargetsOptimizerWidgets` — `GET /stats/api/v1.0/boosts/{boost_id}/targets/blacklist/widgets`.
- `postTargetsWidgetsOptimizerAdd` — `POST /stats/api/v1.0/boosts/{boost_id}/targets/blacklist/widgets/add`,
  body `{"id": "32,35,57"}` (comma-separated widget IDs in a single string, as the provider's own
  example shows).
- `postTargetsWidgetsOptimizerRemove` — the inverse, same body shape.

Always `getTargetsOptimizerWidgets` before and after a write: there is no idempotency key, and the
add/remove operations do not return the resulting list.

## Guardrails

- **Bulk updates are dangerous.** RevContent added an explicit safety parameter in 2021 precisely
  because a bulk campaign update could otherwise hit every campaign on the account. Never issue a
  bulk write without scoping it.
- **`sub_account_id` is not enforced by the token.** One client-credentials token can act across
  every sub account. If you are operating on behalf of a child account, set `sub_account_id` on
  every call in the loop, not just the first.
- Retries on `postBoostWidgets` and the blacklist writes are not idempotent. On a timeout, re-read
  with the matching GET and compare before re-sending.
