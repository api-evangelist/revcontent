---
name: Launch a RevContent campaign
description: Authenticate, resolve targeting reference codes, create a campaign (boost), attach creative content, and verify it is live.
api: openapi/revcontent-boosts-api-openapi.yml
operations: [getOauthAccess, getCountries, getRegions, getDevices, getOperatingSystems, getLanguages, getBrowsers, getDmas, postBoostAdd, postBoostContentAdd, getAllBoosts, postBoostsStatus]
generated: '2026-08-13'
method: generated
source: openapi/ (derived from https://api.revcontent.io/docs/stats/api_data.json)
---

# Launch a RevContent campaign

Base URL: `https://api.revcontent.io`

## 1. Get a token

`getOauthAccess` — `POST /oauth/token`, `Content-Type: application/x-www-form-urlencoded`,
body `grant_type=client_credentials&client_id=…&client_secret=…`.

Credentials come from Account Settings → **Stats API Credentials**, and only after a RevContent
account representative enables API access. The token is valid **24 hours** and there is no refresh
token — re-POST the credentials when it expires. Send it as `Authorization: Bearer {token}` with
`Content-type: application/json` on every subsequent call.

## 2. Resolve targeting codes BEFORE building the request

Never hand-write targeting values. Every targeting array must contain IDs from the Helpers
operations, and the API rejects unknown codes with a 400:

| Field you will set | Operation to read first |
|---|---|
| `country_codes` | `getCountries` |
| `region_codes` | `getRegions` |
| `device_targeting` | `getDevices` |
| `os_targeting` | `getOperatingSystems` |
| `language_targeting` | `getLanguages` |
| `browser_targeting` | `getBrowsers` |
| `dma_codes` | `getDmas` |

Two rules the contract states explicitly and that are easy to get wrong:

- `os_targeting` IDs must correspond to the `device_targeting` IDs you selected. Targeting OS IDs
  4/5, or 6/7/8, silently **resets targeting to All**.
- A `*_codes` array is mandatory whenever its matching `*_targeting` field is not `all`.

## 3. Create the campaign

`postBoostAdd` — `POST /stats/api/v1.0/boosts/add`, JSON body.

- `name` is the only required field.
- Use `default_bids` (`web`, `email`, `apple_news`), **not** `bid_amount` — the contract marks
  `bid_amount` deprecated, kept for backward compatibility.
- Minimum CPC bid is **0.01**. Anything lower is rejected.
- `budget` accepts `unlimited` or an amount. CSR accounts cannot have unlimited budgets.
- `pacing` defaults to `on` for limited budgets and is forced `off` for unlimited ones.
- `schedule` (hour array, e.g. `[15,16,17]`) is only available on unlimited-budget campaigns.
- `optimize` is `cpc` or `cpa`. If `cpa`, `conversion.id` is mandatory — create the pixel first with
  `postConversionAdd` (see the conversion-tracking skill).
- To act on a child account, set `sub_account_id`. Omit it to act on your own.

Read `boost_id` out of the response before doing anything else.

## 4. Attach creative content

`postBoostContentAdd` — `POST /stats/api/v1.0/boosts/{boost_id}/content/add`.
Repeat per creative. Correct later with `postBoostContentUpdate`.

## 5. Verify and activate

`getAllBoosts` — `GET /stats/api/v1.0/boosts?boost_id={boost_id}`. Check both status fields, they
are different things:

- `status` — system status: `active`, `balance_issue`, `budget_exhausted`, `inactive`, `disabled`,
  `archived`.
- `enabled` — user status: `active`, `inactive`.

A campaign showing `balance_issue` or `budget_exhausted` is not going to serve regardless of
`enabled`. Flip user status with `postBoostsStatus`.

## Error and retry rules

Errors come back as `{"success": false, "errors":[{"code","title","detail"}]}` with
`application/json` — **not** RFC 9457. Branch on `success` first. Only `errors[].detail` names the
offending field, and it is English prose.

**There is no idempotency key anywhere in this API.** `postBoostAdd` creates a new campaign on every
call. If a create times out, do **not** retry — call `getAllBoosts` with `created_at` set to just
before your attempt and check whether the campaign exists before trying again.

`401` means the 24-hour token expired; re-authenticate and replay. `500` is safe to retry on GETs
only.
