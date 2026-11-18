# 05 · Technical Setup for AI Search

The technical foundations that let AI assistants find, read and trust your pages. Written for marketers: you don't need to code, but you may need to send some of these to a developer.

> ⚠️ Crawler names and platform behaviour change. Check each company's official documentation before making changes to a live site.

---

## Contents

1. [How AI crawlers work](#1-how-ai-crawlers-work)
2. [Common AI crawlers](#2-common-ai-crawlers)
3. [Training crawlers vs search crawlers](#3-training-crawlers-vs-search-crawlers)
4. [robots.txt: what it is and how to edit it](#4-robotstxt-what-it-is-and-how-to-edit-it)
5. [Firewalls and CDNs](#5-firewalls-and-cdns)
6. [Indexing in Google and Bing](#6-indexing-in-google-and-bing)
7. [IndexNow](#7-indexnow)
8. [Making content readable](#8-making-content-readable)
9. [Structured data (schema)](#9-structured-data-schema)
10. [llms.txt](#10-llmstxt)
11. [Technical checklist](#11-technical-checklist)

---

## 1. How AI crawlers work

A **crawler** (also called a bot or spider) is a program that visits web pages and reads them. Search engines like Google and Bing have used crawlers for decades. AI companies now run their own crawlers too.

Each crawler identifies itself with a name called a **user agent**. Your website can tell specific crawlers what they may or may not visit, using a file called `robots.txt`.

## 2. Common AI crawlers

| Company | User agent | What it's for |
|---|---|---|
| OpenAI | `OAI-SearchBot` | Finding pages to show in ChatGPT search results |
| OpenAI | `ChatGPT-User` | Visiting a page when a ChatGPT user asks it to |
| OpenAI | `GPTBot` | Collecting content that may be used to train models |
| Perplexity | `PerplexityBot` | Indexing pages for Perplexity answers |
| Perplexity | `Perplexity-User` | Visiting pages on behalf of a user's question |
| Anthropic | `Claude-SearchBot` | Indexing for Claude's search results |
| Anthropic | `Claude-User` | Visiting pages on behalf of a Claude user |
| Anthropic | `ClaudeBot` | Collecting content that may be used for training |
| Microsoft | `Bingbot` | Bing search, which also powers Copilot and contributes to other AI tools |
| Google | `Googlebot` | Google Search, including AI Overviews and AI Mode |
| Google | `Google-Extended` | A control token (not a separate crawler) for whether content is used for Gemini models; it does not affect Google Search or AI Overviews |
| Apple | `Applebot-Extended` | A control for whether content is used in Apple's AI models |
| Common Crawl | `CCBot` | Open web archive that many AI models have been trained on |

## 3. Training crawlers vs search crawlers

This is the key decision:

- **Search / user crawlers** (OAI-SearchBot, ChatGPT-User, PerplexityBot, Claude-SearchBot, Bingbot, Googlebot) help your pages **appear and be cited** in AI answers. **For visibility, allow them.**
- **Training crawlers** (GPTBot, ClaudeBot, CCBot, Google-Extended) collect content for **training future models**. Allowing them may help the model "know" your brand long term; blocking them protects your content from being used for training. This is a business choice.

A common setup for brands that want visibility: **allow search crawlers, and decide on training crawlers based on company policy.**

## 4. robots.txt: what it is and how to edit it

### What it is

A plain text file at `https://yourdomain.com/robots.txt` that tells crawlers which parts of the site they may visit. Open yours in a browser to see it.

### How it's written

```
User-agent: [crawler name]
Allow: [path]
Disallow: [path]
```

- `User-agent: *` means "all crawlers".
- `Disallow: /` means "nothing on this site".
- `Disallow:` (empty) or `Allow: /` means "everything".
- More specific rules for a named crawler override the `*` rules for that crawler.

### Example: allow AI search, allow training

See [`robots-txt-example.txt`](robots-txt-example.txt) for a full commented example.

```
User-agent: *
Allow: /
Disallow: /admin/

Sitemap: https://yourdomain.com/sitemap.xml
```

### Example: allow AI search, block AI training

```
User-agent: *
Allow: /
Disallow: /admin/

User-agent: GPTBot
Disallow: /

User-agent: ClaudeBot
Disallow: /

User-agent: CCBot
Disallow: /

User-agent: Google-Extended
Disallow: /

Sitemap: https://yourdomain.com/sitemap.xml
```

### Common mistakes

| Mistake | Result |
|---|---|
| `User-agent: *` + `Disallow: /` left over from a staging site | Blocks everyone, including Google |
| Blocking `OAI-SearchBot` when you meant to block only training | You disappear from ChatGPT search |
| Typos in crawler names | The rule is silently ignored |
| Forgetting the sitemap line | Crawlers find new pages more slowly |

### How to edit it on common platforms

- **Webflow:** Site settings → SEO → robots.txt
- **WordPress:** an SEO plugin (e.g. Yoast or Rank Math) → file editor, or edit the file on the server
- **Shopify:** edit the `robots.txt.liquid` theme template
- **Wix / Squarespace:** check the SEO settings; some platforms limit custom robots.txt
- **Custom sites:** ask your developer to edit the file in the site root

## 5. Firewalls and CDNs

Even with a perfect robots.txt, a **firewall, CDN or bot-protection tool** can block AI crawlers before they reach the site. Some CDNs offer settings to block AI bots with one click, and some enable it by default for new sites.

**What to check (or ask your developer):**

- ☐ Bot protection / "block AI bots" settings in your CDN or hosting dashboard
- ☐ Firewall rules that block unknown user agents
- ☐ Rate limits that might block crawlers visiting many pages
- ☐ Server logs: are requests from OAI-SearchBot, PerplexityBot and Bingbot getting a `200 OK` response, or `403`/`429` errors?

## 6. Indexing in Google and Bing

AI tools that search the web mostly rely on search engine indexes. If a page isn't indexed, it usually can't be cited.

### Google Search Console (search.google.com/search-console)

1. Add and verify your domain (DNS verification covers all subdomains).
2. **Sitemaps** → submit `https://yourdomain.com/sitemap.xml`.
3. **URL Inspection** → paste a key page URL → check "URL is on Google". If not, click **Request indexing**.
4. **Pages report** → review why some pages aren't indexed ("Crawled – currently not indexed", "Duplicate", "Blocked by robots.txt", etc.).

### Bing Webmaster Tools (bing.com/webmasters)

Often overlooked, but important because Bing data feeds **Microsoft Copilot** and has been a major source for **ChatGPT search**.

1. Sign in and add your site. You can **import from Google Search Console** to save time.
2. **Sitemaps** → submit your sitemap.
3. **URL Inspection** → check key pages are indexed.
4. **URL Submission** → submit new or updated pages.
5. **AI Performance** → see how often your pages are cited in Copilot and partner AI answers (see `06-measurement-guide.md`).

## 7. IndexNow

**IndexNow** is a protocol that lets your site instantly notify participating search engines (including Bing and Yandex) when a page is added, updated or deleted, instead of waiting for them to re-crawl.

- **Why it helps:** faster updates in Bing, which feeds Copilot and other AI tools.
- **How to enable:** many platforms and plugins support it (some SEO plugins for WordPress, some CDNs). Otherwise a developer can set it up using the documentation at indexnow.org.

## 8. Making content readable

AI crawlers often read the raw HTML and may not run JavaScript the way a browser does.

**Quick tests:**

1. **View source:** open the page, press Ctrl+U (Windows) or Cmd+Option+U (Mac), then search (Ctrl+F) for a key sentence. If it's not in the source, crawlers may not see it.
2. **Disable JavaScript** in your browser and reload. Is the main content still there?
3. **Check images of text:** pricing tables or charts saved as images can't be quoted. Add the same information in HTML text.

**Common problems and fixes:**

| Problem | Fix |
|---|---|
| Content loads only via JavaScript (single-page apps) | Server-side rendering or pre-rendering |
| Key info inside PDFs | Publish an HTML version of the page |
| Pricing in an image | Add an HTML table |
| Content in tabs/accordions loaded on click | Make sure the text is in the HTML on page load |
| Very slow pages / timeouts | Improve page speed; crawlers may give up |

## 9. Structured data (schema)

**Structured data** is extra code (usually in **JSON-LD** format) that labels what a page is about, such as "this is an organisation", "this is an FAQ" or "this is a product with this price". It helps search engines understand content precisely. AI-powered search builds on these systems, so clean structured data supports how your brand and pages are understood.

### Most useful types

| Schema type | Where to use it | Example file |
|---|---|---|
| `Organization` | Homepage / About page | [`organization-schema-example.json`](organization-schema-example.json) |
| `FAQPage` | Pages with an FAQ section | [`faq-schema-example.json`](faq-schema-example.json) |
| `Article` / `BlogPosting` | Blog posts and research | Include author, datePublished, dateModified |
| `SoftwareApplication` / `Product` | Product pages | Name, category, offers/price |
| `LocalBusiness` / `Restaurant` | Local businesses | Address, hours, menu URL, cuisine |
| `Person` | Author pages | Name, job title, sameAs links |
| `BreadcrumbList` | Most pages | Shows site structure |

### How to add it

- Paste the JSON-LD inside a `<script type="application/ld+json">` tag in the page's `<head>` (or body).
- **Webflow:** Page settings → Custom code → Inside `<head>` tag (use CMS fields for blog templates).
- **WordPress:** SEO plugins add basic schema automatically; add custom schema via the plugin or a code snippet.

### How to test it

- **Schema Markup Validator:** validator.schema.org
- **Google Rich Results Test:** search.google.com/test/rich-results

### Rules

- Schema must describe what's **visible on the page**. Don't add FAQs or reviews in schema that users can't see.
- Keep facts consistent with the page and your other profiles.

## 10. llms.txt

**llms.txt** is a proposed standard: a Markdown file at `yourdomain.com/llms.txt` that gives AI tools a short summary of your site and links to your most important pages.

- **Status:** major AI search platforms haven't confirmed relying on it.
- **Recommendation:** low priority. It's cheap to add, but do everything else in this guide first.

A simple example:

```markdown
# [Brand]

> [Brand] is [one-line description].

## Key pages
- [Product overview](https://yourdomain.com/product): what [Brand] does and who it's for
- [Pricing](https://yourdomain.com/pricing): plans and prices
- [Brand vs Competitor](https://yourdomain.com/brand-vs-competitor): comparison
- [Research](https://yourdomain.com/research): original data on [topic]
```

## 11. Technical checklist

- ☐ robots.txt allows OAI-SearchBot, ChatGPT-User, PerplexityBot, Claude-SearchBot, Bingbot, Googlebot
- ☐ Training crawler policy decided (GPTBot, ClaudeBot, CCBot, Google-Extended)
- ☐ No leftover `Disallow: /` from staging
- ☐ Sitemap linked in robots.txt
- ☐ CDN/firewall isn't blocking AI search crawlers
- ☐ Server logs show `200` responses for AI crawlers
- ☐ Site verified in Google Search Console, sitemap submitted
- ☐ Site verified in Bing Webmaster Tools, sitemap submitted
- ☐ Key pages indexed in both Google and Bing
- ☐ IndexNow enabled (optional)
- ☐ Key content visible in page source (not JavaScript-only)
- ☐ No key facts trapped in images or PDFs
- ☐ Organization schema on homepage
- ☐ FAQPage schema on pages with FAQs
- ☐ Article schema with author and dates on posts
- ☐ All schema validates without errors
- ☐ llms.txt added (optional, low priority)

Next: [`06-measurement-guide.md`](06-measurement-guide.md)
