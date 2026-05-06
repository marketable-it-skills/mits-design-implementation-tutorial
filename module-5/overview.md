# Module 5: Guide & Contribute Pages Styling

## Overview

In this module, you'll complete the styling of the entire 4-page MITS website by creating `guide.css` and `contribute.css`. The Guide page teaches a powerful new CSS technique - **CSS counters** - to auto-number the four registration steps. The Contribute page applies the `auto-fit` grid pattern from Module 4 to a new set of cards, reinforcing what you've learned. By the end, every page of your website will be fully styled and consistent.

## What You'll Build

Starting from Module 4's complete website (home + about styled, guide + contribute unstyled), you'll add:

**Guide page (`guide.css`):**
- Page-title section (consistent with About page)
- Numbered step cards powered by **CSS counters** - the step numbers are generated entirely by CSS, not HTML
- Prerequisites section with checkmark indicators and labelled skill groups
- CTA section with two buttons side-by-side and a generous gap

**Contribute page (`contribute.css`):**
- Page-title section
- Centred intro paragraph
- Responsive 2×2 grid of opportunity cards with greyscale emoji icons and inner lists
- Contact information box with aligned labels and values

## What are CSS Counters?

**CSS counters** let you generate and display incrementing numbers in CSS, without writing them in HTML. Think of them as variables that count up automatically.

There are three CSS properties you need:

```css
/* 1. Create a counter and set it to 0 */
.how-to-use {
  counter-reset: step-counter;
}

/* 2. Increment the counter for each element */
.step {
  counter-increment: step-counter;
}

/* 3. Display the current value */
.step::before {
  content: counter(step-counter);
}
```

**Why this matters:** Separation of concerns. The HTML says *what* the steps are; the CSS decides *how* they're numbered. If you add a 5th step to the HTML, the CSS automatically shows "5" - you never have to update `step-5: ` in the heading text.

This is the same principle that CSS ordered lists (`<ol>`) use internally, but made explicit so you can control every aspect of the counter's presentation.

## Key Concepts You'll Learn

### 1. CSS Counters

Three properties working together to auto-number elements:

- `counter-reset` - Declares and initialises a counter (set on the parent)
- `counter-increment` - Increments by 1 for each matching element
- `counter()` function inside `content` - Outputs the current value

```css
.how-to-use { counter-reset: step-counter; }
.step        { counter-increment: step-counter; }
.step::before { content: counter(step-counter); }
```

### 2. Flexbox for Side-by-Side Content

The step layout uses Flexbox to place the number circle next to the text content:

```css
.step {
  display: flex;
  gap: var(--spacing-lg);
  align-items: flex-start; /* top-align circle with first line of text */
}
```

`align-items: flex-start` is the key property here - without it, the circle stretches to match the full height of the text block.

### 3. CSS `::before` Pseudo-element as a Flex Child

When a container uses `display: flex`, its `::before` pseudo-element becomes a flex child. This lets you use `::before` to inject a styled element *before* the real content:

```css
.step::before {
  content: counter(step-counter); /* inject the number */
  display: flex;
  width: 3rem;
  height: 3rem;
  border-radius: 50%; /* makes it a circle */
  background-color: var(--color-accent);
}
```

### 4. `text-transform` and `letter-spacing` for Labels

Small, uppercase, spaced-out labels are a classic typographic pattern used to distinguish section sub-headers from body text:

```css
.prerequisites h3 {
  font-size: 0.875rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--color-accent);
}
```

### 5. `min-width` on Flex Children for Alignment

When displaying label/value pairs in a Flex row, a `min-width` on the label makes all values line up neatly:

```css
.contact-info strong {
  min-width: 90px; /* all labels take the same space → values align */
  flex-shrink: 0;
}
```

## Why This Matters

### Completing the Website

Before this module: 2 out of 4 pages styled. After: all 4 pages complete. You now have a full, multi-page website ready for the responsive and accessibility improvements in Modules 7-8.

### CSS Counters in the Real World

CSS counters are used in:
- **Numbered lists** - Styled legal documents, instruction manuals
- **Chapter/section numbers** - Documentation sites, books
- **Progress indicators** - Wizard UIs, onboarding flows
- **Footnote numbering** - Academic and editorial websites

Understanding counters also prepares you to understand how browsers implement `<ol>` internally.

### Reinforcing Patterns from Previous Modules

