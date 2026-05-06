# Module 7: Responsive Design — Mobile First

## Overview

Most people browsing the web today are on a phone. Yet the website you've built so far is designed for a wide desktop screen. In Module 7 you fix that — without touching any of the existing CSS files.

You'll create a single new file, `responsive.css`, that transforms the 4-page MITS website into a fluid, mobile-friendly experience. By the end, the site looks great at any width: a 320 px phone, a 768 px tablet, or your full desktop monitor.

---

## What is Responsive Design?

Responsive design means a single website adapts its layout to the screen it's displayed on — no separate "mobile site" required.

There are two philosophies:

| Approach | Write base styles for… | Use queries to… |
|---|---|---|
| **Desktop-first** | Wide screens | Scale *down* with `max-width` |
| **Mobile-first** | Narrow screens | Scale *up* with `min-width` |

Our existing CSS (Modules 1–6) was written desktop-first, which is common when inheriting or retrofitting a codebase. Module 7 teaches both philosophies and applies `max-width` media queries to the real, desktop-first code — exactly the skill you need on the job.

---

## Key Concepts

### 1. Media Queries

```css
@media (max-width: 767px) {
  /* Rules that only apply on screens 767 px wide or narrower */
}
```

Think of a media query as a conditional: "if the screen is this size, apply these rules instead."

**Breakpoints used in this module:**

| Name | Rule | Context |
|---|---|---|
| Tablet | `max-width: 1023px` | iPad landscape and below |
| Mobile | `max-width: 767px` | Phones and small tablets |

> **Why these numbers?** Breakpoints should be set where your *content* starts to look cramped, not around specific devices. 768 px and 1024 px are common inflection points where multi-column layouts start feeling crowded.

### 2. Responsive Typography with `clamp()`

Manually overriding every heading size in a media query is tedious. CSS `clamp()` does it in one line:

```css
h1 {
  font-size: clamp(1.75rem, 4vw, 3rem);
  /*         ^^^^^^^^^^^^^^ ^^^^^^^^^
             minimum        maximum   */
  /*                  ^^^^
                      preferred (scales with viewport) */
}
```

- **min** — font will never shrink below this value (e.g. 1.75 rem = 28 px)
- **preferred** — 4 vw = 4% of the viewport width, so it scales continuously
- **max** — font will never grow above this value (e.g. 3 rem = 48 px)

No media query needed. The font size just flows.

### 3. CSS-Only Hamburger Navigation

Showing a hamburger menu without JavaScript uses a clever trick: a **visually hidden `<input type="checkbox">`** paired with a `<label>`. Clicking the label toggles the checkbox's `:checked` state, and CSS sibling selectors respond to that state:

```css
/* Hide the nav panel by default */
nav ul { display: none; }

/* Show it when the checkbox becomes :checked */
.nav-toggle:checked ~ nav ul { display: flex; }
```

The `~` (general sibling combinator) selects `nav ul` when any preceding sibling of `.nav-toggle` matches `:checked`. No JavaScript events required.

### 4. Touch-Friendly Design

On touch screens, finger taps are far less precise than mouse clicks. Two rules of thumb:

- **Minimum tap target: 44 × 44 px** — Apple HIG and WCAG 2.5.5 both recommend this.
- **Enough spacing** — adjacent tappable items need breathing room so users don't tap the wrong one.

For the hamburger button and mobile nav links, the solution adds generous padding to meet this requirement.

### 5. Breakpoints Based on Content, Not Devices

There is no canonical list of device widths. Instead, shrink your browser window slowly and set a breakpoint *where the layout breaks* — not where a specific phone model starts. This approach stays correct as devices change.

---

## What You'll Learn

- Add a `<link>` to load `responsive.css` as the last stylesheet
- Use `clamp()` for fluid typography that needs zero media queries
- Build a CSS-only hamburger menu with `<input>` + `:checked` + `~`
- Write `@media (max-width: …)` breakpoints for tablet and mobile
- Stack grid columns for mobile with a single `grid-template-columns: 1fr` override
- Stack flex button rows vertically on mobile
- Set minimum touch target sizes (44 × 44 px)
- Test responsive layouts with browser DevTools device emulation

---

## Why This Matters

> "A page that forces you to pinch-zoom is a page that loses visitors."

More than half of global web traffic comes from mobile devices. A non-responsive site signals to users — and to Google — that the experience will be poor. This module adds that critical layer of polish so the MITS website is truly production-ready.

Practically, the techniques here cover what you'll do in almost every real-world project:
- Retrofit a desktop-first codebase with responsive rules
- Add a mobile navigation pattern without JavaScript
- Scale typography fluidly across viewports

---

## PRD Connection

This module implements:

> **Must-have**: Responsive design across all screen sizes  
> **Must-have**: Mobile navigation pattern  
> **Must-have**: Touch-friendly interactions  

---

## Prerequisites

- Completed Module 6 (polished 4-page site with `enhancements.css`)
- Basic understanding of the CSS box model
- Familiarity with browser DevTools (any modern browser)

---

## Time Estimate

⏱️ **90–120 minutes**

---

## Module Structure

1. **Task 1** — Open DevTools responsive mode & audit the current site
2. **Task 2** — Create `responsive.css` and link it in all pages
3. **Task 3** — Add fluid typography with `clamp()`
4. **Task 4** — Add hamburger HTML to all pages
5. **Task 5** — Style the hamburger button (desktop hidden, mobile shown)
6. **Task 6** — Animate hamburger → X on open
7. **Task 7** — Add tablet breakpoint (2-column grids)
8. **Task 8** — Add mobile breakpoint (single column, reduced spacing)
9. **Task 9** — Make the nav panel appear on mobile
10. **Task 10** — Touch-friendly nav links and CTA buttons
11. **Task 11** — Version control with Git

---

## Expected Result

After this module the website will:

- **320 px (phone)** — single-column cards, hamburger menu, stacked hero buttons
- **768 px (tablet)** — 2-column project cards, full nav still visible
- **1024 px+ (desktop)** — unchanged from Module 6

The hamburger icon will smoothly animate into an × when the menu is open, and every tap target will meet the 44 × 44 px minimum size requirement.
