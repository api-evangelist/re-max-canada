# RE/MAX Canada (re-max-canada)

RE/MAX Canada is the Canadian arm of RE/MAX, LLC, operating the remax.ca consumer portal in English and French and franchising RE/MAX brokerages across the country. Since RE/MAX Holdings closed its USD 235 million purchase of the RE/MAX INTEGRA North America regions on 2021-07-21, the Ontario-Atlantic and Western Canada regions are company-owned regions of RE/MAX, LLC, folded into RE/MAX Canada; Quebec is served separately and remax.ca robots.txt explicitly disallows /qc and /quebec. Its home market is Canada, and it sits in the value chain as a brokerage franchisor and consumer portal operator rather than as a data owner. Canadian residential listing content is cooperatively controlled by CREA and the member boards through REALTOR.ca and the Data Distribution Facility, so RE/MAX Canada displays MLS content it licenses rather than publishes; the remax.ca footer carries CREA's MLS trademark notice, and the site's home price estimates are supplied by Teranet Inc. under a personal-use-only licence that forbids commercial use, resale, external distribution and sublicensing even though Teranet's own inputs derive from public records collected by the Province of Ontario, the Province of Manitoba and the British Columbia Assessment Authority. Its API posture is recorded here honestly: there is no developer portal, no published API programme, no OpenAPI, Swagger, GraphQL or OData `$metadata` document, and no RESO Web API or Data Dictionary certification.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/re-max-canada/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/re-max-canada/refs/heads/main/apis.yml)

## Tags

- Real Estate
- Canada
- Brokerage
- Property Listings
- MLS
- RESO
- IDX
- PropTech
- Land Registry
- Valuation
- Rentals
- Franchising

## Timestamps

- **Created:** 2026-07-26
- **Modified:** 2026-07-26

## RESO Posture

**No RESO reference found.** RE/MAX Canada is not RESO-certified and does not appear in the RESO certification directory. A case-insensitive regex for `re ?/? ?max` across the full 416,233-byte [RESO Certification Status](https://www.reso.org/certificates/) document (HTTP 200, fetched 2026-07-26) returns zero matches across all 578 listed organizations. No Web API certification, no Data Dictionary certification, no UOI, no OData `$metadata`, and no Universal Property Identifier appears anywhere in its estate. The 11 apparent "reso" string matches on the remax.ca homepage are all false positives from "RESOURCES" and "Resort".

Canada *is* represented in the RESO directory — 30 Canadian entries were observed — but only at board, association and pooled-platform level: Information Technology Systems Ontario (ITSO, UOI M00000807, Passed Current), Pillar 9 (UOI M00000674, Passed Current), REALTORS® Association of Edmonton, Nova Scotia Association of REALTORS®, Vancouver Island and Victoria Real Estate Boards, and others. Only two of the thirty carry status "Certified Current"; Toronto Regional Real Estate Board and Greater Vancouver REALTORS® are both listed as **Uncertified**. CREA itself appears on the [RESO membership list](https://www.reso.org/membership/) as a Class F association member, not as a certified data provider.

## Access Gate

**`none-published`.** There is nothing for a developer to sign or join, because no programme exists — no developer portal, no API terms, no key request, no application flow, no pricing, no rate limits, no sandbox. `developer.remax.ca`, `developers.remax.ca` and `docs.remax.ca` return HTTP 403 but are **wildcard DNS artifacts** pointing at `customers.kvcore.com`, proven by the control probe `zzzznotreal.remax.ca` resolving identically. `api.remax.ca` is a real AWS load balancer running Kestrel that HTTP 301-redirects every probed path — `/swagger`, `/swagger/v1/swagger.json`, `/odata`, `/Reso`, `/RESO/odata/$metadata`, `/graphql`, `/listings` — straight back to `www.remax.ca`.

A developer who wants Canadian MLS listing data must go one layer up, to CREA's REALTOR.ca Data Distribution Facility (DDF®) or a member board / board technology provider — none of which RE/MAX Canada controls or resells. Going the other direction is expressly forbidden: the [remax.ca terms of use](https://www.remax.ca/terms-of-use) prohibit automated, electronic or high-volume means, including web crawlers, scripts and other automated devices, from accessing the services, and `robots.txt` disallows `/api/`, `/v2/` and `/feature-flags/` to all user agents.

## Open Data

**None.** The clearest illustration is Teranet. Section 4 of the terms of use governs the site's home price estimates, supplied by Teranet Inc. — operator of Ontario's privatised land registry. Those estimates may be used only for personal, non-business evaluation and expressly not for commercial purposes, sale, external distribution, or licensing or sublicensing, whether for a fee or not — while the same clause concedes that some or all of them may be based on public information collected by the Province of Ontario, the Province of Manitoba and the British Columbia Assessment Authority. Public record reaches the consumer only through a private intermediary, under a personal-use-only licence.

## APIs

### RE/MAX Canada Blog WordPress REST API

The only anonymously reachable, machine-readable API surface found anywhere in the RE/MAX Canada estate. `blog.remax.ca` is a WordPress VIP site (CNAME `remax-promotions.go-vip.net`) that serves the stock WordPress REST API at `/wp-json/` with no authentication. The discovery index returned HTTP 200 and 446,832 bytes on 2026-07-26, declaring 25 namespaces and 563 routes, and self-documents every route's methods and arguments. It must not be mistaken for a RE/MAX product API: it carries Canadian real estate news posts, pages, categories, tags, media and authors — no listings, no property records, no valuations, no RESO Data Dictionary fields. Most of the 563 routes belong to Jetpack, Akismet, cron-control, Yoast, Cloudinary and WordPress VIP plugins and require authentication; the anonymously readable surface is the `wp/v2` content namespace. RE/MAX Canada publishes no documentation for it — it is a default of the hosting platform. The identical surface is live on `join.remax.ca` and `franchise.remax.ca`.

- **Human URL:** [https://blog.remax.ca/](https://blog.remax.ca/)
- **Base URL:** `https://blog.remax.ca/wp-json`

#### Tags

- Blog
- Content
- WordPress
- Canada

#### Properties

- [Index](openapi/re-max-canada-blog-wp-json-index.json) — WordPress REST API discovery index, saved verbatim
- [Index](https://blog.remax.ca/wp-json/)
- [Authentication](https://blog.remax.ca/wp-admin/authorize-application.php) — WordPress application passwords
- [Blog](https://blog.remax.ca/feed/)

## Common Properties

- [Website](https://www.remax.ca/)
- [Website](https://www.remax.ca/fr/)
- [Blog](https://blog.remax.ca/)
- [BlogRSS](https://blog.remax.ca/feed/)
- [Website](https://franchise.remax.ca/)
- [Website](https://join.remax.ca/)
- [TermsOfService](https://www.remax.ca/terms-of-use)
- [Website](https://www.remax.com/)
- [LinkedIn](https://www.linkedin.com/company/remax-canada)

## Notes

The most revealing artifact in this profile is a split posture. `blog.remax.ca/robots.txt` explicitly **allows** GPTBot, OAI-SearchBot, ChatGPT-User, ClaudeBot, Claude-SearchBot, Claude-User, PerplexityBot, Perplexity-User, Google-Extended, CCBot and cohere-ai, with a blanket `User-agent: * / Disallow:` — while the terms of use governing the listings portal forbid crawlers, scripts and automated devices entirely. The content RE/MAX Canada owns is wide open to agents; the data it merely licenses is closed to everyone.

See `review.yml` for the full probe log, RESO evidence and access-gate analysis, and the sibling repo `all/re-max/` for RE/MAX Holdings (United States).
