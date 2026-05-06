# MITS Design & Implementation Tutorial

![MITS Design & Implementation Tutorial](./assets/images/course-cover-image.webp)

> Build a **production-ready, 4-page professional website** using only HTML5 and CSS3 — no JavaScript, no frameworks, just pure web fundamentals done right.

[![Course Status](https://img.shields.io/badge/Status-Complete-brightgreen)](.)
[![Modules](https://img.shields.io/badge/Modules-8-blue)](.)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner%20to%20Intermediate-orange)](.)
[![Time](https://img.shields.io/badge/Total%20Time-8--12%20hours-lightgrey)](.)
[![Tech](https://img.shields.io/badge/Tech-HTML5%20%2B%20CSS3-cyan)](.)

---

## 📚 Overview

The **MITS Design & Implementation Tutorial** teaches you to build professional websites using pure HTML5 and CSS3. You'll build a complete promotional website for the MITS (Marketable IT Skills) platform — a dark-themed, 4-page site featuring a hero section with background image, responsive project cards, accessible navigation, and full mobile support.

No shortcuts. No frameworks. You'll understand every line you write.

### What You'll Build

A complete **MITS Platform promotional website** with 4 fully-styled, accessible, responsive pages:

| Page            | Content                                                  |
| --------------- | -------------------------------------------------------- |
| **Home**        | Hero section, project card grid, call-to-action sections |
| **About**       | Mission statement, feature grid, project goals           |
| **Guide**       | Step-by-step registration walkthrough, prerequisites     |
| **Collaborate** | Contribution opportunities, contact information          |

The final result is a **live, GitHub Pages-hosted portfolio project** with Lighthouse scores of 90+ across all categories.

### Who This Course Is For

- **Beginner web developers** learning HTML/CSS fundamentals from scratch
- **Bootcamp students** who want to master web standards deeply before frameworks
- **Self-taught developers** building strong foundational skills
- **Vocational IT students** preparing for web design competitions (EuroSkills, WorldSkills)
- **Anyone** who wants to build websites without relying on pre-built component libraries

---

## 🎯 What You'll Learn

By completing all 8 modules, you'll be able to:

- ✅ **Write semantic HTML5** — proper document structure with accessibility built in from the start
- ✅ **Create a CSS design system** — CSS custom properties (variables) for colors, spacing, and typography
- ✅ **Build modern layouts** — CSS Grid for 2D layouts, Flexbox for 1D layouts (never floats)
- ✅ **Design a dark theme** — professional color palette matching the MITS platform aesthetic
- ✅ **Style reusable components** — buttons, cards, badges, tags — the building blocks of any UI
- ✅ **Use CSS pseudo-elements** — `::before` for custom bullets, CSS counters for auto-numbering
- ✅ **Add professional polish** — `@keyframes` animations, `scroll-behavior: smooth`, focus rings
- ✅ **Build responsive layouts** — `clamp()` typography, `auto-fit` grids, CSS-only hamburger menu
- ✅ **Ensure accessibility** — WCAG AA compliance, ARIA labels, skip links, keyboard navigation
- ✅ **Optimise for SEO** — Open Graph tags, JSON-LD structured data, `sitemap.xml`, `robots.txt`
- ✅ **Deploy to production** — GitHub Pages deployment, Lighthouse auditing
- ✅ **Follow professional Git practices** — feature branches, meaningful commits, GitHub push

---

## 📋 Prerequisites

**Required:**

- Basic computer literacy (creating folders, opening files)
- A modern web browser — Chrome, Firefox, Edge, or Safari
- [VS Code](https://code.visualstudio.com/) (free code editor)
- [Git](https://git-scm.com/) installed
- A free [GitHub](https://github.com/) account

**Recommended:**

- VS Code [Live Server extension](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) for instant browser refresh
- Basic familiarity with HTML tags (helpful, not required — we teach from scratch)
- Browser DevTools open on the side (we use it constantly)

**No experience needed with:**

- CSS (we start from zero)
- JavaScript (none used in this course)
- Command line (every command is explained step by step)
- Frameworks (we deliberately avoid them)

---

## 📖 Course Structure

### ✅ Module 1: HTML Structure Only

⏱️ **Time:** 40–55 minutes

Create all 4 pages with complete semantic HTML5 structure. CSS files are linked but left empty — this teaches separation of concerns and prevents cognitive overload before you're ready to style.

**What you'll learn:**

- HTML5 semantic elements (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`)
- Proper heading hierarchy (one H1 per page, then H2–H6 in order)
- Multi-page website structure and internal linking
- CSS file organisation strategy (6 CSS files with clear responsibilities)
- HTML validation with the W3C validator

**Deliverable:** 4-page unstyled website with perfect semantic HTML — readable even without CSS

[📖 Overview](module-1/overview.md) | [🔨 Workshop](module-1/workshop.md) | [✅ Solution](module-1/solution/)

---

### ✅ Module 2: CSS Fundamentals — Base & Layout

⏱️ **Time:** 60–75 minutes

Transform your unstyled HTML into a professionally styled dark-themed website. This module builds the design system foundation that all other modules rely on.

**What you'll learn:**

- CSS reset and the box model (`box-sizing: border-box`)
- CSS custom properties (variables) for colors, spacing, and typography
- Dark theme color palette (`#0f172a` background, `#06b6d4` accent)
- Typography hierarchy — headings, body text, links
- Flexbox for 1D layouts (sticky header, navigation)
- CSS Grid for 2D layouts (footer columns)
- Sticky positioning for the header

**Deliverable:** Dark-themed website with styled header, footer, and consistent typography across all 4 pages

[📖 Overview](module-2/overview.md) | [🔨 Workshop](module-2/workshop.md) | [✅ Solution](module-2/solution/)

---

### ✅ Module 3: Home Page Styling (`index.css`)

⏱️ **Time:** 75–90 minutes

Build the most complex page first. The home page introduces the key component patterns — buttons, hero with background image, project cards — that cascade through the rest of the course.

**What you'll learn:**

- CSS component design patterns (`.btn`, `.btn-primary`, `.btn-secondary`)
- Background images with `background-size: cover` and `background-position`
- Linear gradient overlays for text readability over images
- Interactive card components: `transform: translateY()`, `box-shadow`, hover transitions
- CSS Grid `repeat(3, 1fr)` for the project card grid
- Badge and tag styling with semi-transparent backgrounds

**Deliverable:** Stunning home page with hero image, styled buttons, project cards with hover effects, and complete visual hierarchy

[📖 Overview](module-3/overview.md) | [🔨 Workshop](module-3/workshop.md) | [✅ Solution](module-3/solution/)

---

### ✅ Module 4: About Page Styling (`about.css`)

⏱️ **Time:** 60–75 minutes

Apply the design system to the About page with more advanced CSS techniques — introducing `auto-fit` grids that respond to content without media queries, and pseudo-element custom bullets.

**What you'll learn:**

- Page-specific CSS architecture (one CSS file per page)
- Section background alternation for visual rhythm
- CSS pseudo-elements (`::before`) for custom arrow list bullets
- CSS Grid `auto-fit` + `minmax(240px, 1fr)` — responsive without media queries
- `filter: grayscale(1)` for decorative emoji icons
- `p:first-of-type` selector for typographic callout emphasis

**Deliverable:** Fully styled About page with responsive feature grid and custom visual elements

[📖 Overview](module-4/overview.md) | [🔨 Workshop](module-4/workshop.md) | [✅ Solution](module-4/solution/)

---

### ✅ Module 5: Guide & Contribute Pages Styling

⏱️ **Time:** 75–90 minutes

Style the final two pages of the site. The Guide page introduces CSS counters for automatic step numbering; the Contribute page teaches opportunity card grids and flex alignment for contact information.

**What you'll learn:**

- CSS counters (`counter-reset`, `counter-increment`, `counter()`) for auto-numbered steps
- `::before` pseudo-element as a styled numbered circle
- Flexbox for step layout (number circle + content side by side)
- `text-transform: uppercase` + `letter-spacing` for label typography
- `align-items: baseline` + `min-width` for aligned label/value contact rows
- `margin-top: auto` to push elements to the bottom of flex containers

**Deliverable:** All 4 pages fully styled — a complete, portfolio-ready MITS website

[📖 Overview](module-5/overview.md) | [🔨 Workshop](module-5/workshop.md) | [✅ Solution](module-5/solution/)

---

### ✅ Module 6: Polish & Advanced CSS Techniques

⏱️ **Time:** 60–75 minutes

Add professional polish across the entire site via a single `enhancements.css` file. No new pages — just one new file that elevates the whole experience.

**What you'll learn:**

- `scroll-behavior: smooth` for native smooth scrolling
- Skip-to-content link (visually hidden until keyboard-focused)
- `:focus` vs `:focus-visible` — keyboard ring without mouse outline
- `@keyframes` `fadeInUp` animation on `<main>` page load
- `@media (prefers-reduced-motion: reduce)` — accessible animation disabling
- `@media print` — white background, hidden nav, clean printed output

**Deliverable:** A polished 4-page website with smooth interactions, keyboard accessibility, fade-in animations, and print-friendly output

[📖 Overview](module-6/overview.md) | [🔨 Workshop](module-6/workshop.md) | [✅ Solution](module-6/solution/)

---

### ✅ Module 7: Responsive Design — Mobile First

⏱️ **Time:** 90–120 minutes

Make the desktop-first website work beautifully at every screen size — 320 px phones to wide monitors — using a single `responsive.css` file and a CSS-only hamburger menu.

**What you'll learn:**

- `clamp(min, preferred, max)` for fluid typography without media queries
- CSS-only hamburger navigation: hidden `<input type="checkbox">` + `:checked` + `~` sibling selector
- Hamburger → ✕ animation with `transform: translateY() rotate()`
- `@media (max-width: 1023px)` tablet breakpoints
- `@media (max-width: 767px)` mobile breakpoints
- `position: absolute; top: 100%` for the dropdown nav panel
- Touch-friendly tap targets (44 × 44 px minimum)
- Browser DevTools device emulation for responsive testing

**Deliverable:** A fully responsive 4-page website that adapts from 320 px phones to desktops, with a working CSS hamburger menu

[📖 Overview](module-7/overview.md) | [🔨 Workshop](module-7/workshop.md) | [✅ Solution](module-7/solution/)

---

### ✅ Module 8: Accessibility, SEO & Production Deployment

⏱️ **Time:** 90–120 minutes

The final module makes the site production-ready: WCAG AA compliant, discoverable by search engines, and live on GitHub Pages with Lighthouse scores of 90+.

**What you'll learn:**

- `aria-label="Main navigation"` on `<nav>` for screen reader landmarks
- `aria-current="page"` on active nav links
- Logo as a navigation link with correct accessible name (no redundant announcements)
- `aria-hidden="true"` for decorative emoji icons
- Page `<title>` best practices (50–60 characters)
- `<meta name="description">` (120–158 characters)
- Open Graph tags (`og:title`, `og:description`, `og:image`, `og:type`) for social sharing
- Twitter Card tags for share previews
- `<link rel="canonical">` and `<meta name="theme-color">`
- JSON-LD structured data (`WebSite` + `WebPage` schemas)
- `sitemap.xml` and `robots.txt`
- GitHub Pages deployment and Lighthouse auditing

**Deliverable:** A live, publicly accessible website deployed on GitHub Pages with WCAG AA accessibility, full SEO metadata, and Lighthouse 90+ scores

[📖 Overview](module-8/overview.md) | [🔨 Workshop](module-8/workshop.md) | [✅ Solution](module-8/solution/)

---

## 📚 Modules at a Glance

| Module         | Title                            | Status      | Time       | Key Concept                              |
| -------------- | -------------------------------- | ----------- | ---------- | ---------------------------------------- |
| [1](module-1/) | HTML Structure Only              | ✅ Complete | 40–55 min  | Semantic HTML5, W3C validation           |
| [2](module-2/) | CSS Fundamentals — Base & Layout | ✅ Complete | 60–75 min  | CSS variables, Flexbox, Grid             |
| [3](module-3/) | Home Page Styling                | ✅ Complete | 75–90 min  | Components, hero image, cards            |
| [4](module-4/) | About Page Styling               | ✅ Complete | 60–75 min  | `::before`, `auto-fit`, grayscale filter |
| [5](module-5/) | Guide & Contribute Styling       | ✅ Complete | 75–90 min  | CSS counters, flex alignment             |
| [6](module-6/) | Polish & Advanced CSS            | ✅ Complete | 60–75 min  | Animations, focus rings, print styles    |
| [7](module-7/) | Responsive Design                | ✅ Complete | 90–120 min | `clamp()`, hamburger menu, breakpoints   |
| [8](module-8/) | Accessibility, SEO & Deployment  | ✅ Complete | 90–120 min | ARIA, Open Graph, JSON-LD, GitHub Pages  |

**Total estimated time:** 8–12 hours

---

## 🚀 Getting Started

### Option 1: Follow Modules Sequentially (Recommended)

Each module builds directly on the previous one. Follow this path for the full learning experience:

1. Read [Module 1 Overview](module-1/overview.md) to understand the concepts
2. Work through [Module 1 Workshop](module-1/workshop.md) step-by-step
3. Compare your work with [Module 1 Solution](module-1/solution/) if you get stuck
4. Move to Module 2 and repeat

**Why this works:** You see the site transform incrementally — from plain HTML to a dark-themed layout to a polished, responsive, live website. Each step produces an immediate visual result.

### Option 2: Clone and Explore

```bash
# Clone the course creator repository
git clone https://github.com/marketable-it-skills/mits-course-creator.git

# Navigate to this course
cd mits-course-creator/courses/mits-design-implementation-tutorial

# Open Module 1 overview
code module-1/overview.md
```

### Option 3: Use Solutions as Reference

Each module includes a complete `solution/` folder. Use them to:

- Verify your implementation is on the right track
- Debug issues by comparing your code with the working version
- See the expected visual result at each stage

> **Note:** Try to complete each workshop yourself before checking solutions. You'll learn significantly more from working through the challenge.

### Option 4: Fast-Track (For Developers with HTML/CSS Basics)

If you already know basic HTML/CSS, focus on the modern techniques:

| Module                | Why It's Worth Your Time                             |
| --------------------- | ---------------------------------------------------- |
| [Module 2](module-2/) | CSS custom properties — the modern way to theme      |
| [Module 4](module-4/) | `auto-fit` grids + pseudo-element bullets            |
| [Module 5](module-5/) | CSS counters — powerful and underused                |
| [Module 6](module-6/) | `@keyframes`, `prefers-reduced-motion`, print styles |
| [Module 7](module-7/) | `clamp()` + CSS-only hamburger menu                  |
| [Module 8](module-8/) | ARIA, Open Graph, JSON-LD, deployment                |

---

## 🛠️ Technologies & Concepts Covered

### Core Technologies

- **HTML5** — Semantic elements, accessibility attributes, meta tags
- **CSS3** — Grid, Flexbox, custom properties, animations, media queries
- **Git & GitHub** — Version control, feature branches, GitHub Pages deployment

### CSS Concepts by Module

**Foundation (Modules 1–3)**

- Semantic HTML5 structure (`header`, `nav`, `main`, `section`, `article`, `footer`)
- CSS reset and box model (`box-sizing: border-box`)
- CSS custom properties (design tokens for colors, spacing, typography)
- Typography hierarchy (heading scale, line height, font weights)
- Flexbox for 1D layouts — header navigation, button groups
- CSS Grid for 2D layouts — footer columns, project card grid
- Sticky positioning, container pattern, section spacing
- Button components (`.btn`, `.btn-primary`, `.btn-secondary`)
- Background images with gradient overlays (`background-size: cover`)
- Card components — hover effects with `transform` and `box-shadow`

**Intermediate (Modules 4–5)**

- CSS pseudo-elements `::before` for custom list bullets
- CSS Grid `auto-fit` + `minmax()` — responsive without media queries
- CSS counters — automatic sequential numbering
- `filter: grayscale(1)` for decorative images
- `text-transform`, `letter-spacing` for label typography
- `align-items: baseline` for aligned label/value rows
- `margin-top: auto` for bottom-aligned flex children

**Advanced (Modules 6–8)**

- `@keyframes` and the `animation` shorthand
- `scroll-behavior: smooth` — native smooth scrolling
- `:focus-visible` — keyboard ring without mouse outline
- `@media (prefers-reduced-motion)` — accessible animation
- `@media print` — print-friendly stylesheet
- `clamp(min, preferred, max)` — fluid responsive typography
- CSS-only hamburger: `<input type="checkbox">` + `:checked` + `~`
- `position: absolute; top: 100%` — dropdown panels
- `aria-label`, `aria-current`, `aria-hidden` — ARIA attributes
- Open Graph and Twitter Card meta tags
- JSON-LD structured data (`schema.org`)
- `sitemap.xml` and `robots.txt`

### Professional Practices

- **Git workflow** — Feature branches (`feat/module-N`), meaningful commit messages, push to remote
- **Separation of concerns** — HTML for structure, CSS for presentation (no inline styles)
- **Progressive enhancement** — Each module's solution is the next module's starting point
- **CSS architecture** — One file per concern (`base.css` → `layout.css` → page-specific → `enhancements.css` → `responsive.css`)
- **Accessibility-first** — WCAG AA compliance built into every stage, not retrofitted at the end
- **W3C validation** — Check HTML and CSS for errors throughout
- **Browser DevTools** — Used for debugging and responsive testing in every module

---

## 📁 Project Structure

```
mits-design-implementation-tutorial/
├── module-1/                    ✅ HTML Structure Only
│   ├── overview.md              # Module concepts & learning objectives
│   ├── workshop.md              # Step-by-step exercises
│   └── solution/                # Complete working code
│       ├── index.html
│       ├── about.html
│       ├── guide.html
│       ├── contribute.html
│       └── css/                 # All CSS files (empty in Module 1)
│
├── module-2/                    ✅ CSS Fundamentals
│   └── solution/css/
│       ├── base.css             # Reset, variables, typography, buttons
│       └── layout.css           # Header, footer, container, sections
│
├── module-3/                    ✅ Home Page
│   └── solution/
│       ├── assets/images/       # Hero image, logo
│       └── css/index.css        # Hero, cards, badges, tags — NEW
│
├── module-4/                    ✅ About Page
│   └── solution/css/about.css   # Feature grid, goals list — NEW
│
├── module-5/                    ✅ Guide & Contribute Pages
│   └── solution/css/
│       ├── guide.css            # Step counters, prerequisites — NEW
│       └── contribute.css       # Opportunity grid, contact — NEW
│
├── module-6/                    ✅ Polish
│   └── solution/css/
│       └── enhancements.css     # Animations, skip link, print — NEW
│
├── module-7/                    ✅ Responsive Design
│   └── solution/css/
│       └── responsive.css       # clamp(), hamburger, breakpoints — NEW
│
├── module-8/                    ✅ Accessibility, SEO & Deployment
│   └── solution/
│       ├── *.html               # Full SEO meta, ARIA improvements
│       ├── sitemap.xml          # NEW
│       ├── robots.txt           # NEW
│       └── css/layout.css       # logo link fix
│
├── assets/
│   └── images/
│       ├── course-cover-image.webp
│       └── logo-dark.svg
│
└── README.md                    # You are here!
```

> **Module continuity:** Each module's `solution/` folder is the starting point for the next module's workshop. This reflects real professional development — you always build on existing work.

---

## ⏱️ Time Commitment

**Total course:** ~8–12 hours across all 8 modules

| Phase            | Modules | Time       | Focus                                        |
| ---------------- | ------- | ---------- | -------------------------------------------- |
| Foundation       | 1–3     | ~3–4 hours | HTML structure, CSS system, home page        |
| Content pages    | 4–6     | ~3–4 hours | About, Guide, Contribute, polish             |
| Production-ready | 7–8     | ~3–4 hours | Responsive design, accessibility, deployment |

Each module is designed to be completed in **one focused session** with immediate visual results after every step — no session ends without something new to see in the browser.

---

## 🌟 Course Highlights

What makes this course different from typical HTML/CSS tutorials:

**Pure fundamentals** — No utility-class frameworks (no Tailwind), no component libraries (no Bootstrap). You understand every pixel.

**Dark theme** — Most tutorials use a generic white background. This course matches a real professional dark-themed platform, which is harder and more instructive.

**Real design spec** — You're not designing from scratch. You're implementing a specific design (the MITS platform interface) — exactly what professional developers do.

**One concept per module** — Module 4 introduces `auto-fit` grids. Module 5 introduces CSS counters. Module 7 introduces `clamp()`. You're never overwhelmed with five new things at once.

**Incremental steps with testing** — Every workshop breaks implementation into small pieces, each followed by a verification step. You can't accidentally do an hour of work only to discover a typo broke everything.

**Accessibility built in** — Skip links appear in Module 6. ARIA attributes in Module 8. Focus rings throughout. Accessibility isn't an afterthought — it's part of the architecture from the start.

**Live portfolio result** — The course ends with a deployed, live URL you can share on your CV, LinkedIn, or portfolio.

---

## 🤝 Contributing

Found an issue or have a suggestion? We'd love your input!

- 🐛 [Open an issue](https://github.com/marketable-it-skills/mits-course-creator/issues)
- 🔀 Submit a pull request
- 💬 Join the discussion in GitHub Discussions

---

## 💬 Support

Need help?

- 📧 **Email:** info@mits-platform.org
- 🐛 **Issues:** [GitHub Issues](https://github.com/marketable-it-skills/mits-course-creator/issues)
- 📖 **Docs:** Each module's `overview.md` explains the concepts in detail before the workshop begins

---

## 📄 License

This course is part of the **[Marketable IT Skills (MITS) Initiative](https://github.com/marketable-it-skills)** — educational resources for vocational IT training, used in competition preparation programmes across Europe.

---

**Ready to start?** → [Module 1: HTML Structure Only](module-1/overview.md) 🚀
