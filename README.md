# Data Scraper API: What Does Each Request Really Cost, Which ScraperAPI Plan Covers Amazon and Google SERP, and When Is the Free Tier Enough? (Full Plan and Credit Table)

A data scraper API takes three jobs off your plate: rotating proxies, rendering JavaScript, and getting past CAPTCHAs. ScraperAPI does those three things and adds structured endpoints for Amazon, Google, and Walmart that hand back JSON instead of raw HTML. That package is worth paying for when you need tens of thousands of pages a month from sites that actively block crawlers. If you're pulling a few hundred rows from one site, or the site already offers an official API, you don't need it.

What follows is the money side: how ScraperAPI's credits translate into actual page counts, where the plan boundaries really sit, and what the documentation says about running dry mid-month that the homepage doesn't.

> **Quick take:** start on the free plan (1,000 credits a month, 5 concurrent connections, plus 5,000 credits for the first 7 days), then move to **Hobby** (100,000 credits, 20 threads) if your targets are Amazon or Walmart product pages at 5 credits each. Step up to **Business** only when you need country-level geotargeting or unlimited analytics history.
> 👉 [Check current ScraperAPI plans and credit allowances](https://www.scraperapi.com/pricing?fp_ref=coupons)

## The full plan lineup, side by side

ScraperAPI sells seven plans. The differences that affect your bill are credit volume, concurrent threads, geotargeting scope, and whether you can keep spending after credits run out.

| Plan | Monthly API credits | Concurrent threads | Geotargeting | When credits hit zero | Plan page |
| --- | --- | --- | --- | --- | --- |
| Hobby | 100,000 | 20 | US & EU | Auto-upgrade (opt-in) | [ Hobby details](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Startup | 1,000,000 | 50 | US & EU | Auto-upgrade (opt-in) | [ Startup details](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Business | 3,000,000 | 100 | Country-level | Auto-upgrade (opt-in) | [ Business details](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Scaling | 5,000,000 | 200 | Country-level | Pay-as-you-go or auto-upgrade | [ Scaling details](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Professional | 10,500,000 | 300 | Country-level | Pay-as-you-go or auto-upgrade | [ Professional details](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Advanced | 21,500,000 | 500 | Country-level | Pay-as-you-go only | [ Advanced details](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Enterprise | 22,000,000+ | 500+ | Country-level | Pay-as-you-go | [ Enterprise details](https://www.scraperapi.com/pricing?fp_ref=coupons) |

The free tier sits below Hobby: 1,000 credits a month with a maximum of 5 concurrent connections, and 5,000 credits available for the first 7 days after signup so you can test at a larger scale.

Three details from the second half of the pricing table: analytics history is capped at the last 30 days on Hobby and Startup and unlimited from Business up; credit rollover is unavailable on every plan; annual billing takes 10% off all self-serve tiers, with Enterprise quoted individually. Per-plan dollar prices live on the official pricing page and differ between monthly and annual billing. What doesn't change is the credit allowance and what each request burns, which is the part that decides your actual bill.

## Credits are not requests: the cost table that decides your bill

One credit buys one standard page fetch. Harder targets cost multiples, and the multiplier is set by the domain, not by your plan.

| Request type | Credits per request |
| --- | --- |
| Standard page | 1 |
| E-commerce (Amazon, Walmart, eBay) | 5 |
| SERP (Google, Bing, including subdomains) | 25 |
| Social (LinkedIn) | 30 |
| Bot-protection bypass (Cloudflare, Cloudflare Turnstile, DataDome, PerimeterX/HUMAN, Akamai) | +10 |
| JS rendering (`render=true`) | 10 |
| Premium proxy (`premium=true`) | 10 |
| Screenshot (`screenshot=true`) | 10 |
| Premium proxy + JS rendering | 25 |
| Ultra premium (`ultra_premium=true`) | 30 (paid plans only) |
| Ultra premium + JS rendering | 75 (paid plans only) |
| Geotargeting, sessions, device type, output format, auto parsing | No extra cost |

Run the numbers on Hobby's 100,000 credits and the plan looks very different depending on the job:

- Standard pages: 100,000 fetches.
- Amazon, Walmart or eBay product pages at 5 credits: 20,000 fetches.
- Amazon pages with `render=true` at 15 credits: about 6,666 fetches.
- Google or Bing SERPs at 25 credits: 4,000 searches.
- LinkedIn pages at 30 credits: roughly 3,333 fetches.

Business at 3,000,000 credits buys 600,000 e-commerce fetches or 120,000 SERPs. A rank-tracking job across 1,000 keywords checked daily burns 25,000 credits a day, about 750,000 a month, which means Startup is the realistic floor for that workload, not Hobby. Price monitoring on 5,000 ASINs once a day costs 25,000 credits a day too, because each ASIN is 5 credits.

Two tools keep this from becoming guesswork: the Domain Cost Estimator in the dashboard prices any URL before you send it, and every response returns its cost in the `sa-credit-cost` header. You can also set `max_cost` per scrape to cap a single request.

👉 [See what each plan's credit allowance gives you per month](https://www.scraperapi.com/pricing?fp_ref=coupons)

## What happens when you hit the limit

By default, scraping pauses until credits renew. That's the sentence to plan around, because the alternatives aren't available everywhere.

Auto-upgrade is opt-in on Hobby, Startup, Business, Scaling, and Professional, and it moves you to the next plan when credits run out. Pay-as-you-go is available on Scaling, Professional, Advanced, and Enterprise only, billed at a fixed per-credit rate up to a monthly spending cap you set. So Business has auto-upgrade but no pay-as-you-go, while Advanced has pay-as-you-go but no auto-upgrade. If you need both behaviors, you're on Scaling, Professional, or Enterprise.

Concurrency works differently from credits. Exceed your plan's thread limit and the API returns a 429 asking you to bring concurrency back within range. There's no surcharge, and the request is rejected rather than queued, so a burst of parallel jobs fails fast instead of quietly backing up.

Annual plans deliver the full year's credits upfront and let you use them on any timeline. If you burn through them early you can renew the same annual plan for a fresh allocation, or fall back on pay-as-you-go or auto-upgrade where your plan supports it. Rollover doesn't exist on any tier, so unused monthly credits expire at renewal.

Cancellation is self-serve from the dashboard and carries no charge. Refunds follow a 7-day no-questions-asked policy, which lines up neatly with the 7-day 5,000-credit trial window: you can run a realistic test at volume and walk away inside the same week.

👉 [Start on the free plan and upgrade only if the test justifies it](https://www.scraperapi.com/?fp_ref=coupons)

## Which plan fits Amazon, Google SERP, Walmart, or a no-code pipeline

Four product lines sit behind the same subscription, and matching your job to the right one matters more than the plan tier.

**Structured Data Endpoints (SDEs)** return JSON or CSV for 11 endpoints across three domains. Amazon has Search (submit a keyword list, get ranking products), Product (monitor ASINs for name, price, ratings), and Offers (spot competitor promotions). Google has Search, Shopping, News, and Jobs. Walmart has Product (by ID) and Search (by keyword). If your work lives inside those three domains, SDEs remove the parsing code you'd otherwise maintain, and the 5-credit e-commerce and 25-credit SERP rates are what you pay for that.

**The Scraping API** is the general-purpose entry point: point it at any public URL and it handles proxy rotation, CAPTCHA, and browser rendering. This is the fallback when your target isn't one of the 11 endpoints, and it's worth being explicit that no amount of plan upgrade turns a niche site into a structured endpoint. You'd get clean HTML and write your own extractor.

**Async Scraper** handles millions of requests asynchronously, which is the mode you want for nightly catalog sweeps rather than interactive lookups.

**DataPipeline** automates collection without code, aimed at teams that want scheduled output rather than an API client.

Geotargeting deserves its own note because it's the cleanest upgrade trigger in the lineup. Hobby and Startup cover US and EU only. Country-level targeting starts at Business, backed by a pool of more than 40 million proxies across 50+ countries. If your price comparison has to reflect what a shopper in Brazil or Japan sees, Business is the entry point and nothing below it works.

## Credits per request vs. price per record: two ways to bill a data scraper API

ScraperAPI bills in credits consumed per request, with multipliers by domain and by the features you switch on. Bright Data, the most direct alternative for pre-built scrapers, bills per delivered record starting at $0.70 per 1,000 records, and its documentation spells out three rules worth knowing regardless of which vendor you pick: records that fail because of bad input are still billable, a synchronous call that times out and returns a 202 continues asynchronously without being charged twice, and collected snapshots are retained for 30 days before deletion.

The two models produce different economics. A per-record price is easy to forecast when you know your row count, and it punishes malformed input rather than blocked requests. A per-request credit model is predictable when your targets are uniform, and it gets expensive exactly where ScraperAPI adds the most value: 25 credits for a Google SERP is 25 times the cost of a plain page, so a SERP-heavy workload needs a bigger plan than a page-heavy one with identical volume.

Before you commit to either, ask the vendor three questions in writing: does a request that returns a block or a CAPTCHA still consume credits; what happens to in-flight jobs when a plan's credits run out; and is there a per-request ceiling I can set to stop a runaway loop. ScraperAPI answers the third with `max_cost` and the second with its pause-by-default behavior. The first one is worth confirming with support for your specific targets.

## Who should not buy this

Skip it if any of these describe you.

You need a few hundred records a month from a single site. The free tier covers 1,000 credits, and a quick script with requests and BeautifulSoup covers the rest for $0.

Your target has an official API. Marketplace seller APIs, ad platform APIs, and most large social platforms offer sanctioned access with rate limits and terms that won't get your account closed.

You need one specific site outside the 11 structured endpoints and you have engineering time. The Scraping API still saves you the proxy pool and the CAPTCHA work, but you're paying for infrastructure rather than for parsed output, and self-hosting a small proxy rotation on a $20 VPS is a legitimate comparison at low volume.

You need country-level geotargeting on a small budget. The cheapest plan that offers it is Business, and there's no add-on to buy it separately.

## FAQ

**Do I need a credit card to start?**
ScraperAPI documents a free plan with 1,000 credits a month and 5 concurrent connections, plus 5,000 credits for the first 7 days. Card requirements aren't stated in the documentation, so confirm on the signup form before you enter details.

**Can it scrape Amazon and Google?**
Yes, through the Structured Data Endpoints: Amazon Search, Product, and Offers; Google Search, Shopping, News, and Jobs. Expect 5 credits per Amazon request and 25 per Google request, and remember that adding `render=true` to an Amazon request pushes it to 15.

**What format does the data come back in?**
SDEs return structured JSON or CSV. The general Scraping API returns page content you parse yourself.

**What happens if I run out of credits mid-month?**
Scraping pauses until renewal unless you've enabled auto-upgrade (Hobby through Professional) or pay-as-you-go (Scaling, Professional, Advanced, Enterprise). Nothing rolls over.

**Can I get a refund?**
Yes, within 7 days of purchase, no questions asked, via support. Cancellation is available anytime from the dashboard at no cost.

## Picking a plan without overbuying

Match the workload, not the credit number:

- Testing the API on real targets → free plan, 1,000 credits a month plus the 5,000-credit first week.
- Amazon, Walmart, or eBay product data up to about 20,000 fetches a month → Hobby.
- Daily SERP tracking or ASIN monitoring that runs into the hundreds of thousands of requests → Startup, because 25-credit SERPs and 5-credit product pages eat allowances fast.
- Country-level geotargeting, unlimited analytics history, or teams that need a landing spot between 1M and 5M credits → Business.
- Workloads that must keep running past the monthly allowance → Scaling or above, the tiers where pay-as-you-go exists.

Two things to confirm before you pay: the monthly spending cap on pay-as-you-go (it's a limit, not a prepayment, and service stops at the cap unless you raise it), and whether your specific targets bill at the standard rate or carry a bot-protection surcharge of 10 credits. A five-minute test with the Domain Cost Estimator answers the second one with your own URLs.

👉 [Compare ScraperAPI plans on the official pricing page](https://www.scraperapi.com/pricing?fp_ref=coupons)
