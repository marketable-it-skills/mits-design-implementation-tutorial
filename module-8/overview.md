# Module 8: Accessibility, SEO & Production Deployment

## Overview

Your MITS website looks beautiful, responds to every screen size, and runs polished animations. In Module 8 you make it *production-ready* — visible to search engines, understandable by screen readers, and live on the web via GitHub Pages.

By the end of this module, every page will have structured metadata that search engines and social platforms understand, ARIA improvements that screen readers announce correctly, a `sitemap.xml` that guides crawlers, and a live URL you can share in your portfolio.

---

## What is Accessibility (WCAG AA)?

**WCAG** — Web Content Accessibility Guidelines — is the international standard for making web content usable by people with disabilities. "AA" is the middle tier: it's what most governments and organisations require by law.

Key WCAG AA concepts applied in this module:

| Concept | What it means | How we implement it |
|---|---|---|
| Accessible names | Every interactive element needs a text name a screen reader can announce | `aria-label` on the hamburger nav, `aria-label` on nav element |
| Current page indication | Screen readers should know which page is active | `aria-current="page"` on active nav links |
| Decorative images | Images that are purely decorative shouldn't be announced | `alt=""` + `aria-hidden="true"` on the logo `<img>` |
| Decorative icons | Emoji used as decoration shouldn't be read aloud | `aria-hidden="true"` on icon spans |
| Logo as navigation | The logo should link back to the homepage | Wrap `.logo` in `<a href="index.html">` |

### Screen Reader Behaviour — Before vs After

**Before (Module 7):**
> "Navigation — list of 4 items — Home, About, Guide, Contribute"

A screen reader user doesn't know *which* page they're on.

**After (Module 8):**
> "Main navigation — list of 4 items — Home, About, current page: Guide, Contribute"

`aria-current="page"` tells the screen reader to announce "current page" next to the active link.

---

## What is SEO?

**SEO** (Search Engine Optimisation) is the practice of helping search engines understand and rank your content.

Three layers of SEO meta tags are used in this module:

### 1. Standard HTML Meta Tags

```html
<title>MITS — Marketable IT Skills Platform for Vocational Education</title>
<meta name="description" content="Real competition tasks..." />
<link rel="canonical" href="https://YOUR-USERNAME.github.io/REPO-NAME/index.html" />
<meta name="theme-color" content="#1a1a2e" />
```

- **title** — the clickable headline in Google results (50–60 characters ideal)
- **description** — the snippet below the title (120–158 characters ideal)
- **canonical** — the definitive URL for this page, prevents duplicate-content penalties
- **theme-color** — colours the browser chrome on mobile (Chrome/Android)

### 2. Open Graph Tags

Open Graph tags control how your page looks when shared on Facebook, LinkedIn, and messaging apps:

```html
<meta property="og:type" content="website" />
<meta property="og:title" content="MITS — Marketable IT Skills Platform" />
<meta property="og:description" content="..." />
<meta property="og:image" content="https://YOUR-USERNAME.github.io/REPO-NAME/assets/images/mits-hero-image.webp" />
<meta property="og:url" content="https://YOUR-USERNAME.github.io/REPO-NAME/index.html" />
<meta property="og:site_name" content="MITS Platform" />
<meta property="og:locale" content="en_US" />
```

Without these, social platforms generate their own (often wrong) preview.

### 3. Twitter Card Tags

Twitter (now X) uses its own tags:

```html
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:title" content="MITS — Marketable IT Skills Platform" />
<meta name="twitter:description" content="..." />
<meta name="twitter:image" content="https://YOUR-USERNAME.github.io/REPO-NAME/assets/images/mits-hero-image.webp" />
```

### 4. JSON-LD Structured Data

**JSON-LD** is a machine-readable format that tells search engines about *entities* on your page — not just the text content:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "name": "MITS Platform",
  "url": "https://YOUR-USERNAME.github.io/REPO-NAME/",
  "publisher": {
    "@type": "Organization",
    "name": "MITS Initiative",
    "email": "info@mits-platform.org"
  }
}
</script>
```

Google uses this to generate rich results, knowledge panels, and better search snippets.

---

## What is a Sitemap?

`sitemap.xml` is a file that lists every URL on your site. Search engines use it to ensure all your pages get crawled, even pages with no inbound links.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://YOUR-USERNAME.github.io/REPO-NAME/index.html</loc>
    <priority>1.0</priority>
  </url>
  ...
</urlset>
```

