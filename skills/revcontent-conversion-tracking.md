---
name: Set up RevContent CPA conversion tracking
description: Create a conversion pixel, bind it to a campaign optimizing for CPA, and read cost-per-conversion back out.
api: openapi/revcontent-conversions-api-openapi.yml
operations: [getOauthAccess, getConversions, postConversionAdd, postConversionEdit, postConversionDelete, postBoostSettings, getBoostPerformance, getWidgetStats]
generated: '2026-08-13'
method: generated
source: openapi/ (derived from https://api.revcontent.io/docs/stats/api_data.json)
---

# Set up RevContent CPA conversion tracking

CPA optimization only works if a conversion pixel exists **before** the campaign is switched to
`optimize=cpa`. Do it in this order.

Authenticate first (`getOauthAccess`, 24-hour bearer token).

## 1. Inventory existing pixels

`getConversions` — `GET /stats/api/v1.0/conversions`. Check whether the pixel you need already
exists before creating another; there is no uniqueness constraint and no idempotency key, so it is
easy to accumulate duplicates.

## 2. Create the pixel

`postConversionAdd` — `POST /stats/api/v1.0/conversions/add`. Capture the returned conversion id.

## 3. Bind it to the campaign

`postBoostSettings` — `POST /stats/api/v1.0/boosts/{boost_id}/settings` with:

```json
{ "optimize": "cpa", "conversion": { "id": "<conversion id>" } }
```

`conversion.id` is **mandatory whenever `optimize` is `cpa`**. The body also exposes
`conversion.delete` to unbind. Note that `postBoostSettings` is a partial update — the provider's own
example sends only `{"name": "My Renamed Campaign"}` — so send just the fields you are changing.

`sub_account_id` goes on the query string here, not in the body.

## 4. Measure

Cost per conversion was added across the reporting surface on 2021-07-06 and is available on:

- `getBoostPerformance` — campaign level
- `getWidgetStats` — per widget within a campaign
- `getContentWidgetStats` — a single creative across widgets

Use the same `date_from` / `date_to` window on all three or the numbers will not reconcile.

## 5. Maintain

- `postConversionEdit` — `POST /stats/api/v1.0/conversions/{conversion_id}/update`
- `postConversionDelete` — `POST /stats/api/v1.0/conversions/{conversion_id}/delete`

**Deleting a pixel that a CPA campaign is bound to will break that campaign's optimization.** There
is no dependency check in the API and no warning in the response. Call `getAllBoosts` and inspect
which campaigns reference the conversion id before deleting it.

## Errors

Vendor envelope `{"success": false, "errors":[…]}`, `application/json`. `errors[].code` just mirrors
the HTTP status, so distinguish failure modes from `errors[].detail` prose. No idempotency key: a
timed-out `postConversionAdd` must be resolved by re-reading `getConversions`, never by retrying.
