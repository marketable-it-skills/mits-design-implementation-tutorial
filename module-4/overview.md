# Module 4: About Page Styling (about.css)

## Overview

In this module, you'll style the **About MITS** page by creating `about.css` - a dedicated page-specific stylesheet that follows the same pattern you learned in Module 3. You'll style a page-title section, an impactful mission statement, a styled goal list, and a responsive feature grid showcasing four platform benefits.

By the end of this module, your About page will feel like a coherent part of the same professional website as your home page, with its own distinct visual personality while sharing the same design language (colours, spacing, typography).

## What You'll Build

Starting from Module 3's complete website (home page fully styled, other pages unstyled), you'll add:

- **Page Title Section** - Branded page header consistent with the home page's visual hierarchy
- **Mission Section** - Spacious, readable content area with an emphasis blockquote
- **Goals List** - Custom-styled list with accent-coloured bullets and clear typography
- **Feature Grid** - A 4-column CSS Grid of feature cards with icons, hover effects, and auto-responsive columns (no media queries needed)
- **Page-Specific CTA** - A call-to-action button that links to the guide page

## What is a CSS Grid with `auto-fit` + `minmax`?

Module 3 introduced CSS Grid with a fixed `repeat(3, 1fr)` layout. In this module you'll meet a more **flexible pattern**:

```css
.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: var(--spacing-lg);
}
```

- `auto-fit` - The browser fills the row with as many columns as fit
- `minmax(240px, 1fr)` - Each column is at least 240px but can grow to fill space
- **The result:** 4 columns on wide screens, 2 on medium, 1 on narrow - *without a single media query*

This is one of the most powerful modern CSS Grid patterns and you will use it often in professional work.

## Key Concepts You'll Learn

### 1. Page-Specific CSS Architecture

Learn why and how to keep page styles separate from shared styles:

```
css/
├── base.css       ← shared: variables, typography, buttons
├── layout.css     ← shared: header, footer, container
├── index.css      ← home page only  (Module 3)
├── about.css      ← about page only (THIS MODULE)
├── guide.css      ← empty for now
└── contribute.css ← empty for now
```

Adding a style to `about.css` instead of `base.css` means:
- Changes can't accidentally break other pages
- Each file has a single responsibility
- You always know where to look for a style

### 2. Section Colour Alternation

Pages feel longer and more varied when adjacent sections alternate background colours:

```css
/* Default section: dark primary */
.page-title  { background-color: var(--color-bg-secondary); }

/* Alternating section: slightly lighter */
.mission     { background-color: var(--color-bg-primary);   }
.goals       { background-color: var(--color-bg-secondary); }
.features    { background-color: var(--color-bg-primary);   }
```

This creates a "stripe" rhythm that guides the eye down the page.

### 3. Custom List Styling

CSS lets you replace default browser bullets with any character or shape:

```css
.goals-list li {
  list-style: none;
  padding-left: 2rem;
  position: relative;
}

.goals-list li::before {
  content: "→";
  position: absolute;
  left: 0;
  color: var(--color-accent);
}
```

The `::before` pseudo-element inserts content *before* the list item text without touching the HTML.

### 4. Greyscale Emoji with CSS Filter

Colourful emoji can clash with a carefully crafted dark monochrome palette. Wrapping the emoji in a `<span>` and applying `filter: grayscale(1)` desaturates it to neutral grey tones:

```html
<h3><span class="feature-icon">📚</span> Curated Projects</h3>
```

```css
.feature-icon {
  filter: grayscale(1);
}
```

This keeps the icon as a recognisable symbol while making it feel like a deliberate design choice rather than an accident.

### 5. Equal-Height Feature Cards

CSS Grid automatically stretches cards in the same row to the same height. Combine this with `align-content: start` inside the card to keep card *content* top-aligned:

```css
.feature {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
```

### 5. Hover Lift Effect (Consistent with Module 3)

Reuse the same pattern you learned for project cards:

```css
.feature:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.3);
}
```

Consistency across pages is a hallmark of professional design.

## Why This Matters

### Scalability

Every real website has multiple pages. The architecture you establish here - one CSS file per page, shared base and layout files - scales well:

- Adding a new page means adding one new CSS file
- Fixing the header means editing `layout.css` once, not six files
- Onboarding a team member is easier because the structure is predictable

### Grid vs Flexbox (When to Use Which)

| Flexbox | CSS Grid |
|---------|----------|
| One dimension (row *or* column) | Two dimensions (rows *and* columns) |
| Content-driven sizes | Layout-driven sizes |
| Navigation bar, button groups | Feature grids, card layouts |

The feature grid is a perfect CSS Grid use case: you want equal-width, equal-height cells in a 2D arrangement.

### Professional Practices