Module 5 deliberately reuses patterns from Modules 3 and 4:
- `auto-fit` grid (from Module 4) → used for opportunity cards
- `::before` pseudo-elements (from Module 4) → used for step circles
- Greyscale emoji filter (from Module 4) → applied to opportunity icons
- Section background alternation → maintained across both pages

Repetition builds mastery. Each reuse is intentional.

## What You'll Learn

By completing this module, you'll be able to:

- ✅ Use CSS counters (`counter-reset`, `counter-increment`, `counter()`) to auto-number elements
- ✅ Position a CSS `::before` pseudo-element as a Flex child
- ✅ Style instructional step layouts with numbered circle indicators
- ✅ Create labelled list sections with uppercase `letter-spacing` sub-headers
- ✅ Build a styled contact information box with aligned label/value pairs
- ✅ Apply the `auto-fit` grid pattern to a second page's card layout
- ✅ Style inner `<ul>` lists inside card components
- ✅ Complete a consistent 4-page visual design system

## PRD Connection

This module implements the two remaining **Page Specifications**:

**Guide Page:**
- How to Use MITS - Step-by-step registration walkthrough
- Prerequisites - Required skills and tools
- Call-to-Action - Registration buttons

**Contribute Page:**
- How You Can Contribute - Four audience types (Educators, Industry, Competition Organizers, Open Source)
- Get Involved - Contact details and CTA

## Prerequisites

- ✅ **Completed Module 4** - About page styled, CSS Grid and `::before` familiar
- ✅ **Text Editor** - VS Code open with the project folder
- ✅ **Browser** - Chrome/Firefox with DevTools open (F12)
- ✅ **Git** - Repository connected to GitHub

**Skills from previous modules:**
- CSS custom properties and typography
- Flexbox and CSS Grid
- `::before` pseudo-elements
- Page-specific CSS file organisation
- Section background alternation
- Greyscale emoji filter

## Time Estimate

⏱️ **75-90 minutes**

**Breakdown:**

- Task 1: Verify starting point (5 min)
- Task 2: Guide - Page title section (5 min)
- Task 3: Guide - Step cards with CSS counters (20 min)
- Task 4: Guide - Prerequisites section (10 min)
- Task 5: Guide - CTA section with buttons (8 min)
- Task 6: Contribute - Page title + intro (8 min)
- Task 7: Contribute - Opportunity grid & cards (15 min)
- Task 8: Contribute - Get Involved & contact (10 min)
- Task 9: Git workflow (5 min)

## Module Structure

1. **Task 1: Verify Starting Point** - Confirm files and open both pages in the browser
2. **Task 2: Guide - Page Title** - Reuse the page-title pattern from Module 4
3. **Task 3: Guide - Step Cards** - CSS counter setup, numbered circles, content layout
4. **Task 4: Guide - Prerequisites** - Uppercase labels, checkmark list items
5. **Task 5: Guide - CTA Section** - Centred section with properly-spaced button pair
6. **Task 6: Contribute - Page Title & Intro** - Title section + centred intro text
7. **Task 7: Contribute - Opportunity Cards** - Grid layout, card styling, inner lists
8. **Task 8: Contribute - Get Involved** - Contact info box with aligned labels
9. **Task 9: Version Control with Git** - Commit and push your completed website

## Expected Result

**Before Module 5 (Module 4 complete):**
- Guide page: header and footer styled, all content plain text
- Contribute page: header and footer styled, all content plain text

**After Module 5 (This module complete):**
- **Guide page**: Cyan numbered circles mark each step, uppercase prereq labels, two-button CTA
- **Contribute page**: 2×2 grid of opportunity cards, styled contact info box
- **All 4 pages** are now fully styled and consistent

**Milestone:** Your complete 4-page MITS website is ready for the responsive and production improvements in Modules 7-8!

## What's NOT in This Module

- ❌ **Responsive design** - Mobile layouts come in Module 7
- ❌ **Animations beyond hover** - Polish comes in Module 6
- ❌ **JavaScript** - Pure HTML/CSS course
- ❌ **Forms** - The "Register Now" button links to an external service (no form needed)

## Tips for Success

- **Open both pages side-by-side** with your existing styled pages to check consistency
- **Work through guide.css first, then contribute.css** - the guide has the new concept (counters)
- **Inspect `.step` in DevTools** after adding the counter to see the circle appear
- **If the circle is missing:** check that `counter-reset` is on the *parent* (`.how-to-use`), not on `.step`

## Ready to Start?

Head over to [workshop.md](workshop.md) to style the final two pages!

After this module you'll have a complete 4-page professional website - a real portfolio project built entirely with HTML and CSS. 🎉
