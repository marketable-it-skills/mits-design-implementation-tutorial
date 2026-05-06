# Module 8 Workshop: Accessibility, SEO & Production Deployment

**Goal:** Make the MITS website production-ready — accessible to screen readers, visible to search engines, and live on GitHub Pages.

**Starting point:** Your Module 7 solution (4 responsive pages)

---

## Task 1: Accessibility Audit — Find What's Missing

Before writing code, run a quick manual audit to understand the baseline.

### Step 1.1: Test with Keyboard Only

Close your mouse. Use only these keys to navigate your Module 7 site:

| Key | Action |
|---|---|
| `Tab` | Move to next focusable element |
| `Shift + Tab` | Move to previous focusable element |
| `Enter` / `Space` | Activate a link or button |
| `Esc` | Close a menu |

**Check:**
- [ ] Can you reach every link and button without a mouse?
- [ ] Is the focus outline visible at all times?
- [ ] On mobile breakpoint (resize window): can you open/close the hamburger menu with keyboard?

### Step 1.2: Run Lighthouse

In Chrome, open DevTools → "Lighthouse" tab → check "Accessibility" → click "Analyze page load".

Note the current accessibility score and which issues it flags.

**Common issues you'll fix in this module:**
- "Links do not have a discernible name" (logo link with empty alt)
- "Navigation landmark does not have an accessible name"
- "List items are not contained within a `<ul>` or `<ol>`"

### Step 1.3: Verify

Write down (or screenshot) the accessibility score before making changes. You'll compare after.

---

## Task 2: Make the Logo a Navigation Link

Users expect the logo to be a link back to the homepage. Screen reader users specifically benefit because it provides an easy way to return to home.

### Step 2.1: Change the Logo Wrapper

In **all four HTML files**, find the logo `<div>` in the header:

```html
<!-- Before (Module 7) -->
<div class="logo">
  <img src="assets/images/logo-dark.svg" alt="MITS Logo" class="logo-icon" />
  <span>MITS Platform</span>
</div>
```

Replace it with an `<a>` element:

```html
<!-- After (Module 8) -->
<a href="index.html" class="logo">
  <img src="assets/images/logo-dark.svg" alt="" aria-hidden="true" class="logo-icon" />
  <span>MITS Platform</span>
</a>
```

> **Why `alt=""` and `aria-hidden="true"` on the image?**
>
> The accessible name of the link comes from the `<span>MITS Platform</span>` text. If the `<img>` also has `alt="MITS Logo"`, a screen reader would announce "MITS Logo MITS Platform link" — redundant and confusing.
>
> Setting `alt=""` (empty string) tells the browser the image is decorative. Adding `aria-hidden="true"` ensures even the empty alt doesn't appear in the accessibility tree. The link's accessible name is simply "MITS Platform" from the span.

### Step 2.2: Add `text-decoration: none` to layout.css

When `.logo` changes from a `<div>` to an `<a>`, the browser adds a default underline. Fix this in `css/layout.css`:

Find the `.logo` rule and add one line:

```css
.logo {
  display: flex;
  align-items: center;
  gap: var(--spacing-xs);
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--color-text-primary);
  text-decoration: none; /* add this */
}
```

### Step 2.3: Verify

Refresh the page. The logo should:
- [ ] Look identical to before (no underline, correct color)
- [ ] Be clickable from any page and navigate to `index.html`
- [ ] Show a focus ring when tabbed to (from `enhancements.css`)
- [ ] Announce as "MITS Platform link" in a screen reader (not "MITS Logo MITS Platform link")

---

## Task 3: Navigation Accessibility — `aria-label` and `aria-current`

### Step 3.1: Add `aria-label` to the `<nav>` Element

Without a label, a screen reader announces "navigation" — unhelpful when a page has multiple navs (header + footer). Add a label to the main nav on **all four pages**:

```html
<!-- Before -->
<nav>

<!-- After -->
<nav aria-label="Main navigation">
```

Now a screen reader announces: **"Main navigation — landmark"**.

### Step 3.2: Add `aria-current="page"` to Active Links

Replace `class="active"` with both `class="active"` and `aria-current="page"` on the current page's link.

**`index.html`** — Home link is active:
```html
<li><a href="index.html" class="active" aria-current="page">Home</a></li>
```

**`about.html`** — About link is active:
```html
<li><a href="about.html" class="active" aria-current="page">About</a></li>
```

