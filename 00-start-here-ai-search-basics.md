# 00 · Start Here: How AI Search Works

New to GEO and AEO? Read this first. It explains, in plain language, how AI assistants decide what to say and which sources to cite, so the rest of the kit makes sense.

⏱️ Reading time: ~12 minutes

---

## Contents

1. [What changed in search](#1-what-changed-in-search)
2. [SEO vs AEO vs GEO](#2-seo-vs-aeo-vs-geo)
3. [How an AI assistant builds an answer](#3-how-an-ai-assistant-builds-an-answer)
4. [Training data vs live retrieval](#4-training-data-vs-live-retrieval)
5. [How each platform finds sources](#5-how-each-platform-finds-sources)
6. [Mentions vs citations](#6-mentions-vs-citations)
7. [Why some pages get cited and others don't](#7-why-some-pages-get-cited-and-others-dont)
8. [Common myths](#8-common-myths)
9. [What this means for marketers](#9-what-this-means-for-marketers)

---

## 1. What changed in search

For 20+ years, search worked like this: a buyer typed a query, saw ten blue links, clicked a few, and made up their own mind.

Now many buyers ask an AI assistant instead, for example:

> "What is the best performance management software for a 200-lawyer firm?"

The assistant reads several sources, writes **one summarised answer**, and often names 3–5 options. The buyer may never see a list of links at all.

**What this means:**

- If your brand isn't named in that answer, you may not make the buyer's shortlist.
- The sources the AI cites get the credibility and the clicks.
- Ranking #1 on Google no longer guarantees you're in the AI answer, and some brands that rank lower get cited often.

## 2. SEO vs AEO vs GEO

| Term | Stands for | Goal | Example question it answers |
|---|---|---|---|
| **SEO** | Search Engine Optimization | Rank pages high in search results so people click | "How do I rank #1 for 'law firm HR software'?" |
| **AEO** | Answer Engine Optimization | Be the direct answer to a question (featured snippets, voice assistants, AI answers) | "How do I become the answer when someone asks 'what is upward review'?" |
| **GEO** | Generative Engine Optimization | Be mentioned and cited in answers written by generative AI (ChatGPT, Perplexity, Gemini, Copilot, AI Overviews) | "How do I get ChatGPT to recommend my product?" |

They overlap heavily. Good GEO is built on good SEO: AI tools that search the web usually pull from pages that are already indexed and trusted by search engines. Think of it as:

```
SEO  →  your pages can be found
AEO  →  your pages answer questions clearly
GEO  →  AI chooses to quote and recommend you
```

Other names you may see: **AI SEO**, **LLM SEO**, **AI search optimization**, **LLMO** (Large Language Model Optimization). They describe roughly the same thing.

## 3. How an AI assistant builds an answer

A simplified version of what happens when a buyer asks a question:

```
1. Buyer asks a question
        ↓
2. The assistant decides whether it needs fresh information
        ↓  (if yes)
3. It rewrites the question into one or more search queries
        ↓
4. It searches an index (Bing, Google or its own) and fetches pages
        ↓
5. It picks the most relevant passages from those pages
        ↓
6. It writes an answer, blending those passages with what it already "knows"
        ↓
7. It shows citations: links to some of the pages it used
```

This process is often called **RAG (Retrieval-Augmented Generation)**.

Three important details:

- **Step 3 (query rewriting):** the AI may search for several variations of the question, sometimes called **query fan-out**. A question about "best HR software for law firms" might trigger searches for "law firm HR software comparison", "HR software for legal industry reviews", and so on. Pages that answer many related variations have more chances to be picked.
- **Step 5 (passage selection):** AI usually picks **passages, not whole pages**. A clear, self-contained paragraph that directly answers the question is much more likely to be used than an answer buried in a long story.
- **Step 7 (citations):** not every source used is shown as a citation, and not every citation gets clicked. That's why you track both citations and referral traffic.

## 4. Training data vs live retrieval

AI answers come from two places:

| | Training data (model memory) | Live retrieval (web search) |
|---|---|---|
| **What it is** | What the model learned from huge amounts of text before its training cut-off | Pages fetched at the moment the question is asked |
| **How fresh** | Months or years old | Current |
| **Citations shown?** | Usually no | Usually yes |
| **How you influence it** | Slowly: be widely and consistently mentioned across the web over time | Faster: publish clear, crawlable pages that rank for the questions buyers ask |

**Practical takeaway:** you can influence live retrieval in weeks (new pages, better structure). Influencing model memory takes longer and depends on being mentioned in many credible places (publications, review sites, community discussions, associations).

## 5. How each platform finds sources

Platforms change often, so treat this as a general guide and re-check before big decisions.

| Platform | Where it usually gets live information | What this means for you |
|---|---|---|
| **ChatGPT (with search)** | Its own search crawler plus partner search indexes (Bing has been a major source) | Being indexed in **Bing** matters, not just Google. Allow OpenAI's search crawler (see `05-technical-setup.md`). |
| **Microsoft Copilot** | Bing's index | Bing SEO directly affects Copilot. **Bing Webmaster Tools** shows AI citation data. |
| **Perplexity** | Its own crawler plus web search | Always shows sources, so it's a good place to see who gets cited. Allow PerplexityBot. |
| **Google Gemini** | Google Search | Google SEO matters most. |
| **Google AI Overviews / AI Mode** | Google's index (crawled by normal Googlebot) | Strong Google rankings help. Blocking "Google-Extended" does **not** remove you from AI Overviews. |
| **Claude (with web search)** | Web search plus Anthropic's crawlers | Allow Claude's search crawlers if you want to be found there. |

## 6. Mentions vs citations

These two are different, and you should track both:

- **Mention:** the AI names your brand in its answer ("Options include Brand A, **Brand B** and Brand C").
- **Citation:** the AI links to a page as a source (a numbered footnote or a link card).

Four possible outcomes:

| | Cited | Not cited |
|---|---|---|
| **Mentioned** | 🟢 Best case: named and linked | 🟡 Named, but someone else's page is the source (often a review site or competitor list) |
| **Not mentioned** | 🟡 Your page is used as a source but you aren't recommended (common for educational content) | 🔴 Invisible |

The yellow cases are opportunities: in the first, improve your own pages so they get cited; in the second, make sure your page clearly connects the topic to your product.

## 7. Why some pages get cited and others don't

Patterns that show up again and again in testing:

**Pages that get cited usually:**

1. **Answer one clear question**, and answer it in the first 2–3 sentences.
2. **Match how buyers phrase things** ("Is X good for law firms?", "X vs Y", "best X for Y").
3. **Contain specific facts**: numbers, dates, names, prices, criteria.
4. **Include original data or research** that other sites don't have, so the AI has to cite you to use it.
5. **Are well structured**: descriptive headings, short paragraphs, bullet lists, tables, FAQs.
6. **Are balanced**: comparison pages that are fair to competitors are trusted more than pure sales pages.
7. **Are fresh**: a visible "last updated" date and current information.
8. **Are trusted elsewhere**: backlinks, publication mentions, author credentials.

**Pages that rarely get cited:**

- Vague marketing pages ("We empower teams to unlock potential")
- Content where the answer is hidden in images, PDFs, tabs or scripts
- Thin pages that repeat what 100 other pages say
- Pages blocked from crawlers, or not indexed in Bing/Google

## 8. Common myths

| Myth | Reality |
|---|---|
| "GEO replaces SEO." | GEO builds on SEO. If search engines can't find and trust your page, AI search usually can't either. |
| "You can pay to be recommended by ChatGPT." | Organic AI answers aren't sold the way search ads are. You earn visibility through content and reputation. |
| "Adding an llms.txt file gets you cited." | llms.txt is a proposed standard. Major platforms haven't confirmed relying on it, so it's optional and low priority. |
| "Keyword stuffing works on AI." | AI picks passages that answer the question well. Stuffing makes text worse, not better. |
| "One test tells you where you stand." | AI answers vary between sessions, users, locations and days. Test multiple times and track trends. |
| "Only big brands get cited." | Specialist pages with original data often beat big brands for niche buyer questions. |

## 9. What this means for marketers

A simple game plan:

1. **Find out where you stand** → run the audit (`01-audit-checklist.md`).
2. **Make sure you can be found** → fix crawling and indexing (`05-technical-setup.md`).
3. **Create content AI wants to quote** → follow the content playbook (`04-content-playbook.md`).
4. **Build reputation off your site** → reviews, publications, associations, communities.
5. **Measure and repeat monthly** → see `06-measurement-guide.md`.

Next: [`01-audit-checklist.md`](01-audit-checklist.md)
