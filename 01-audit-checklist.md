# AI Search Visibility Audit Checklist

Work through each section in order. Log findings in `citation-tracker.csv`.

## 1. Setup

- [ ] Write a one-line description of the product and its category
- [ ] List 3–5 direct competitors (plus 1–2 alternatives buyers also consider)
- [ ] Pick 15–30 buyer prompts from `02-prompt-library.md` and adapt them to the category
- [ ] Note the target market (country, industry) and add it to prompts where relevant
- [ ] Decide which platforms to test: ChatGPT, Perplexity, Gemini, Microsoft Copilot, Google AI Overviews
- [ ] Use clean or logged-out sessions where possible, and record the test date

## 2. Prompt testing

For every prompt on every platform, record:

- [ ] Is the brand **mentioned**? (Yes / No)
- [ ] **Position** in the answer (1st, 2nd, in a list, footnote only)
- [ ] **Sentiment and accuracy:** is the description correct and current?
- [ ] **Cited sources:** which URLs are linked or referenced
- [ ] Is a **brand-owned page** cited? Which one?
- [ ] Which **competitors** are mentioned, and in what order?

## 3. Citation analysis

- [ ] Calculate **mention rate**: prompts where the brand appears ÷ total prompts, per platform
- [ ] Calculate **citation share** for key prompts: brand citations ÷ all citations
- [ ] List the **top 10 cited domains** across all answers (competitors, review sites, Reddit, publications, directories)
- [ ] Flag prompts where competitors appear and the brand doesn't: these are the **priority gaps**
- [ ] Flag **inaccurate claims** about the brand (old pricing, missing features, wrong positioning)

## 4. On-site check

- [ ] Pages are crawlable: check robots.txt for AI crawlers (e.g. GPTBot, PerplexityBot, Bingbot, Google-Extended) and that content isn't hidden behind scripts
- [ ] Each key buyer question has a **dedicated page** that answers it in the first 2–3 sentences
- [ ] There are **comparison pages** ("Brand vs Competitor") and **buyer guides** ("Best X for Y")
- [ ] Content includes **original data**, research or specific numbers
- [ ] Headings are descriptive questions or statements, not vague labels
- [ ] **FAQ sections** exist on key pages, with FAQPage schema (see `faq-schema-example.json`)
- [ ] Organization and Product structured data are present
- [ ] Product facts (pricing model, integrations, who it's for) are stated plainly in text, not only in images
- [ ] Pages are fresh: dates are visible and content has been updated recently

## 5. Off-site check

- [ ] Brand is listed on the review and comparison sites that AI keeps citing in this category
- [ ] Brand is mentioned in relevant publications, association bulletins or industry reports
- [ ] There are credible backlinks to the key buyer pages
- [ ] Community discussions (Reddit, forums, LinkedIn) describe the brand accurately

## 6. Measurement setup

- [ ] **Bing Webmaster Tools → AI Performance** is verified and tracking citations
- [ ] **Google Search Console** is tracking the same buyer queries
- [ ] **GA4** shows referral traffic from AI platforms (chatgpt.com, perplexity.ai, copilot.microsoft.com, gemini.google.com) as a segment or channel group
- [ ] Engagement rate and conversions from AI referrals are compared with organic search

## 7. Prioritise

Score each fix on **impact** (how many priority gaps it closes) and **effort**. Start with:

1. Buyer questions where competitors are cited and the brand isn't
2. Inaccurate information about the brand
3. Missing comparison and buyer-guide pages
4. Technical blockers (crawlability, missing schema)
