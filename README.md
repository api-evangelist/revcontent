# RevContent

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

RevContent is a performance-driven native advertising and content recommendation network offering a REST API for managing widgets, campaigns (boosts), ad content, audience targeting, bidding, conversion pixels, sub accounts, and performance reporting. Publishers and advertisers access the platform through OAuth 2.0 client-credentials authenticated endpoints to programmatically control campaign settings, device, OS, browser, language and geo targeting, widget blacklisting, content delivery, and statistical reporting at scale. RevContent publishes its machine-readable contract as apiDoc rather than OpenAPI, at https://api.revcontent.io/docs/stats/api_data.json, covering 43 operations across eleven groups.

**Areas:** Native Advertising · Content Recommendation · Ad Network · Publisher Monetization · Programmatic Advertising · AdTech · Campaign Management · Audience Targeting · Conversion Tracking · Marketing

## RevContent on APIs.io

Everything profiled for RevContent is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/revcontent/](https://apis.io/providers/revcontent/)** — or go straight to one of the APIs or properties below.

### APIs (12)

- [RevContent Stats & Management API](https://apis.io/apis/revcontent/revcontent-stats-management-api/) — REST API providing programmatic access to RevContent's advertising platform for managing campaigns (boosts), widgets, content, targeting, widget…
- [RevContent Access API](https://apis.io/apis/revcontent/revcontent-access-api/) — OAuth 2.0 client-credentials token issuance and account reactivation.
- [RevContent CCPA API](https://apis.io/apis/revcontent/revcontent-ccpa-api/) — CCPA consumer data access and deletion requests for publishers.
- [RevContent Content API](https://apis.io/apis/revcontent/revcontent-content-api/) — Ad creatives attached to campaigns, and their per-widget performance.
- [RevContent Conversions API](https://apis.io/apis/revcontent/revcontent-conversions-api/) — Conversion pixel management used by CPA-optimized campaigns.
- [RevContent Helpers API](https://apis.io/apis/revcontent/revcontent-helpers-api/) — Reference lookups for browsers, countries, devices, DMAs, languages, operating systems and regions — the source of every valid targeting code.
- [RevContent Targeting API](https://apis.io/apis/revcontent/revcontent-targeting-api/) — Per-campaign widget targeting and widget-level bid overrides.
- [RevContent Widget Internal Content API](https://apis.io/apis/revcontent/revcontent-widget-internal-content-api/) — Publisher-owned content injected into that publisher's own widget.
- [RevContent Widget Optimizer API](https://apis.io/apis/revcontent/revcontent-widget-optimizer-api/) — Campaign-level widget blacklisting.
- [RevContent Campaigns API](https://apis.io/apis/revcontent/revcontent-campaigns-api/) — Create, update, list, archive and report on advertising campaigns (boosts).
- [RevContent Widget API](https://apis.io/apis/revcontent/revcontent-widget-api/) — Publisher widget inventory, geo statistics and Sub ID reporting.
- [RevContent Subaccounts API](https://apis.io/apis/revcontent/revcontent-subaccounts-api/) — Create, edit, list and enable/disable sub accounts under a parent account.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [revcontent-mcp.yml](https://apis.io/servers/revcontent/revcontent-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Revcontent Agentic Access](https://apis.io/agentic-access/revcontent/revcontent-agentic-access/)

#### JSON Schema (11)

The data models the API reads and writes.

- [AccessToken](https://apis.io/schemas/revcontent/access-token/)
- [Campaign](https://apis.io/schemas/revcontent/campaign/)
- [CampaignCreateRequest](https://apis.io/schemas/revcontent/campaign-create-request/)
- [CampaignSettingsRequest](https://apis.io/schemas/revcontent/campaign-settings-request/)
- [CCPADataRequest](https://apis.io/schemas/revcontent/ccpa-data-request/)
- [ContentItem](https://apis.io/schemas/revcontent/content-item/)
- [Conversion](https://apis.io/schemas/revcontent/conversion/)
- [Error](https://apis.io/schemas/revcontent/error/)
- [SubAccount](https://apis.io/schemas/revcontent/sub-account/)
- [Widget](https://apis.io/schemas/revcontent/widget/)
- [WidgetTarget](https://apis.io/schemas/revcontent/widget-target/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Revcontent Context](https://apis.io/jsonld/revcontent/revcontent-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Revcontent Vocabulary](https://apis.io/vocabularies/revcontent/revcontent-vocabulary/)

#### Examples (18)

Example requests and responses.

- [Access Token Response](https://apis.io/examples/revcontent/access-token-response/)
- [Campaign List Error Response](https://apis.io/examples/revcontent/campaign-list-error-response/)
- [Campaign List Response](https://apis.io/examples/revcontent/campaign-list-response/)
- [Campaign Performance Response](https://apis.io/examples/revcontent/campaign-performance-response/)
- [Campaign Settings Request](https://apis.io/examples/revcontent/campaign-settings-request/)
- [Campaign Widget Stats Response](https://apis.io/examples/revcontent/campaign-widget-stats-response/)
- [Ccpa Data Request](https://apis.io/examples/revcontent/ccpa-data-request/)
- [Ccpa Submit Request](https://apis.io/examples/revcontent/ccpa-submit-request/)
- [Content List Response](https://apis.io/examples/revcontent/content-list-response/)
- [Conversion List Response](https://apis.io/examples/revcontent/conversion-list-response/)
- [Helpers Countries Response](https://apis.io/examples/revcontent/helpers-countries-response/)
- [Helpers Devices Response](https://apis.io/examples/revcontent/helpers-devices-response/)
- [Helpers Operating Systems Response](https://apis.io/examples/revcontent/helpers-operating-systems-response/)
- [Sub Account List Response](https://apis.io/examples/revcontent/sub-account-list-response/)
- [Widget Blacklist Add Request](https://apis.io/examples/revcontent/widget-blacklist-add-request/)
- [Widget Blacklist Response](https://apis.io/examples/revcontent/widget-blacklist-response/)
- [Widget List Response](https://apis.io/examples/revcontent/widget-list-response/)
- [Widget Subid Stats Response](https://apis.io/examples/revcontent/widget-subid-stats-response/)

#### Collections (11)

Postman and Open Collection request collections.

- [RevContent Access API](https://apis.io/collections/revcontent/open-revcontent-access-api/)
- [RevContent Campaigns API](https://apis.io/collections/revcontent/open-revcontent-boosts-api/)
- [RevContent CCPA API](https://apis.io/collections/revcontent/open-revcontent-ccpa-api/)
- [RevContent Content API](https://apis.io/collections/revcontent/open-revcontent-content-api/)
- [RevContent Conversions API](https://apis.io/collections/revcontent/open-revcontent-conversions-api/)
- [RevContent Helpers API](https://apis.io/collections/revcontent/open-revcontent-helpers-api/)
- [RevContent Sub Accounts API](https://apis.io/collections/revcontent/open-revcontent-sub-accounts-api/)
- [RevContent Targeting API](https://apis.io/collections/revcontent/open-revcontent-targeting-api/)
- [RevContent Widget Internal Content API](https://apis.io/collections/revcontent/open-revcontent-widget-internal-content-api/)
- [RevContent Widget Optimizer API](https://apis.io/collections/revcontent/open-revcontent-widget-optimizer-api/)
- [RevContent Widget API](https://apis.io/collections/revcontent/open-revcontent-widgets-api/)

#### Overlays (11)

OpenAPI overlays, including conversational phrasing for each operation.

- [Revcontent Access Api Overlay](https://apis.io/overlays/revcontent/revcontent-access-api-overlay/)
- [Revcontent Boosts Api Overlay](https://apis.io/overlays/revcontent/revcontent-boosts-api-overlay/)
- [Revcontent Ccpa Api Overlay](https://apis.io/overlays/revcontent/revcontent-ccpa-api-overlay/)
- [Revcontent Content Api Overlay](https://apis.io/overlays/revcontent/revcontent-content-api-overlay/)
- [Revcontent Conversions Api Overlay](https://apis.io/overlays/revcontent/revcontent-conversions-api-overlay/)
- [Revcontent Helpers Api Overlay](https://apis.io/overlays/revcontent/revcontent-helpers-api-overlay/)
- [Revcontent Sub Accounts Api Overlay](https://apis.io/overlays/revcontent/revcontent-sub-accounts-api-overlay/)
- [Revcontent Targeting Api Overlay](https://apis.io/overlays/revcontent/revcontent-targeting-api-overlay/)
- [Revcontent Widget Internal Content Api Overlay](https://apis.io/overlays/revcontent/revcontent-widget-internal-content-api-overlay/)
- [Revcontent Widget Optimizer Api Overlay](https://apis.io/overlays/revcontent/revcontent-widget-optimizer-api-overlay/)
- [Revcontent Widgets Api Overlay](https://apis.io/overlays/revcontent/revcontent-widgets-api-overlay/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [RevContent — jsonschema rules](https://apis.io/rules/revcontent/revcontent-jsonschema-spectral-rules/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Revcontent Authentication](https://apis.io/security/revcontent/revcontent-authentication/)
- [Revcontent Domain Security](https://apis.io/security/revcontent/revcontent-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Revcontent Scopes](https://apis.io/scopes/revcontent/revcontent-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Revcontent Plans Pricing](https://apis.io/plans/revcontent/revcontent-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Revcontent Rate Limits](https://apis.io/rate-limits/revcontent/revcontent-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Revcontent Finops](https://apis.io/finops/revcontent/revcontent-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.revcontent.com)
- [Documentation](https://help.revcontent.com/knowledge/native-api)
- [Getting started](https://help.revcontent.com/knowledge/publisher-advertiser-api-requests)
- [API reference](https://api.revcontent.io/docs/stats/index.html)
- [Sign up](https://www.revcontent.com/registration)
- [Support](https://www.revcontent.com/resources/contact-us)
- [Blog](https://www.revcontent.com/resources/blog)
- [Security](https://www.revcontent.com/policy/security)
- [Compliance](https://www.revcontent.com/policy/security)
- [Privacy policy](https://www.revcontent.com/policy/privacy-policy)
- [GitHub](https://github.com/RevContent)

## API Evangelist rating

**Kin Score 44.0** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.4 |
| Contract quality | 25.1 |
| Contract governance | 41.7 |
| Operational transparency | 28.9 |
| Developer ergonomics | 66.1 |
| Access clarity | 31.6 |

**Agent readiness 31.8** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 35.3** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/revcontent/](https://apis.io/providers/revcontent/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for RevContent: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/revcontent/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
