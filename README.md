# bandwagonhost ecommerce sla: what the 99.99% uptime promise actually covers, current plan pricing, and which one fits your store

BandwagonHost's E-Commerce SLA plans are the only tier in the company's catalog with a contractual 99.99% monthly uptime commitment, hosted in a single Los Angeles datacenter (USCA_5 at Coresite LA2) and wired with three premium China routes: CN2 GIA, CMIN2 and China Unicom Premium. If uptime drops below that target in a calendar month, you're owed service credit on a fixed schedule, starting at 12 hours for as little as 4 minutes 32 seconds of downtime.

What most plan listings skip is how the guarantee actually works in practice: what counts as downtime, which exclusions quietly swallow real incidents (DDoS nullrouting is the big one), and how the billing cycles change what you effectively pay per month. Those details decide whether this line fits your store, so they take up most of this guide.

> **Quick take:** running a real store or a China-facing service? The 320G plan (8 vCPU, 16 GB RAM, 8 TB traffic) at $199.99/month is the sensible middle of the line, and the annual term brings it to $1,999.99, about $167 a month. Light-duty users can start at the 20G plan for $239.99/year. 👉 [See the full E-Commerce SLA lineup and current stock](https://bwh81.net/aff.php?aff=77528)

## What "E-Commerce SLA" actually is

E-Commerce SLA is a tier of KVM VPS plans that all live in the same building: USCA_5, Coresite LA2, in Los Angeles. Every plan in the tier pairs dedicated AMD EPYC cores with NVMe RAID-10 storage, and every one carries the 99.99% monthly uptime commitment backed by a written credit schedule.

The "E-Commerce" label undersells it a little. These plans work for anything that needs stable China connectivity plus a real uptime guarantee — cross-border stores, a TikTok live backend, an API service for users in China. The name is just the marketing hook.

One warning before anything else: the SLA applies to USCA_5 only. Other BandwagonHost datacenters, including other Los Angeles sites like USCA_6 and USCA_9, are not SLA-backed. If you accidentally order an E-Commerce (non-SLA) plan in a different location, the 99.99% promise doesn't follow you — you get the standard 99.9%.

## The 99.99% promise, with the fine print

The SLA is a service-credit commitment, not insurance for your revenue. When it triggers, BandwagonHost adds prepaid time to your account; it does not reimburse lost sales. Keep that distinction in mind for the math below.

Here's the math that makes the tier interesting. A 99.9% guarantee tolerates 43.2 minutes of downtime a month, which is an entire sales peak gone. 99.99% caps it at 4.32 minutes. If your store does $500 an hour in orders, the gap between those two numbers is roughly $360 in a single incident, before counting the customers who never come back.

So when is a VPS officially "down"? Two conditions have to hold for more than one continuous minute: the machine can't be reached from the public internet on the provider's standard checks (TCP, UDP, HTTP/HTTPS, ICMP), and the provider's own monitoring confirms the cause isn't an exclusion. One practical result: if a DDoS filters your ping but TCP traffic still flows, that isn't downtime. Annoying if you were staring at a monitoring dashboard, but it keeps false claims off the table on both sides.

The exclusion list matters more than the headline number:

- Planned maintenance announced 24 hours ahead, plus emergency maintenance under 10 minutes
- Anything caused by your own OS, scripts, firewall, SSH config or application stack
- Resource throttling after you pass plan limits
- DDoS attacks and the nullrouting that follows — no DDoS filtering is included on SLA plans
- Upstream network failures outside BandwagonHost's own equipment
- Unpaid bills, abuse suspensions, force majeure

> The DDoS line catches people. If your store is visible enough to attract attacks, a sustained one can get your IP nullrouted, and none of that time gets credited. You'd want your own mitigation layer sitting in front of the VPS.

When downtime does qualify, the credit scale is concrete:

| Downtime in one month | Credit |
| --- | --- |
| 4 min 32 sec – 10 min | 12 hours |
| 10 – 59 minutes | 3 days |
| 1 – 2 hours | 5 days |
| 2 – 4 hours | 10 days |
| 4 – 7 hours | 15 days |
| 7 hours or more | one full month |

Credits max out at one month of service per month and arrive as prepaid time, not cash. To file, open a support ticket within 90 days of the month the downtime happened and include the exact phrase "SLA Service Credit". A generic "my server was down" message won't trigger the review.

## Plans and pricing

The E-Commerce SLA line runs nine plans in total. The four below cover the smallest plan and three larger sizes, all currently in stock at USCA_5, and each has complete verified pricing across every billing cycle. The intermediate sizes sit on the same order page if you want to browse them. All prices in USD.

| Plan | vCPU / RAM | Storage | Traffic / Port | Price from | Order |
| --- | --- | --- | --- | --- | --- |
| 20G KVM (PID 164) | 2 / 1 GB | 20 GB | 1 TB / 2.5 Gbps | $65.89/quarter | [ Order](https://bwh81.net/aff.php?aff=77528) |
| 320G KVM (PID 168) | 8 / 16 GB | 320 GB | 8 TB / 5 Gbps | $199.99/month | [ Order](https://bwh81.net/aff.php?aff=77528) |
| 640G KVM (PID 169) | 10 / 32 GB | 640 GB | 10 TB / 10 Gbps | $369.99/month | [ Order](https://bwh81.net/aff.php?aff=77528) |
| 1280G HIBW 20T (PID 172) | 12 / 64 GB | 1.28 TB | 20 TB / 10 Gbps | $1,159.99/month | [ Order](https://bwh81.net/aff.php?aff=77528) |

The plan pages list RAM as 1,060 MB, 16,512 MB and 32,934 MB on the smaller three — those round to 1, 16 and 32 GB. Port speed caps your peak throughput, which is why the 20G tops out at 2.5 Gbps while the two larger plans get 10 Gbps.

Full cycle pricing:

| Plan | Monthly | Quarterly | Semi-annual | Annual |
| --- | --- | --- | --- | --- |
| 20G | — | $65.89 | $125.99 | $239.99 |
| 320G | $199.99 | $569.99 | $1,079.99 | $1,999.99 |
| 640G | $369.99 | $1,055.99 | $1,999.99 | $3,699.99 |
| 1280G HIBW 20T | $1,159.99 | $3,299.99 | $6,269.99 | $11,598.99 |

### What each billing cycle really costs

The annual term is where the pricing actually moves. On the 320G, paying monthly costs $199.99; the same plan annually works out to $166.67 a month, roughly 17% less. The 640G drops from $369.99 to about $308 a month, and the 1280G from $1,159.99 to about $967. The pattern holds across the whole line.

Two quirks worth knowing before checkout. First, the 20G plan has no monthly option at all — the shortest commitment is a quarter at $65.89, about $22 a month, and the annual term lands at exactly $20 a month. Second, the semi-annual prices don't always sit neatly between quarterly and annual, so if you're set on a long term, compare against the annual number before assuming a middle term saves more. 👉 [Check current cycle prices and stock](https://bwh81.net/aff.php?aff=77528)

## The routing is the real reason people pick this line

Specs like 8 TB of monthly traffic are easy to find elsewhere. What's rare at this price is the route stack: USCA_5 carries three premium China-direct paths, where most Los Angeles providers are lucky to offer one.

- **China Telecom CN2 GIA / CTGNet** (AS4809 / AS23764) — the telecom backbone that stays usable during the evening peak, when regular 163 transit degrades badly
- **China Mobile CMIN2** (AS58807) — Mobile's premium tier, a real step up from the default CMI routing most LA hosts get
- **China Unicom Premium** (AS10099) — Unicom's commercial-grade path rather than the shared budget route

The datacenter also peers directly with Apple, Google, Facebook, ByteDance, Tencent/ACE, Cloudflare and Akamai, and sits on the ANY2IX exchange. On the infrastructure side, USCA_5 runs dual redundant edge routers, core switches and top-of-rack switches, with multiple 100 Gbps uplinks and automatic failover.

One underrated panel feature: you can change your IP for free every two weeks from KiwiVM, BandwagonHost's control panel. No ticket, no waiting. If TikTok, WeChat or an ad network blacklists your IP, that's the difference between a two-minute fix and a support queue. 👉 [See USCA_5 plans and availability](https://bwh81.net/aff.php?aff=77528)

## Who shouldn't buy one

A few situations where the SLA premium doesn't pay off, and it's worth being honest about them.

If your site is likely to draw DDoS attacks, think twice. No filtering is included on these plans, nullroute time isn't credited, and a sustained attack could leave you offline with no compensation coming. You'd need to budget for separate mitigation.

If your workload is very light, the entry plan's 1 GB of RAM is fine for a small API, a proxy or a staging box, but a busy WooCommerce store with a database and a stack of plugins will feel cramped. That's a 320G job. And if neither China routing nor the uptime guarantee matters for your project, cheaper non-SLA plans exist on both BandwagonHost's own catalog and elsewhere — the premium here only makes sense if you'd actually use what it guarantees.

Finally, if you're counting on the SLA to cover lost revenue during an outage, it won't. Compensation is prepaid service time, capped at one month per month.

## Before you order: three checks

The order button opens the official checkout page, where you pick billing period, location and payment method. The mistakes here are all avoidable at that step.

1. Confirm the location reads **USCA_5 / Coresite LA2**. The SLA doesn't travel with you to other datacenters.
2. Choose the billing cycle with the prepay in mind: annual saves roughly 17% a month but locks in anywhere from $239.99 to $11,598.99 depending on the plan, and the 20G's minimum commitment is quarterly.
3. Match the transfer allowance (1–20 TB) and port speed (2.5–10 Gbps) to your real peak. Going over the limit triggers throttling, and throttling is excluded from the SLA.

## FAQ

**Does the 99.99% SLA apply to every BandwagonHost plan?**
No. It applies only to USCA_5 in Los Angeles. Other locations, including other LA sites like USCA_6 and USCA_9, carry the standard 99.9% commitment at most.

**What exactly counts as downtime under the SLA?**
Your VPS must be unreachable from the public internet on the provider's standard checks — TCP, UDP, HTTP/HTTPS or ICMP — for more than one continuous minute, with monitoring confirming the cause isn't an exclusion. Ping being filtered during a DDoS while TCP still works doesn't count.

**How do I claim an SLA credit?**
Open a support ticket within 90 days of the month the downtime happened and include the phrase "SLA Service Credit". Credits are added as prepaid time and max out at one month of service per month.

**Can I get a new IP if mine gets blacklisted?**
Yes. IP changes are free every two weeks through the KiwiVM panel, no support ticket needed.

## Picking between the plans

Load decides this more than anything else. A lightweight service or a test box that deserves a real guarantee fits the 20G at $20 a month on the annual term. A store or production API serving China traffic lands on the 320G, with the 640G as the step up when your database is doing heavy lifting. The 1280G HIBW 20T is for catalogs and traffic levels already paying for themselves many times over.

Whichever tier you land on, double-check the location at checkout and give the SLA exclusions a second read if DDoS exposure is part of your threat model. 👉 [View the full E-Commerce SLA lineup and current prices](https://bwh81.net/aff.php?aff=77528)
