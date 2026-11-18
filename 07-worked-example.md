# 07 · Worked Example: A Mini Audit from Start to Finish

> **This is a fictional example** for learning purposes. "TableFlow" and its competitors are made-up brands, and all numbers are invented to show how the method works.

---

## The brand

**TableFlow** is a restaurant POS system for independent restaurants in Australia, with kiosk ordering and delivery-app integrations.

- **Competitors:** "OrderPoint", "KitchenOS", "TillMate"
- **Market:** Australia (focus: Brisbane and Sydney)
- **Platforms tested:** ChatGPT, Perplexity, Gemini, Copilot, Google AI Overviews
- **Prompts:** 20 (shown here: 5 of them)

---

## Step 1 · Prompt testing (sample rows)

| Prompt | Stage | ChatGPT | Perplexity | Gemini | Copilot | AI Overviews |
|---|---|---|---|---|---|---|
| Best POS system for restaurants in Australia | Consideration | ❌ | ❌ | ❌ | ❌ | ❌ |
| Restaurant POS with kiosk ordering | Consideration | ❌ | ✅ (4th) | ❌ | ❌ | ❌ |
| TableFlow vs OrderPoint | Comparison | ✅ | ✅ | ✅ | ✅ | ✅ |
| How much does a restaurant POS cost in Australia? | Decision | ❌ | ❌ | ❌ | ❌ | ❌ |
| What is TableFlow? | Accuracy | ✅ ⚠️ | ✅ | ✅ | ✅ ⚠️ | ✅ |

⚠️ = inaccurate: ChatGPT and Copilot said TableFlow "doesn't support delivery integrations" (it added them last year).

## Step 2 · Calculations

**Mention rate (all 20 prompts × 5 platforms = 100 answers):** TableFlow mentioned in 27 of 100 → **27%**

**By funnel stage:**

| Stage | Answers | TableFlow mentioned | Mention rate |
|---|---|---|---|
| Awareness | 20 | 0 | 0% |
| Consideration | 35 | 3 | 9% |
| Comparison | 25 | 14 | 56% |
| Decision | 10 | 2 | 20% |
| Accuracy | 10 | 8 | 80% |

**Share of voice (all brand mentions across answers):**

| Brand | Mentions | Share |
|---|---|---|
| OrderPoint | 61 | 41% |
| KitchenOS | 44 | 30% |
| TillMate | 16 | 11% |
| **TableFlow** | 27 | **18%** |

## Step 3 · Top cited domains

| Domain | Type | Times cited | TableFlow listed? |
|---|---|---|---|
| orderpoint.com.au/blog | Competitor | 19 | n/a |
| (a POS review site) | Review site | 15 | ❌ No |
| (a hospitality industry magazine) | Publication | 9 | ❌ No |
| reddit.com/r/restaurateur | Community | 7 | Rarely mentioned |
| tableflow.com.au | Brand | 6 | n/a |

## Step 4 · Diagnosis

1. **Strong on comparison, invisible on consideration.** People who already know TableFlow get good answers. People looking for a shortlist never hear of it. This is the costliest gap.
2. **OrderPoint wins with content.** Its blog has "best POS for cafés", "POS cost guide" and "kiosk ordering explained" pages, exactly the questions buyers ask.
3. **Missing from the top review site and the industry magazine**, which AI relies on.
4. **Outdated facts** about delivery integrations, traced to an old review article and an old TableFlow features page that was never updated.
5. **Technical:** robots.txt was fine, but the CDN's bot protection was blocking PerplexityBot (server logs showed `403` errors). TableFlow was also not verified in Bing Webmaster Tools.

## Step 5 · Prioritised fix list

| # | Fix | Impact | Effort | Score |
|---|---|---|---|---|
| 1 | Allow AI search crawlers in CDN settings; verify Bing Webmaster Tools; submit sitemap | 4 | 1 | High |
| 2 | Update features page with delivery integrations; ask review site to update old article | 4 | 1 | High |
| 3 | Publish "How much does a restaurant POS cost in Australia? (2026)" with a pricing table | 5 | 2 | High |
| 4 | Publish "Best POS systems for restaurants in Australia" buyer guide (fair, with disclosure) | 5 | 3 | High |
| 5 | Publish "Restaurant kiosk ordering: complete guide" | 4 | 2 | Medium |
| 6 | Create a profile on the top review site; ask 20 customers for reviews | 4 | 3 | Medium |
| 7 | Pitch original data ("What Brisbane diners order at kiosks") to the industry magazine | 4 | 4 | Medium |

## Step 6 · Results after 90 days (fictional)

| Metric | Baseline | Day 90 |
|---|---|---|
| Overall mention rate | 27% | 41% |
| Consideration mention rate | 9% | 31% |
| Share of voice | 18% | 26% |
| Accuracy issues | 2 | 0 |
| Copilot citations / month | 40 | 310 |
| AI referral sessions / month | 12 | 58 |

## What to learn from this example

- **Look at results by funnel stage.** The overall 27% hid a 9% consideration problem.
- **Cited domains show you the playbook.** Competitor blog formats and review sites told TableFlow exactly what to build.
- **Technical issues can hide behind a "fine" robots.txt.** Always check the CDN and server logs.
- **Accuracy fixes are quick wins.** Updating one page and one third-party article removed both errors.

Next: [`08-glossary-and-faq.md`](08-glossary-and-faq.md)
