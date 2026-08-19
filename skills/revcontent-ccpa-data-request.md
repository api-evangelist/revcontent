---
name: Handle a RevContent CCPA data request
description: Submit a consumer data access or deletion request on behalf of a publisher and retrieve the resulting data.
api: openapi/revcontent-ccpa-api-openapi.yml
operations: [getOauthAccess, postSubmitCCPARequest, postUserData, postUsersData]
generated: '2026-08-13'
method: generated
source: openapi/ (derived from https://api.revcontent.io/docs/stats/api_data.json)
---

# Handle a RevContent CCPA data request

RevContent exposes a dedicated CCPA surface so publishers can honour consumer access and deletion
requests for data collected through RevContent widgets on their sites.

Docs: https://help.revcontent.com/knowledge/ccpa-data-request-data-deletion-request-api

## 1. Submit the request

`postSubmitCCPARequest` — `POST /stats/api/v1.0/data_requests/submit`

This one is different from the rest of the API:

- Content type is **`application/x-www-form-urlencoded`**, not JSON.
- The provider's own example calls it on `https://www.revcontent.com`, and passes the consumer's
  identity via a `Cookie: __ID=…` header — the request is made from the consumer's browser context,
  because the `__ID` cookie is how RevContent identifies the consumer.

Form fields: `domain`, `pub_id`, `request_id`, `email`, `delete_data`.

- `request_id` is **yours to generate and yours to keep**. It is the only handle you will have on
  this request afterwards — there is no list operation.
- `delete_data` distinguishes an access request from a deletion request.

## 2. Retrieve the data

- `postUserData` — `POST /stats/api/v1.0/data_requests/data`, form field `request_id`. One request.
- `postUsersData` — `POST /stats/api/v1.0/data_requests/multiple_data`. Several at once.

Both take a bearer token (unlike the submit call).

## Timing

Processing is asynchronous. Data fetch takes several hours; **deletion completes within 90 days**.
Poll `postUserData` rather than expecting a synchronous result, and do not treat an empty response
immediately after submission as "no data".

## Compliance notes for an agent operating this flow

- Persist every `request_id` with its submission timestamp, `domain` and `pub_id`. Losing it means
  losing the ability to evidence that the request was honoured.
- Do not log the retrieved payload into general application logs — it is consumer personal data
  returned specifically for a rights request.
- These endpoints are the mechanism, not the obligation. The statutory clock belongs to the
  publisher, and RevContent's 90-day deletion window sits inside it.