**`guide.html`** — Guide link is active:
```html
<li><a href="guide.html" class="active" aria-current="page">Guide</a></li>
```

**`contribute.html`** — Contribute link is active:
```html
<li><a href="contribute.html" class="active" aria-current="page">Contribute</a></li>
```

> **Why both `class="active"` and `aria-current="page"`?**
>
> `class="active"` is for CSS (visual styling). `aria-current="page"` is for screen readers (semantic meaning). CSS and accessibility are separate concerns — both are needed.

### Step 3.3: Add `aria-label` to Footer Navigation

The footer has a Quick Links `<ul>`. Add a label to distinguish it from the header nav:

In **all four pages**, find the footer Quick Links section and update the `<ul>`:

```html
<ul aria-label="Footer navigation">
```

### Step 3.4: Verify

Use the keyboard to tab into the nav on any page. A screen reader (or Chrome's accessibility panel) should announce:
- [ ] "Main navigation" when entering the `<nav>`
- [ ] "current page" next to the active link

---

## Task 4: Hide Decorative Emoji from Screen Readers

Emoji read aloud by screen readers sound strange. "book books books" or "graduation cap" instead of just "Curated Projects" interrupts the content.

### Step 4.1: `about.html` — Feature Icons

Find the feature card headings. Add `aria-hidden="true"` to each `.feature-icon` span:

```html
<!-- Before -->
<h3><span class="feature-icon">📚</span> Curated Projects</h3>

<!-- After -->
<h3><span class="feature-icon" aria-hidden="true">📚</span> Curated Projects</h3>
```

Do this for all four feature icons: 📚, 🎯, 💼, 🌍.

### Step 4.2: `contribute.html` — Opportunity Icons

Same pattern for the opportunity card headings:

```html
<!-- Before -->
<h3><span class="opportunity-icon">🎓</span> Educators & Teachers</h3>

<!-- After -->
<h3><span class="opportunity-icon" aria-hidden="true">🎓</span> Educators &amp; Teachers</h3>
```

Do this for all four icons: 🎓, 💻, 🏆, 🌟.

> **Note:** Also change `&` to `&amp;` in "Educators & Teachers" — `&` should always be escaped in HTML to `&amp;` to avoid parser confusion.

### Step 4.3: `index.html` — Flag Emoji in Badge

The language badge `🇬🇧 EN` contains a decorative flag. Hide the flag emoji while keeping the "EN" text:

```html
<!-- Before -->
<span class="badge-lang">🇬🇧 EN</span>

<!-- After -->
<span class="badge-lang"><span aria-hidden="true">🇬🇧</span> EN</span>
```

This way screen readers say "EN" only — not the full flag description.

### Step 4.4: Verify

Run Lighthouse again. Accessibility score should be higher. Alternatively, use Chrome's built-in accessibility tree (DevTools → Elements → Accessibility tab) to inspect headings — they should show clean text without emoji.

---

## Task 5: Improve Page Titles and Meta Descriptions

Good titles and descriptions are crucial for click-through rates in search results.

### Step 5.1: Title Tag Guidelines

```
Format: [Page Topic] — [Site Name]
Length: 50–60 characters (Google truncates longer titles)
```

Update each page's `<title>`:

**`index.html`:**
```html
<title>MITS — Marketable IT Skills Platform for Vocational Education</title>
```

**`about.html`:**
```html
<title>About MITS — Our Mission & Platform Features</title>
```

**`guide.html`:**
```html
<title>Getting Started with MITS — Registration & User Guide</title>
```

**`contribute.html`:**
```html
<title>Collaborate with MITS — Contribute to Vocational IT Education</title>
```

### Step 5.2: Meta Description Guidelines

```
Length: 120–158 characters
Content: What the page offers + a reason to click
No: "Homepage", "Click here", keyword stuffing
```

Update each page's `<meta name="description">`:

**`index.html`:**
```html
<meta
  name="description"
  content="MITS provides real competition tasks from European and international IT competitions, adapted for vocational education. Build portfolio projects with authentic challenges."
/>
```

**`about.html`:**
```html
<meta
  name="description"
  content="Learn about the MITS initiative — bridging vocational education and industry by providing real EuroSkills and WorldSkills competition tasks for students worldwide."
/>
```

**`guide.html`:**
```html
<meta
  name="description"
  content="Learn how to get started with the MITS platform. Create an account, browse competition projects, and start building your portfolio with real-world IT challenges."
/>
```

**`contribute.html`:**
```html
<meta
  name="description"
  content="Join the MITS initiative as an educator, industry professional, or open-source contributor. Help shape the future of vocational IT education through collaboration."
/>
```

### Step 5.3: Verify

Open each page and check `<head>` in DevTools. Confirm the titles are updated.

Use [this character counter tool](https://charactercounter.com/) to verify your descriptions are 120–158 characters.

---

## Task 6: Add Open Graph Tags

Open Graph tags control the preview card when your page is shared on Facebook, LinkedIn, WhatsApp, Slack, and most other platforms.

### Step 6.1: Understand the Tags

```html
<meta property="og:type"        content="website" />
<meta property="og:url"         content="https://YOUR-USERNAME.github.io/REPO-NAME/index.html" />
<meta property="og:title"       content="MITS — Marketable IT Skills Platform" />
<meta property="og:description" content="Real competition tasks for vocational IT education..." />
<meta property="og:image"       content="https://YOUR-USERNAME.github.io/REPO-NAME/assets/images/mits-hero-image.webp" />
<meta property="og:site_name"   content="MITS Platform" />
<meta property="og:locale"      content="en_US" />
```

> **Recommended OG image size:** 1200 × 630 px. The hero image (`mits-hero-image.webp`) works well as it's a wide landscape image.

### Step 6.2: Add to All Four Pages

Add the OG block in `<head>`, **after** the `<meta name="description">` tag, in each HTML file. Adjust the `og:url`, `og:title`, and `og:description` to match each page.

**`index.html`** (add after description meta):
```html
<!-- Open Graph -->
<meta property="og:type" content="website" />
<meta property="og:url" content="https://YOUR-USERNAME.github.io/REPO-NAME/index.html" />
<meta property="og:title" content="MITS — Marketable IT Skills Platform" />
<meta property="og:description" content="Real competition tasks from EuroSkills and WorldSkills, adapted for vocational IT education. Build your portfolio with authentic projects." />
<meta property="og:image" content="https://YOUR-USERNAME.github.io/REPO-NAME/assets/images/mits-hero-image.webp" />
<meta property="og:site_name" content="MITS Platform" />
<meta property="og:locale" content="en_US" />
```

Use the same pattern for `about.html`, `guide.html`, `contribute.html` — only `og:url`, `og:title`, and `og:description` change per page. `og:image`, `og:site_name`, and `og:locale` stay the same.

### Step 6.3: Verify Locally

You can't fully test Open Graph locally (social crawlers need a public URL), but you can verify the tags exist using DevTools → Elements → search for `og:title`.

---

## Task 7: Add Twitter Card Tags

Twitter (now X) uses its own meta tags. They're similar to Open Graph but with different property names.

### Step 7.1: Add to All Four Pages

Add immediately after the OG block:

```html
<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:title" content="MITS — Marketable IT Skills Platform" />
<meta name="twitter:description" content="Real competition tasks for vocational IT education." />
<meta name="twitter:image" content="https://YOUR-USERNAME.github.io/REPO-NAME/assets/images/mits-hero-image.webp" />
```

> **`summary_large_image`** shows a large image preview (the best choice for sites with visual content). The alternative `summary` shows a small thumbnail.

Again, only `twitter:title` and `twitter:description` change per page.

### Step 7.2: Verify

Search `twitter:card` in DevTools Elements to confirm the tags are present.

---

## Task 8: Canonical URL and Theme Color

### Step 8.1: Add Canonical URL

A canonical URL tells search engines "this is the definitive address for this page". It prevents duplicate-content penalties when the same page is accessible via multiple URLs.

Add inside `<head>`, after the `<title>`:

```html
<link rel="canonical" href="https://YOUR-USERNAME.github.io/REPO-NAME/index.html" />
```

Change the filename (`index.html`, `about.html`, etc.) for each page.

### Step 8.2: Add Theme Color

This tints the browser chrome on Android/Chrome when users visit your site:

```html
<meta name="theme-color" content="#1a1a2e" />
```

`#1a1a2e` matches the dark background of the site.

### Step 8.3: Verify

The canonical link should appear in DevTools → Elements under `<head>`. The theme-color effect is visible when the site is deployed and accessed on Android Chrome.

---

## Task 9: Add JSON-LD Structured Data

JSON-LD (JavaScript Object Notation for Linked Data) adds machine-readable context to your pages. Google can use it to show rich results in search.

### Step 9.1: Add WebSite Schema to `index.html`

Place the `<script>` block inside `<head>`, after the Twitter Card tags:

```html
<!-- Structured Data: WebSite + Organization -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "name": "MITS Platform",
  "url": "https://YOUR-USERNAME.github.io/REPO-NAME/",
  "description": "Marketable IT Skills platform providing real competition tasks for vocational education",
  "publisher": {
    "@type": "Organization",
    "name": "MITS Initiative",
    "url": "https://YOUR-USERNAME.github.io/REPO-NAME/",
    "email": "info@mits-platform.org",
    "sameAs": ["https://github.com/marketable-it-skills"]
  }
}
</script>
```

### Step 9.2: Add WebPage Schema to Inner Pages

For `about.html`, `guide.html`, and `contribute.html`, use the `WebPage` type:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "name": "About MITS",
  "url": "https://YOUR-USERNAME.github.io/REPO-NAME/about.html",
  "description": "Learn about the MITS initiative and its mission",
  "isPartOf": {
    "@type": "WebSite",
    "name": "MITS Platform",
    "url": "https://YOUR-USERNAME.github.io/REPO-NAME/"
  }
}
</script>
```

Change `"name"`, `"url"`, and `"description"` for each page.

### Step 9.3: Validate

Go to [Google's Rich Results Test](https://search.google.com/test/rich-results) and paste the contents of `index.html`. It will show whether the JSON-LD is valid and eligible for rich results.

> **Alternative:** Use [Schema.org Validator](https://validator.schema.org/) for offline validation.

---

## Task 10: Create `sitemap.xml` and `robots.txt`

### Step 10.1: Create `sitemap.xml`

In the root of your project (same level as `index.html`), create `sitemap.xml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">

  <url>
    <loc>https://YOUR-USERNAME.github.io/REPO-NAME/index.html</loc>
    <changefreq>monthly</changefreq>
    <priority>1.0</priority>
  </url>

  <url>
    <loc>https://YOUR-USERNAME.github.io/REPO-NAME/about.html</loc>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>

  <url>
    <loc>https://YOUR-USERNAME.github.io/REPO-NAME/guide.html</loc>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>

  <url>
    <loc>https://YOUR-USERNAME.github.io/REPO-NAME/contribute.html</loc>
    <changefreq>monthly</changefreq>
    <priority>0.7</priority>
  </url>

</urlset>
```

> **`priority`** is relative (1.0 = most important). The home page gets 1.0, inner pages get 0.7–0.8.

### Step 10.2: Create `robots.txt`

In the same root folder, create `robots.txt`:

```
User-agent: *
Allow: /

Sitemap: https://YOUR-USERNAME.github.io/REPO-NAME/sitemap.xml
```

### Step 10.3: Verify Locally

Open `sitemap.xml` in your browser. It should render as valid XML (no parse errors). The browser usually displays XML in a tree structure with colour highlighting.

---

## Task 11: Deploy to GitHub Pages

### Step 11.1: Commit Your Changes

```bash
git add .
git commit -m "Add SEO meta tags, ARIA improvements, sitemap, and robots.txt"
```

### Step 11.2: Push to GitHub

```bash
git push origin main
```

### Step 11.3: Enable GitHub Pages

1. Go to your repository on **github.com**
2. Click **Settings** tab
3. In the left sidebar, click **Pages**
4. Under **Source**, select **Deploy from a branch**
5. Choose **main** branch, **/ (root)** folder
6. Click **Save**

GitHub will display a message: *"Your site is live at https://YOUR-USERNAME.github.io/REPO-NAME/"*

> **Note:** It can take 1–5 minutes for the site to appear after the first deployment.

### Step 11.4: Update All Placeholders

Once you have your live URL, go back and replace all occurrences of `YOUR-USERNAME` and `REPO-NAME` in:
- All 4 HTML files (canonical, OG, Twitter, JSON-LD)
- `sitemap.xml`
- `robots.txt`

Commit and push again:

```bash
git add .
git commit -m "Update live URLs in meta tags and sitemap"
git push origin main
```

### Step 11.5: Verify

Visit your GitHub Pages URL and check:
- [ ] All 4 pages load correctly
- [ ] Navigation works between pages
- [ ] Images display (hero image, logo)
- [ ] Hamburger menu works on mobile

---

## Task 12: Post-Deployment Testing

### Step 12.1: Run a Lighthouse Audit on the Live Site

Open Chrome, visit your live GitHub Pages URL, open DevTools → Lighthouse.

Run a report for all four categories: **Performance**, **Accessibility**, **Best Practices**, **SEO**.

**Target scores:** 90+ in all four categories.

Common issues and fixes:

| Issue | Fix |
|---|---|
| Accessibility < 90 | Check remaining ARIA issues in Lighthouse report |
| SEO < 90 | Verify all meta tags are present on all pages |
| Best Practices < 90 | Usually HTTPS-related (GitHub Pages provides HTTPS automatically) |
| Performance < 90 | Images may need optimisation — WebP (already used) is good |

### Step 12.2: Test Social Sharing Preview

**Facebook / LinkedIn:**
Use [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/) — paste your live URL to see how it previews.

**Twitter:**
Use [Twitter Card Validator](https://cards-dev.twitter.com/validator) — paste your live URL.

Both tools show you exactly what the social preview card will look like.

### Step 12.3: Submit to Google Search Console (Optional)

1. Go to [Google Search Console](https://search.google.com/search-console)
2. Add your GitHub Pages URL as a property
3. Verify ownership (GitHub Pages can use the HTML tag method)
4. Submit your sitemap URL: `https://YOUR-USERNAME.github.io/REPO-NAME/sitemap.xml`

Google will start indexing your site within a few days.

### Step 12.4: Final Verification Checklist

**Accessibility:**
- [ ] Lighthouse accessibility score: 90+
- [ ] Logo links to homepage from all pages
- [ ] `aria-label="Main navigation"` on all `<nav>` elements
- [ ] `aria-current="page"` on active nav links
- [ ] Decorative emoji hidden with `aria-hidden="true"`
- [ ] Keyboard navigation works through all pages

**SEO:**
- [ ] Each page has unique `<title>` (50–60 chars)
- [ ] Each page has unique `<meta name="description">` (120–158 chars)
- [ ] Canonical URL matches actual page URL
- [ ] Open Graph tags on all 4 pages
- [ ] Twitter Card tags on all 4 pages
- [ ] JSON-LD structured data on all 4 pages
- [ ] `sitemap.xml` is valid XML and accessible at `/sitemap.xml`
- [ ] `robots.txt` is accessible at `/robots.txt`

**Deployment:**
- [ ] Site is live at GitHub Pages URL
- [ ] All pages load without errors
- [ ] Images display correctly
- [ ] Lighthouse scores 90+ in all categories

---

## Task 13: Version Control with Git

### Step 13.1: Create Feature Branch

```bash
git checkout -b feat/module-8-seo-accessibility
```

### Step 13.2: Stage and Commit All Changes

```bash
git add .
git commit -m "Complete Module 8: accessibility improvements, SEO meta tags, and GitHub Pages deployment"
```

### Step 13.3: Merge and Push

```bash
git checkout main
git merge feat/module-8-seo-accessibility
git push origin main
```

---

## Congratulations — Course Complete! 🎉

You have built a complete, production-quality 4-page website from scratch using only HTML and CSS:

| Module | Achievement |
|---|---|
| 1 | Semantic HTML5 structure for all 4 pages |
| 2 | Dark-theme CSS foundation (variables, typography, Flexbox, Grid) |
| 3 | Home page with hero, project cards, buttons, transitions |
| 4 | About page with feature grid and custom list bullets |
| 5 | Guide + Contribute pages with CSS counters and flex layouts |
| 6 | Site-wide polish: animations, skip link, focus rings, print styles |
| 7 | Responsive design: hamburger menu, clamp typography, media queries |
| 8 | Production-ready: ARIA accessibility, SEO meta, JSON-LD, GitHub Pages |

Your site is now:
- **Accessible** — WCAG AA compliant, keyboard navigable, screen-reader friendly
- **SEO-optimised** — proper meta tags, structured data, sitemap
- **Responsive** — works on any device from 320 px to 4K
- **Live** — deployed on GitHub Pages, ready to share in your portfolio

**Next steps:**
- Add your GitHub Pages URL to your CV/LinkedIn profile
- Run Lighthouse monthly to maintain your scores
- Explore JavaScript to add dynamic features
- Explore React or Vue for the next level of frontend development
