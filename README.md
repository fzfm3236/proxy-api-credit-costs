# Proxy API: Which Kind Do You Need, What Does a Scraping Plan Really Cost, and Where Do Your Credits Go? (All ScraperAPI Plans, Per-Domain Credit Costs, Refund Terms)

If you want an endpoint that returns an IP that works, rotates it for you, and bills by usage, you want a proxy pool API. ScraperAPI sells that as part of a managed scraping API: one HTTP call with rotating proxies, headless rendering, and anti-bot handling on the far side. Paid plans start at **$49/month for 100,000 credits and 20 concurrent threads**, and there is a free tier you can test on today.

Two other products share the name, and most pages ranking for "proxy api" describe those instead. If your actual problem is attaching OAuth tokens to outbound calls, or routing traffic between microservices, the checks below will let you rule ScraperAPI out in about a minute, and that is a useful outcome too.

> **Quick pick.** Start free: 1,000 credits a month at 5 concurrent connections, plus 5,000 credits for your first 7 days. Once real volume shows up, Hobby at $49/month covers 100,000 credits and 20 threads. If you need country-level geotargeting outside the US and EU, the cheapest plan that includes it is Business at $299/month. 👉 [See every ScraperAPI plan and its credit allowance](https://www.scraperapi.com/pricing/?fp_ref=coupons)

## Three different products are called a proxy API

The phrase gets used for a pool you pull IPs from, for a credential injector, and for a gateway that forwards traffic. They solve unrelated problems, and mixing them up is how people end up buying bandwidth they never use.

**A proxy pool API** returns usable proxies or gives you a rotating outbound IP. Open-source projects in this category describe themselves in exactly those terms: proxifly's proxy-api hands back tested HTTPS and SOCKS5 proxies from more than 100 countries with automatic rotation and country-level targeting. Bright Data's version of the term is narrower still: its Proxy API is for creating, updating, and deleting proxy ports programmatically from your own code, with the IP pool sitting behind those ports.

**A credential pass-through** never touches your IP. Zapier's Proxy API takes an HTTP request from your code, looks up the stored connection for the target app, resolves whether that app wants OAuth, an API key in a header, an API key in a query string, or Basic auth, injects the right credentials, and forwards the request. The response streams back unchanged. It works across the 9,000+ apps Zapier connects to, and it exists so your code never holds a raw token.

**A gateway reverse proxy** is infrastructure. AWS API Gateway's HTTP proxy integration takes a client request and passes the method, headers, query string, path variables and payload to a backend, with no intervention from the gateway once the method is configured. You build it with a `{proxy+}` resource and a catch-all `ANY` method.

One question sorts you out: **do you need a different outbound IP, or do you need someone else to attach a token you don't want in your code?** Different IP means a proxy pool. Token injection means a pass-through. Neither one is a gateway, and a gateway will not rotate anything for you.

## Every ScraperAPI plan, with the numbers that differ

ScraperAPI prices in API credits rather than gigabytes or raw request counts, and the credit allowance and concurrency limit are the two numbers that actually separate the tiers. Annual billing takes exactly 10% off and is shown below as the effective monthly rate.

| Plan | Credits/month & concurrent threads | Monthly | Annual (per month) | Get started |
| --- | --- | --- | --- | --- |
| Free | 1,000 credits, 5 threads | $0 | — | [Start with the free tier](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Hobby | 100,000 credits, 20 threads | $49 | $44.10 | [Open Hobby](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Startup | 1,000,000 credits, 50 threads | $149 | $134.10 | [Open Startup](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Business | 3,000,000 credits, 100 threads | $299 | $269.10 | [Open Business](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Scaling (most popular) | 5,000,000 credits, 200 threads | $475 | $427.50 | [Open Scaling](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Professional | 10,500,000 credits, 300 threads | $975 | $877.50 | [Open Professional](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Advanced | 21,500,000 credits, 500 threads | $1,975 | $1,777.50 | [Open Advanced](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Enterprise | 22,000,000+ credits, 500+ threads | Custom | Custom | [Request an Enterprise quote](https://www.scraperapi.com/pricing/?fp_ref=coupons) |

The feature list does not change with price. Every paid tier includes JS rendering, premium residential and mobile IPs, anti-bot bypass, JSON autoparse, rotating proxy pools, custom headers, CAPTCHA handling, desktop and mobile user agents, automatic retries, unlimited bandwidth, and a 99.9% uptime guarantee. What you are buying with the higher tiers is credits, threads, and three secondary items:

- **Geotargeting:** US and EU only on Hobby and Startup. Country-level global targeting starts at Business.
- **Pay-as-you-go:** available on Scaling, Professional, Advanced, and Enterprise. Not on Hobby, Startup, or Business.
- **Support and history:** standard support on Hobby through Scaling, priority support on Professional, priority routing on Advanced, dedicated team and Slack on Enterprise. Analytics history runs 30 days on Hobby and Startup and unlimited from Business upward.

## 100,000 credits is not 100,000 pages

This is the part that makes plan comparisons go wrong. Credits are weighted per domain, and the multiplier applies per URL, not per plan, so upgrading never makes an individual request cheaper in credit terms.

A standard page costs 1 credit. Amazon costs 5. Google and Bing, including their subdomains, cost 25. LinkedIn costs 30. When ScraperAPI has to activate bypass logic for Cloudflare, Datadome, or PerimeterX, that adds 10 credits to the request, and the surcharge is applied automatically rather than on request. A `max_cost` parameter lets you cap any single scrape, and the Domain Cost Estimator in the dashboard gives the exact figure for a URL.

What Hobby's 100,000 credits actually buys:

| Target | Credits per request | Requests on 100,000 credits |
| --- | --- | --- |
| Standard page | 1 | 100,000 |
| Amazon | 5 | 20,000 |
| Google or Bing | 25 | 4,000 |
| Google or Bing with bot bypass | 35 | ~2,857 |
| LinkedIn | 30 | ~3,333 |

SERP monitoring is where this bites. A team tracking 5,000 keywords daily on Google across three markets is looking at roughly 450,000 credits a month, which puts them on Startup, not Hobby. Run your own domain mix through the estimator before you pick a tier. 👉 [Check the current Hobby allowance against your own request mix](https://www.scraperapi.com/pricing/?fp_ref=coupons)

## What happens when the credits run out

By default, scraping pauses until your credits renew, which is the safest behavior if you are not watching the dashboard. There are two escape hatches, and which one you get depends on the plan.

**Auto-upgrade** moves you to the next tier when credits hit zero. It is opt-in and available on Hobby, Startup, Business, Scaling, and Professional. This generally lands you at a better price per credit, but it also means a surprise charge if a crawler goes haywire.

**Pay-as-you-go** keeps you on the same plan at a fixed per-credit rate, up to a monthly spending cap you set yourself, and the service will not exceed that cap unless you change it. PAYG is available on Scaling, Professional, Advanced, and Enterprise. Hobby, Startup, and Business accounts get nothing extra: when concurrency exceeds the plan limit, you receive a 429 telling you to bring concurrency back in line. The rejected request is turned away rather than queued, and there is no charge for it.

Two billing details worth knowing before you commit. Credits reset at each renewal and unused credits do not carry forward. Annual plans work differently: you get the full year's credits upfront and can spend them on any timeline, and if you exhaust them early you can renew the same annual plan for a fresh allocation.

## Cancelling, refunds, and the risk of trying it

A 7-day, no-questions-asked refund applies if the service does not work out; you contact support and they process it. Cancellation is self-serve from the dashboard, and there is no cancellation fee. Combined with the free tier, that gives you a low-cost way to find out whether the success rate on your specific targets justifies the credit burn, which is the only question that matters before you scale up.

👉 [Compare plans with the 7-day refund window in mind](https://www.scraperapi.com/pricing/?fp_ref=coupons)

## The pricing unit trap: gigabytes versus credits

Proxy pricing does not compare across vendors unless you check the unit first. Bright Data's proxy network page, dated October 31, 2023, lists three tiers at **$4, $3, and $3 per GB** with monthly bills of **$499, $999, and $1,999**, covering 141 GB, 332 GB, and 798 GB respectively, and those figures came with a 50% promotional discount at the time. That page is roughly three years old as of this writing, so treat the numbers as a historical snapshot of structure rather than a current quote.

The structure is still useful. Gigabytes measure traffic volume. Credits measure requests weighted by how hard the target is. A 200 KB JSON response and a 4 MB HTML page can both cost one credit on a credit-based plan, and both would bill differently on a per-GB plan. Converting one to the other requires knowing your average payload size and your target mix, and most people estimating from a headline price per gigabyte get the answer wrong in one direction or the other.

If you do compare, compare the same workload: run 10,000 Google searches through each pricing model and see what the invoice would be. The per-unit number alone tells you nothing.

## Can you build or run this yourself?

Yes, and for validation work it is often the right call.

**Open-source route.** proxifly's proxy-api is a free REST API that returns tested HTTPS and SOCKS5 proxies from 100+ countries with automatic rotation and geo-targeting by country. You can grab a prebuilt app for your platform, or build from source with Node.js and Git: clone the repository, `cd proxy-api`, run `npm install`, then `npm start`. What the project page does not publish is a quota, a success-rate figure, an SLA, or a list of error codes and rate limits. That absence matters more than the feature list. Without documented limits you cannot tell whether a failed request is your bug or the pool's, and you have no contractual recourse when a target starts blocking.

**Self-built gateway route.** The AWS tutorial is a clean demonstration of how little code a reverse proxy needs. Create a REST API named `HTTPProxyAPI` with a Regional endpoint and IPv4, turn on the Proxy resource with the name `{proxy+}` and the resource path left at `/`, then configure the `ANY` method with integration type HTTP, HTTP proxy integration enabled, HTTP method ANY, and the endpoint URL pointing at the backend with `/{proxy}` appended. Deploy to a stage and you have an invoke URL.

The tutorial's own test results show the boundary. `GET /petstore/pets?type=fish` returns three records. `GET /petstore/pets/1` returns `200 OK` with the item. `GET /petstore` returns `404 Resource Not Found` with `Cannot GET /petstore`, because the backend never exposed that resource. AWS states plainly that the gateway does not mediate between client and backend, and the client has to parse the backend's output format itself. Swapping in a site protected by Cloudflare changes nothing about your proxy configuration and everything about whether the request succeeds.

That is where the money goes on a managed service: retry logic, bypass handling, and someone else owning the failure when a target changes its defenses. Validation runs are cheap to self-host. Production crawls at volume are not, once you count the engineering hours spent on retries and proxy health checks.

## Five questions to ask any proxy API vendor

The error-handling contract is the most under-documented part of this market, and it is where vendors differ most.

1. **What happens on a 401 mid-run?** Well-built pass-throughs refresh the credential and retry once automatically before returning an error, so your code does not need refresh logic. Ask whether the retry is free and whether it counts against your rate limit.
2. **What does a 429 mean and what should the client do?** Zapier's documentation tells clients to wait and retry with exponential backoff. ScraperAPI returns 429 when concurrency exceeds the plan limit and does not charge for the rejected request. A vendor that returns 429 with no guidance is telling you they have not thought about your retry loop.
3. **Are internal and private network addresses blocked?** SSRF protection should reject requests aimed at private IP ranges before forwarding. Zapier documents this explicitly; free and open-source proxy tools frequently do not mention it at all.
4. **Where do credentials live?** The good pattern is that your code references a connection ID, never a raw token, and that credentials are never logged in plain text. If a vendor's docs are silent on logging, assume the worst and test.
5. **Is there an uptime commitment, and what is excluded?** ScraperAPI publishes a 99.9% uptime guarantee across plans. Ask what counts against it, because a guarantee that excludes the targets you actually scrape is decoration.

Response streaming is a smaller item that shows up under load: a proxy that streams the upstream response back as it arrives keeps memory flat and cuts time-to-first-byte on large payloads, while one that buffers the whole body does neither.

## Picking a plan by situation

- **Evaluating feasibility, under a few thousand requests:** the free tier, 1,000 credits and 5 threads. Move on once you know your success rate.
- **Up to ~50,000 standard pages a month:** Hobby at $49. Divide by 5 for Amazon, by 25 for Google and Bing, before assuming this tier fits.
- **SERP or marketplace monitoring at scale:** Startup at $149 if you stay inside the US and EU, Business at $299 the moment you need country-level targeting elsewhere.
- **You expect occasional spikes but hate plan changes:** Scaling at $475 is the cheapest tier with pay-as-you-go and a spending cap you control.
- **300+ concurrent threads or 10M+ credits:** Professional at $975 and up. Below that, the extra threads go unused.

## Before you enter a card number

Confirm three things. First, the billing unit: credits, weighted by domain, so estimate with your real target mix rather than a page count. Second, the overflow behavior: 429 on Hobby, Startup, and Business, pay-as-you-go from Scaling upward, and auto-upgrade available on most tiers if you would rather never pause. Third, the exit: 7-day refund, self-serve cancellation, no cancellation fee, credits that reset rather than roll over.

If your workload is standard pages in the US and EU, Hobby covers most solo projects and the free tier covers the evaluation. If it is Google or Amazon at any volume, do the division first, because the credit multiplier decides your tier far more than your request count does.

👉 [Pick a ScraperAPI plan and start with 1,000 free credits](https://www.scraperapi.com/pricing/?fp_ref=coupons)
