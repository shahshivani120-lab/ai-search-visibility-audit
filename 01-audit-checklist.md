# 01 · AI Search Visibility Audit Checklist

A step-by-step audit with the **what, why and how** for every item. Log your findings in [`citation-tracker.csv`](citation-tracker.csv) and write them up with [`03-report-template.md`](03-report-template.md).

⏱️ Time needed: about **6–10 hours** for a first audit of one brand (25 prompts × 5 platforms). Later monthly re-tests take 2–3 hours.

---

## Contents

- [Phase 1 · Setup and scoping](#phase-1--setup-and-scoping)
- [Phase 2 · Prompt testing](#phase-2--prompt-testing)
- [Phase 3 · Citation and gap analysis](#phase-3--citation-and-gap-analysis)
- [Phase 4 · On-site audit](#phase-4--on-site-audit)
- [Phase 5 · Off-site audit](#phase-5--off-site-audit)
- [Phase 6 · Measurement setup](#phase-6--measurement-setup)
- [Phase 7 · Prioritise and plan](#phase-7--prioritise-and-plan)
- [Common mistakes](#common-mistakes)

---

## Phase 1 · Setup and scoping

### ☐ 1.1 Write a one-line brand description

**What:** One sentence in the form *"[Brand] is a [category] for [audience] that [main benefit]."*
**Why:** You'll compare this against how AI describes the brand. If AI's description differs, that's an accuracy problem to fix.
**How:** Take it from the homepage or ask the client. Example: *"Artemis is AI-native performance review software for law firms that makes partner and associate reviews faster and fairer."*

### ☐ 1.2 Define the category in buyer language

**What:** The words buyers actually use for the category (not internal jargon).
**Why:** AI answers buyer questions in buyer language. If your site calls it a "talent intelligence platform" and buyers ask for "performance review software", you won't match.
**How:** Check Google Search Console queries, competitor homepages, review-site category names and sales call notes. Write down 2–3 variants.

### ☐ 1.3 List competitors

**What:** 3–5 direct competitors plus 1–2 indirect alternatives (spreadsheets, a generic tool, an agency).
**Why:** You need to know who AI recommends instead of you.
**How:** Ask sales who they lose deals to, check review-site "alternatives" pages, and do a quick test prompt: *"What are the best [category] tools for [audience]?"* Note who appears.

### ☐ 1.4 Choose markets and audiences

**What:** Country, industry and company size you care about.
**Why:** AI answers change by location and by how specific the question is. "Best POS for restaurants" and "best POS for restaurants in Brisbane" can give completely different lists.
**How:** Pick the 1–2 markets that matter most and include them in some prompts.

### ☐ 1.5 Build the prompt set

**What:** 20–30 prompts covering all funnel stages.
**Why:** Testing only one or two prompts gives a misleading picture.
**How:** Use [`02-prompt-library.md`](02-prompt-library.md). A good mix:

| Funnel stage | Share of prompts | Example |
|---|---|---|
| Awareness | ~20% | "Why do law firm associates leave?" |
| Consideration | ~35% | "Best performance management software for law firms" |
| Comparison | ~25% | "Lattice vs Artemis for law firms" |
| Decision | ~10% | "How much does Artemis cost?" |
| Brand accuracy | ~10% | "What is Artemis?" |

Prioritise consideration and comparison prompts: they are closest to buying and usually show the biggest gaps.

### ☐ 1.6 Choose platforms

**What:** Which AI tools to test.
**Why:** Each platform uses different sources (see `00-start-here`), so results differ.
**How:** Standard set: **ChatGPT, Perplexity, Gemini, Microsoft Copilot, Google AI Overviews.** Add Claude or others if your audience uses them.

### ☐ 1.7 Prepare a clean testing setup

**What:** A testing environment that reduces personal bias.
**Why:** AI tools can personalise answers based on your history, memory and location.
**How:**

- Use a private/incognito browser window, logged out where the platform allows it.
- If logged in, turn off memory/personalisation or use a fresh test account.
- Make sure web search is turned on where there's a toggle (otherwise you only test model memory).
- Note your location (or VPN location) and the date in the tracker.
- Start a **new chat for every prompt**, so earlier questions don't influence later answers.

---

## Phase 2 · Prompt testing

### ☐ 2.1 Run each prompt on each platform

**How:** Paste the prompt exactly as written. Don't add follow-up questions for the main test.

### ☐ 2.2 Record whether the brand is mentioned

**What:** `Yes` / `No` in the `brand_mentioned` column.
**Tip:** Count variations (e.g. "SRA", "Survey Research Associates") as a mention.

### ☐ 2.3 Record the position

**What:** Where the brand appears: `1` (first recommendation), `2`, `3`…, `list` (in a list without ranking), or `footnote` (only in sources).
**Why:** Being named first matters more than being 7th in a list.

### ☐ 2.4 Check accuracy

**What:** `Yes` / `Partly` / `No` in `description_accurate`, with details in `notes`.
**Check for:** outdated pricing, missing or wrong features, wrong target audience, old company names, discontinued products, wrong locations.

### ☐ 2.5 Record sentiment

**What:** `Positive` / `Neutral` / `Negative`.
**Why:** Being mentioned with a warning ("some users report poor support") is a different problem from not being mentioned.

### ☐ 2.6 Record all cited URLs

**What:** Every source link shown, in `cited_urls` (separate with `;`).
**How:** On Perplexity, sources appear at the top and as numbered footnotes. On ChatGPT, click the "Sources" button. On Copilot and AI Overviews, check link cards and the expand/"show all" option.

### ☐ 2.7 Record whether a brand-owned page is cited

**What:** The exact URL in `brand_page_cited`.
**Why:** Tells you which of your pages AI already trusts, so you can build on them.

### ☐ 2.8 Record competitors

**What:** Every competitor named, in order, in `competitors_mentioned`.

### ☐ 2.9 Save full answers for key prompts

**What:** Copy the full answer text (or screenshot) for your 5–10 most important prompts.
**Why:** AI answers change often. Saved answers let you show before/after progress.

### ☐ 2.10 Repeat important prompts

**What:** Run your top 5 prompts 2–3 times (new chat each time).
**Why:** AI answers vary between runs. If the brand appears in 2 of 3 runs, record that (e.g. "mentioned 2/3").

---

## Phase 3 · Citation and gap analysis

### ☐ 3.1 Calculate mention rate per platform

**Formula:** `mention rate = prompts where brand is mentioned ÷ total prompts tested × 100`
**Example:** Mentioned in 6 of 25 ChatGPT prompts → 24% mention rate on ChatGPT.

### ☐ 3.2 Calculate mention rate per funnel stage

**Why:** Shows *where* in the buying journey you disappear. Many brands do fine on brand-name prompts but vanish on "best X for Y" prompts.

### ☐ 3.3 Calculate citation share for key prompts

**Formula:** `citation share = citations of your domain ÷ all citations for that prompt × 100`
**Example:** A prompt's answers cite 14 URLs in total; 12 are yours → 86% citation share.
**Tip:** Bing Webmaster Tools' AI Performance report can show citation share for real Copilot queries, which is more reliable than manual testing.

### ☐ 3.4 Calculate competitor share of voice

**Formula:** `share of voice = times brand X is mentioned ÷ total brand mentions across all answers × 100`
**Why:** Shows who "owns" the category in AI answers.

### ☐ 3.5 List the top cited domains

**How:** Copy all URLs from `cited_urls` into one column, reduce each to its domain, then count (a pivot table in Google Sheets or Excel works well).
**Group them by type:**

| Type | Examples | What to do |
|---|---|---|
| Competitor sites | competitor.com/blog | Study what format they use and create a better version |
| Review / comparison sites | G2, Capterra, industry directories | Get listed, collect reviews, keep profiles current |
| Publications | Industry magazines, association bulletins | PR, bylined articles, data stories |
| Communities | Reddit, Quora, LinkedIn posts, forums | Participate genuinely; encourage customers to share experiences |
| Your site | yourbrand.com | Strengthen and update these pages |

### ☐ 3.6 Identify priority gaps

**What:** Prompts where **competitors are mentioned and you aren't**.
**Why:** These are winnable: AI is already answering the question, just not with you.
**How:** Filter the tracker: `brand_mentioned = No` AND `competitors_mentioned` is not empty. Sort by funnel stage (comparison and consideration first).

### ☐ 3.7 List accuracy problems

**What:** Every wrong or outdated claim, where it appeared, and the likely source.
**How:** Check the cited URLs on those answers. Often it's an old review, an outdated directory listing or an old page on your own site.

---

## Phase 4 · On-site audit

Full technical how-tos are in [`05-technical-setup.md`](05-technical-setup.md) and content how-tos in [`04-content-playbook.md`](04-content-playbook.md).

### Crawling and indexing

- ☐ **4.1 robots.txt allows AI search crawlers** (OAI-SearchBot, PerplexityBot, Bingbot, Googlebot, Claude-SearchBot). Check `yourdomain.com/robots.txt`.
- ☐ **4.2 No firewall/CDN blocking**: some security tools (e.g. bot protection settings) block AI crawlers by default even when robots.txt allows them.
- ☐ **4.3 Key pages indexed in Google**: check with the URL Inspection tool in Google Search Console.
- ☐ **4.4 Key pages indexed in Bing**: check with URL Inspection in Bing Webmaster Tools. This matters for ChatGPT and Copilot.
- ☐ **4.5 XML sitemap submitted** to both Google Search Console and Bing Webmaster Tools.
- ☐ **4.6 IndexNow enabled** (optional) so Bing learns about new and updated pages quickly.
- ☐ **4.7 Content is in the HTML**: important text isn't only loaded by JavaScript, hidden in images, or locked in PDFs. Quick test: view the page source (Ctrl+U / Cmd+Option+U) and search for a key sentence.

### Content coverage

- ☐ **4.8 Each priority buyer question has a dedicated page** that answers it directly.
- ☐ **4.9 Comparison pages exist** ("[Brand] vs [Competitor]", "[Competitor] alternatives").
- ☐ **4.10 Buyer guides exist** ("Best [category] for [audience]", "How to choose [category]").
- ☐ **4.11 Original research or data exists** (surveys, benchmarks, anonymised product data).
- ☐ **4.12 Product facts are stated in plain text**: pricing model, integrations, who it's for, key features, locations served.

### Content structure

- ☐ **4.13 Direct answer in the first 2–3 sentences** of each key page.
- ☐ **4.14 Descriptive headings** (questions or clear statements, not "Overview" or "More info").
- ☐ **4.15 Short paragraphs** (2–4 sentences), lists and tables where they help.
- ☐ **4.16 FAQ section** on key pages, answering real follow-up questions.
- ☐ **4.17 Visible author and "last updated" date**.
- ☐ **4.18 Sources cited** for statistics and claims.

### Structured data (schema)

- ☐ **4.19 Organization schema** on the homepage (name, logo, URL, social profiles). See `organization-schema-example.json`.
- ☐ **4.20 FAQPage schema** where there are FAQs. See `faq-schema-example.json`.
- ☐ **4.21 Product / SoftwareApplication schema** on product pages, where relevant.
- ☐ **4.22 Article schema** with author and dates on blog posts.
- ☐ **4.23 Schema validates** in the Schema.org validator (validator.schema.org) and Google's Rich Results Test.

---

## Phase 5 · Off-site audit

- ☐ **5.1 Review and comparison sites:** is the brand listed on the sites AI cites in this category? Are profiles complete and current? How many recent reviews?
- ☐ **5.2 Publications:** has the brand been featured or quoted in industry publications in the last 12 months?
- ☐ **5.3 Associations and events:** member listings, speaker pages, bulletin articles (these are often highly trusted).
- ☐ **5.4 Communities:** search Reddit and relevant forums for the brand and category. Is the brand discussed? Accurately? Positively?
- ☐ **5.5 Wikipedia / Wikidata:** for larger brands, is there an accurate entry? (Don't create promotional entries; they get removed.)
- ☐ **5.6 Business listings:** Google Business Profile, Bing Places and local directories are accurate (especially for local businesses like restaurants).
- ☐ **5.7 Consistent facts everywhere:** the same name, description, founding date, locations and pricing model across all profiles. Inconsistency confuses AI.
- ☐ **5.8 Backlinks to key buyer pages:** check in Search Console's Links report or an SEO tool.

---

## Phase 6 · Measurement setup

Details in [`06-measurement-guide.md`](06-measurement-guide.md).

- ☐ **6.1 Bing Webmaster Tools verified**, AI Performance report checked (citations, cited pages, queries).
- ☐ **6.2 Google Search Console verified**, baseline recorded for clicks, impressions, CTR and position on key pages.
- ☐ **6.3 GA4 AI referral channel created** (regex provided in the measurement guide).
- ☐ **6.4 Baseline recorded**: AI referral sessions, engagement rate and conversions for the last 90 days.
- ☐ **6.5 Monthly re-test date set** in the calendar.

---

## Phase 7 · Prioritise and plan

### ☐ 7.1 Score each fix

Use **impact × confidence ÷ effort** (each on a 1–5 scale):

| Fix | Impact (1–5) | Confidence (1–5) | Effort (1–5) | Score |
|---|---|---|---|---|
| Create "Brand vs Competitor A" page | 5 | 4 | 2 | 10.0 |
| Allow OAI-SearchBot in robots.txt | 4 | 5 | 1 | 20.0 |
| Get listed on top-cited review site | 4 | 3 | 3 | 4.0 |

Higher score = do first.

### ☐ 7.2 Use this default priority order

1. **Technical blockers** (crawlers blocked, pages not indexed): quick and often high impact
2. **Accuracy problems** (AI says wrong things about you)
3. **Priority gaps** at comparison and consideration stage
4. **Missing content formats** (comparisons, buyer guides, research)
5. **Off-site reputation** (reviews, publications, communities)
6. **Nice-to-haves** (extra schema, llms.txt)

### ☐ 7.3 Turn it into a 90-day plan

- **Weeks 1–2:** technical fixes, accuracy fixes, measurement setup
- **Weeks 3–8:** publish 4–8 priority pages (comparisons, buyer guides, one research piece)
- **Weeks 4–12:** off-site work (listings, PR, community)
- **Monthly:** re-test the same prompts and report the trend

---

## Common mistakes

| Mistake | Why it's a problem | Fix |
|---|---|---|
| Testing while logged in with personal history | Personalised answers aren't what buyers see | Use clean sessions |
| Forgetting to turn on web search | You only test the model's memory | Check the search toggle |
| Testing only brand-name prompts | You'll look great but miss real buyer questions | Weight toward "best X for Y" and comparisons |
| One run per prompt | Answers vary | Repeat key prompts 2–3 times |
| Not recording the date | Can't compare months later | Always log the date |
| Only tracking mentions | Misses which sources AI trusts | Log cited URLs too |
| Ignoring Bing | ChatGPT and Copilot rely heavily on Bing | Verify Bing Webmaster Tools |

Next: [`02-prompt-library.md`](02-prompt-library.md)