- **DRY CSS** (Don't Repeat Yourself) - Define colours once in variables, reference everywhere
- **Specificity control** - Page-scoped styles are less likely to cause unexpected overrides
- **Progressive enhancement** - The page works perfectly without `about.css`; the stylesheet *enhances* it

## What You'll Learn

By completing this module, you'll be able to:

- ✅ Create a new page-specific CSS file following established conventions
- ✅ Style a page-title section with consistent branding
- ✅ Create a spacious, readable mission/content area
- ✅ Build a custom-styled list with CSS pseudo-elements
- ✅ Build a responsive feature grid with `auto-fit` + `minmax`
- ✅ Apply consistent hover effects across multiple page types
- ✅ Use section background alternation to create visual rhythm
- ✅ Desaturate emoji icons with `filter: grayscale(1)` for a cohesive dark theme

## PRD Connection

This module implements **Page Specifications → About MITS Page**:

- **Page Title** - Branded header identifying the page
- **Mission Section** - Core "why" of the MITS platform
- **Project Goals** - Five specific goals listed clearly
- **Platform Features** - Four feature highlights (Curated Projects, Structured Learning, Industry Relevance, Multilingual Support)

**Design Requirements** maintained:

- Dark theme (`--color-bg-primary` / `--color-bg-secondary` alternation)
- Accent colour (`--color-accent: #06b6d4`) for emphasis
- Consistent spacing scale (`--spacing-*` variables)
- Typography hierarchy (H1 page title → H2 section titles → H3 card titles)

## Prerequisites

Before starting this module, you should have:

- ✅ **Completed Module 3** - Home page fully styled with `index.css`
- ✅ **Text Editor** - VS Code open with the project folder
- ✅ **Browser** - Chrome/Firefox with DevTools open (F12)
- ✅ **Git** - Repository connected to GitHub from previous modules

**Skills from Previous Modules:**

- HTML semantic markup (Module 1)
- CSS custom properties and typography (Module 2)
- Flexbox and CSS Grid basics (Modules 2-3)
- Component CSS patterns (buttons, cards) (Module 3)
- Page-specific CSS file organisation (Module 3)
- Git feature branch workflow (Modules 1-3)

## Time Estimate

⏱️ **60-75 minutes**

**Breakdown:**

- Task 1: Verify starting point & open about.css (5 min)
- Task 2: Page-title section (8 min)
- Task 3: Mission section (10 min)
- Task 4: Goals list with custom bullets (12 min)
- Task 5: Feature grid - layout (10 min)
- Task 6: Feature grid - card styling & hover (10 min)
- Task 7: Version control with Git (5 min)

## Module Structure

This module includes **7 incremental tasks**, each with testing to see immediate results:

1. **Task 1: Verify Starting Point** - Confirm project structure and open `about.css`
2. **Task 2: Page Title Section** - Style the branded page header
3. **Task 3: Mission Section** - Style mission text with visual emphasis
4. **Task 4: Goals List** - Custom bullet styling with CSS pseudo-elements
5. **Task 5: Feature Grid Layout** - Responsive grid with `auto-fit` + `minmax`
6. **Task 6: Feature Card Styling** - Card appearance and hover effects
7. **Task 7: Version Control with Git** - Commit and push your work

**Learning Approach:** Each task targets one section of the About page and is testable immediately. You'll see the page transform section by section.

## Expected Result

**Before Module 4 (Module 3 complete):**

- About page loads with working header and footer (styled)
- Page content is visible but unstyled: plain text, default browser bullets, no grid layout
- The page feels unfinished compared to the home page

**After Module 4 (This module complete):**

- **Styled page-title section** - Consistent branded header across pages
- **Readable mission section** - Well-spaced text that's easy to scan and read
- **Custom goals list** - Accent-coloured arrow bullets, generous spacing
- **Professional feature grid** - 4 cards in a responsive grid with hover effects
- **Visual consistency** - About page feels like part of the same website as the home page

## What's NOT in This Module

To keep focus:

- ❌ **Responsive design** - Grid already works at different sizes thanks to `auto-fit`, but full mobile optimisation comes in Module 7
- ❌ **Guide / Contribute page styling** - Covered in Module 5
- ❌ **Animations beyond hover** - Keyframe animations come later
- ❌ **JavaScript** - Pure HTML/CSS course

## Tips for Success

### Before You Start

1. **Open `about.html` in your browser** to see the unstyled state
2. **Keep DevTools open** - Inspect elements to understand the HTML structure before styling
3. **Compare with the home page** - Use the browser to check consistency as you build

### During the Workshop

- ✅ **Test after every step** - Refresh the browser to see each addition
- ✅ **Read the explanations** - Understanding *why* each rule works matters
- ✅ **Use variables** - `var(--color-accent)` not `#06b6d4`
- ✅ **Experiment** - Change a grid column count, spacing value, or transition speed

### Common Mistakes to Avoid

- ❌ **Styling in base.css** - Page-specific styles belong in `about.css`
- ❌ **Hardcoding colours** - Always use CSS variables defined in `base.css`
- ❌ **Forgetting `list-style: none`** - Required before `::before` pseudo-elements work as intended
- ❌ **Skipping the verify steps** - Catching errors early saves debugging time

## Ready to Start?

Head over to [workshop.md](workshop.md) to begin styling the About page!

**Remember:** The CSS you write here follows the exact same patterns as Module 3 - you're not learning new syntax, you're applying what you know to a different page. Trust the process! 🚀
