# 06 · Measurement Guide: Tracking AI Search Visibility

How to measure AI visibility with free tools: Bing Webmaster Tools, Google Search Console, GA4 and a monthly manual prompt test.

> Menu names in these tools change from time to time. If a step doesn't match exactly, look for the closest equivalent.

---

## Contents

1. [What to measure](#1-what-to-measure)
2. [Bing Webmaster Tools: AI Performance](#2-bing-webmaster-tools-ai-performance)
3. [Google Search Console](#3-google-search-console)
4. [GA4: tracking AI referral traffic](#4-ga4-tracking-ai-referral-traffic)
5. [Manual prompt testing](#5-manual-prompt-testing)
6. [Monthly reporting dashboard](#6-monthly-reporting-dashboard)
7. [How to read the numbers](#7-how-to-read-the-numbers)
8. [Limitations to be honest about](#8-limitations-to-be-honest-about)

---

## 1. What to measure

AI visibility is measured in layers, from "seen" to "revenue":

| Layer | Question | Metric | Tool |
|---|---|---|---|
| 1. Presence | Does AI mention us? | Mention rate, share of voice | Manual prompt testing |
| 2. Citation | Does AI cite our pages? | Citations, citation share, cited pages | Bing Webmaster Tools (AI Performance), manual testing |
| 3. Search demand | Do our pages show up in classic search for the same questions? | Impressions, clicks, CTR, position | Google Search Console, Bing Webmaster Tools |
| 4. Traffic | Do people click through from AI? | AI referral sessions | GA4 |
| 5. Quality | Are those visitors engaged? | Engagement rate, pages per session | GA4 |
| 6. Business | Do they convert? | Leads, demos, sign-ups, revenue | GA4 + CRM |

Report at least one metric from each layer.

## 2. Bing Webmaster Tools: AI Performance

Bing Webmaster Tools includes an **AI Performance** report showing how often your site's pages are cited in **Microsoft Copilot and partner AI experiences**. It's one of the few free sources of real (not simulated) AI citation data.

### Setup

1. Go to bing.com/webmasters and sign in.
2. Add your site (or import it from Google Search Console).
3. Verify ownership if needed.
4. Submit your sitemap.
5. Open **AI Performance** from the menu (data may take some time to appear for new sites).

### What you'll see

- **Citations:** how many times your pages were cited, shown over time (daily chart)
- **Cited pages:** which URLs get cited most
- **Queries / grounding queries:** what users asked when your pages were cited
- **Citation share:** for some queries, what share of citations went to your site

### How to use it

- **Find your winning formats:** look at the most-cited pages. What type of content are they (comparisons, guides, research)? Create more of that.
- **Find new prompt ideas:** add the queries shown here to your prompt library.
- **Track progress:** record monthly citations and the top 10 cited pages.
- **Spot quick wins:** a page cited a lot but with weak content is worth improving.

### Real example of how this works

At a US B2B firm, tracking this report showed AI kept quoting comparison and research pages. Doubling down on those formats took citations from about 41 per day in August to about 93 per day in September, and the content reached 9.5K citations over 3 months, with an 86% citation share for the firm's top buyer query.

> Note: the report shows a limited history (around the last 3 months at the time of writing), so **export or record the numbers every month** to keep a long-term record.

## 3. Google Search Console

Google Search Console doesn't separate AI Overviews data into its own report, but it remains essential because strong Google visibility feeds Gemini and AI Overviews.

### What to track

1. **Performance → Search results**, last 3 months vs previous period:
   - Clicks, impressions, average CTR, average position
2. **Pages tab:** performance of your key buyer pages
3. **Queries tab:** filter with regex to find question-style queries:
   - Filter → Query → Custom (regex) → `^(what|how|why|which|is|are|can|does|best|vs)\b`
4. **Compare clicks vs impressions growth.** If clicks grow faster than impressions, your content is matching intent better.

### Example of what good looks like

| Metric | Before (Q2) | After (Q3) | Change |
|---|---|---|---|
| Clicks | 273 | 725 | +166% |
| Impressions | 71.4K | 84.8K | +19% |
| CTR | 0.4% | 0.9% | doubled |
| Avg. position | 8.5 | 6.8 | improved |

Clicks rising much faster than impressions shows the new pages matched what buyers were actually searching for.

## 4. GA4: tracking AI referral traffic

When someone clicks a link in an AI answer, the visit often shows up in GA4 as a **referral** from the AI platform's domain (for example `chatgpt.com` or `perplexity.ai`).

### Quick check (no setup)

1. GA4 → **Reports → Acquisition → Traffic acquisition**
2. Change the primary dimension to **Session source / medium**
3. Search the table for `chatgpt`, `perplexity`, `copilot`, `gemini`, `claude`

### Better: create a custom "AI Search" channel

This groups all AI platforms into one line in your reports.

1. GA4 → **Admin → Data display → Channel groups**
2. Click **Create new channel group** (or copy the default group)
3. **Add new channel** → name it `AI Search`
4. Condition: **Source** → **matches regex** → paste:

```
.*(chatgpt\.com|chat\.openai\.com|openai\.com|perplexity\.ai|copilot\.microsoft\.com|copilot\.com|gemini\.google\.com|bard\.google\.com|claude\.ai|edgeservices\.bing\.com|you\.com|meta\.ai|deepseek\.com|phind\.com).*
```

5. **Important:** drag the `AI Search` channel **above "Referral"** in the list. GA4 assigns traffic to the first matching channel, so if Referral is above it, AI traffic will be counted as normal referral.
6. Save. The new channel group applies to historical data too.
7. In reports, switch the dimension to your new channel group.

### What to look at

| Metric | Why it matters |
|---|---|
| Sessions from AI Search | Volume of AI-driven visits |
| Engagement rate | AI visitors often arrive with a specific question; compare with Organic Search |
| Average engagement time | Depth of interest |
| Landing pages | Which pages AI sends people to |
| Key events / conversions | Business impact |

**Real example:** at one B2B firm, ChatGPT referrals had a **34% engagement rate vs 19% for Google organic**, small volume but much higher intent.

### Optional: Explorations report

1. GA4 → **Explore → Free form**
2. Dimensions: Session source, Landing page
3. Metrics: Sessions, Engaged sessions, Engagement rate, Key events
4. Filter: Session source matches regex (use the regex above)

### Limitations

- Some AI traffic arrives with **no referrer** and shows up as "Direct". Real AI traffic is likely higher than GA4 shows.
- Google AI Overviews and AI Mode clicks are generally counted as normal Google organic traffic, not separately.
- Mobile apps may not pass referrer information.

## 5. Manual prompt testing

The only way to see mention rates across all platforms. Use `02-prompt-library.md` and `citation-tracker.csv`.

**Monthly routine (2–3 hours):**

1. Run the same 20–30 prompts on the same platforms, in clean sessions.
2. Fill in a new set of rows in the tracker with the new date.
3. Calculate mention rate per platform and per funnel stage.
4. Compare with last month.
5. Save screenshots for the 5 most important prompts.

## 6. Monthly reporting dashboard

A simple one-page monthly scorecard:

| Metric | Last month | This month | Change | Source |
|---|---|---|---|---|
| Overall AI mention rate | | | | Manual testing |
| Consideration-stage mention rate | | | | Manual testing |
| Share of voice vs top competitor | | | | Manual testing |
| Copilot/partner AI citations | | | | Bing AI Performance |
| Pages cited per day (avg.) | | | | Bing AI Performance |
| Google clicks (key pages) | | | | Search Console |
| Google impressions (key pages) | | | | Search Console |
| AI referral sessions | | | | GA4 |
| AI referral engagement rate | | | | GA4 |
| Leads from AI referrals | | | | GA4 / CRM |

**Tip:** build this in Looker Studio by connecting Search Console and GA4, and add the manual and Bing numbers from a Google Sheet.

## 7. How to read the numbers

| What you see | What it likely means | What to do |
|---|---|---|
| Citations up, mentions flat | AI uses your content as a source but doesn't recommend you | Connect educational pages more clearly to your product; add comparison pages |
| Mentions up, citations flat | AI knows your brand from other sources (reviews, press) | Strengthen your own pages so they get cited too |
| Impressions up, clicks flat | Visible but not compelling, or AI answers satisfy the question | Improve titles; add original data people want to click for |
| AI referrals low but engagement high | Small but high-intent channel | Make sure landing pages convert (clear CTA, demo, pricing) |
| Big drop in citations | Possible technical issue or competitor content | Check robots.txt, CDN, indexing; re-test prompts |

## 8. Limitations to be honest about

When reporting to clients or leadership, be upfront:

- **AI answers vary** by session, location, wording and over time. Manual tests are samples, not exact measurements.
- **No tool shows everything.** Bing covers Copilot and partners; other platforms don't publish citation data for site owners.
- **Attribution is incomplete.** Some AI-influenced visits show as direct or branded search.
- **Trends matter more than single numbers.** Report direction over 3+ months.

Next: [`07-worked-example.md`](07-worked-example.md)