You submit the sitemap URL to **Google Search Console** after deployment.

## What is robots.txt?

`robots.txt` tells crawlers which parts of your site they may or may not index. For a public portfolio site, you allow everything and point to the sitemap:

```
User-agent: *
Allow: /
Sitemap: https://YOUR-USERNAME.github.io/REPO-NAME/sitemap.xml
```

---

## What is GitHub Pages?

GitHub Pages is a free static site hosting service built into GitHub. Any public repository can serve its files at `https://YOUR-USERNAME.github.io/REPO-NAME/`.

No server required — it just hosts your HTML, CSS, and image files exactly as they are.

---

## What You'll Learn

- Add `aria-label="Main navigation"` to the nav element
- Use `aria-current="page"` to mark the active page link
- Convert the logo `<div>` to an `<a>` element for keyboard + screen reader users
- Add `aria-hidden="true"` to decorative emoji spans
- Write complete, well-formed page titles and meta descriptions (character-count guidelines)
- Add Open Graph tags for social sharing previews
- Add Twitter Card tags
- Add canonical URL links
- Add `<meta name="theme-color">` for mobile browser chrome
- Embed JSON-LD structured data for search engine rich results
- Create `sitemap.xml` listing all 4 pages
- Create `robots.txt`
- Deploy the site to GitHub Pages
- Test with Lighthouse, PageSpeed Insights, and the Meta Preview Debugger

---

## Why This Matters

A site that only *looks* good is half-finished. Production-quality work means:

- **People with disabilities can use it** — 1 in 6 people worldwide have some form of disability
- **Search engines can index it** — without meta tags, Google can't generate good search previews
- **Social sharing works properly** — without Open Graph, LinkedIn/Facebook generate broken previews
- **It's live and shareable** — a GitHub Pages URL in your portfolio is immediately verifiable

These skills are expected in every professional web project.

---

## PRD Connection

This module implements:

> **Must-have**: WCAG AA accessibility compliance  
> **Must-have**: SEO-optimized with proper meta tags  
> **Must-have**: GitHub-hosted portfolio project  
> **Nice-to-have**: Open Graph and Twitter Card tags  
> **Nice-to-have**: Structured data (JSON-LD)

---

## Prerequisites

- Completed Module 7 (responsive 4-page site with `responsive.css`)
- GitHub account with the repository already set up (from Module 1)
- Familiarity with browser DevTools

---

## Time Estimate

⏱️ **90–120 minutes**

---

## Module Structure

1. **Task 1** — Accessibility audit: identify missing ARIA attributes
2. **Task 2** — Make the logo a navigation link
3. **Task 3** — Add `aria-label` and `aria-current` to navigation
4. **Task 4** — Hide decorative emoji from screen readers
5. **Task 5** — Improve page titles and meta descriptions on all 4 pages
6. **Task 6** — Add Open Graph tags to all 4 pages
7. **Task 7** — Add Twitter Card tags to all 4 pages
8. **Task 8** — Add canonical URL and theme-color meta
9. **Task 9** — Add JSON-LD structured data to all 4 pages
10. **Task 10** — Create `sitemap.xml` and `robots.txt`
11. **Task 11** — Deploy to GitHub Pages
12. **Task 12** — Post-deployment: Lighthouse audit & social preview testing
13. **Task 13** — Version control with Git

---

## Expected Result

After this module:

- All 4 pages pass a Lighthouse accessibility audit with a score of 90+
- Google can generate rich search snippets with your title and description
- Sharing any page on LinkedIn shows the correct hero image preview
- The site is live at `https://YOUR-USERNAME.github.io/REPO-NAME/`
- A Lighthouse Performance + SEO + Accessibility + Best Practices report shows 90+ in all four categories
