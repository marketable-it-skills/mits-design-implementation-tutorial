# Module 5 Workshop: Guide & Contribute Pages Styling

## Goal

Complete the styling of all 4 pages of the MITS website by creating `guide.css` and `contribute.css`. You will learn CSS counters to auto-number the guide steps, then apply the familiar grid and card patterns to the contribute page.

## What You're Starting With

Before this module, you have:

- ✅ `index.html` + `index.css` - Home page fully styled (Module 3)
- ✅ `about.html` + `about.css` - About page fully styled (Module 4)
- ✅ Base CSS with variables, typography, and buttons (Modules 2-3)
- ✅ Layout CSS with header and footer (Module 2)
- ✅ Empty `guide.css` and `contribute.css` ready for styling

## What You'll Build

By the end of this workshop:

- ✅ Guide page with CSS counter-generated step numbers (cyan circles)
- ✅ Prerequisites section with checkmark indicators and labelled groups
- ✅ Guide CTA with two properly-spaced buttons
- ✅ Contribute page with a responsive 2×2 opportunity card grid
- ✅ Styled contact info box with aligned labels

---

## Task 1: Verify Starting Point

### Step 1.1: Check Your Project Structure

Open your project in VS Code and confirm your CSS folder:

```
css/
├── base.css         (complete - Modules 2-3)
├── layout.css       (complete - Module 2)
├── index.css        (complete - Module 3)
├── about.css        (complete - Module 4)
├── guide.css        ← Fill this in Tasks 2-5
└── contribute.css   ← Fill this in Tasks 6-8
```

### Step 1.2: Open Both Unstyled Pages

1. Open `guide.html` in your browser
2. Open `contribute.html` in a second tab
3. Compare them to `about.html` - the header and footer are styled (from `layout.css`), but the main content is plain

### Step 1.3: Inspect the Guide HTML Structure

Open DevTools (F12) on `guide.html` and look at `<main>`:

- `.page-title` - Same class as `about.html` ✅
- `.how-to-use` - Section containing four `.step` divs
  - Each `.step` has a `.step-content` div with an `<h3>` and `<p>`
- `.prerequisites` - Two `<h3>` labels + `<ul>` lists
- `.cta` - CTA section with `.cta-buttons` containing two buttons

### Step 1.4: Open guide.css

Open `css/guide.css`. It has only a placeholder comment. Replace it with the file header:

```css
/* ==========================================
   GUIDE PAGE SPECIFIC STYLES (guide.css)
   Module 5: Guide & Contribute Pages Styling
   ========================================== */
```

### ✅ Verify Step 1 Works

Save and refresh `guide.html` - it should look unchanged (no styles added yet). This confirms `guide.css` is correctly linked.

---

## Task 2: Guide - Page Title Section

The `.page-title` section uses the **exact same HTML classes** as the About page. You can reuse the same CSS pattern - this is one of the benefits of using consistent class names across pages.

### Step 2.1: Add Page Title Styles

In `guide.css`:

```css
/* ==========================================
   PAGE TITLE SECTION
   ========================================== */

.page-title {
  background-color: var(--color-bg-secondary);
  padding: var(--spacing-xl) 0;
  text-align: center;
  border-bottom: 1px solid var(--color-bg-tertiary);
}

.page-title h1 {
  font-size: 2.5rem;
  margin-bottom: var(--spacing-sm);
}

.page-title .subtitle {
  color: var(--color-accent);
  font-size: 1.125rem;
  font-weight: 500;
}
```

> **Note:** This is identical to the `.page-title` rules in `about.css`. Since each page loads only its own CSS file, there's no shared rule - you define it in each file. If this bothers you, the fix is to move shared patterns to `layout.css` (that's a refactoring exercise you can try in Module 6).

### ✅ Verify Step 2 Works

Save and refresh `guide.html`. The "Getting Started" heading should now be in a styled `bg-secondary` section with a cyan subtitle "Your Guide to MITS Platform".

---

## Task 3: Guide - Step Cards with CSS Counters

This is the main new concept in Module 5. Instead of putting "Step 1:", "Step 2:" etc. in the HTML, we let CSS generate and display the numbers automatically.

### Step 3.1: Understand the HTML Change

Open `guide.html` and look at the step structure - notice the headings have been simplified:

```html
<!-- HTML now says the WHAT, not the step number -->
<div class="step">
  <div class="step-content">
    <h3>Create an Account</h3>
    <p>Register for a free account using...</p>
  </div>
</div>
```

The "Step 1:", "Step 2:" etc. text has been removed. CSS will generate the number circles instead. This is **separation of concerns**: HTML describes content, CSS describes presentation.

### Step 3.2: Add the How-to-Use Section Background

```css
/* ==========================================
   HOW TO USE SECTION (CSS COUNTER STEPS)
   ========================================== */

.how-to-use {
  background-color: var(--color-bg-primary);
  padding: var(--spacing-2xl) 0;
  counter-reset: step-counter;
}

.how-to-use h2 {
  text-align: center;
  margin-bottom: var(--spacing-xl);
}
```

**What `counter-reset: step-counter` does:** Declares a new counter named `step-counter` and sets its value to `0`. This must be on the **parent** element that contains all the items to be counted.

### ✅ Verify Step 3.2 Works

Save and refresh. The "How to Use MITS Platform" section should now have the dark background.

### Step 3.3: Increment the Counter per Step

```css
.step {
  display: flex;
  gap: var(--spacing-lg);
  align-items: flex-start;
  padding-bottom: var(--spacing-xl);
  margin-bottom: var(--spacing-xl);
  border-bottom: 1px solid var(--color-bg-tertiary);
  counter-increment: step-counter;
}

.step:last-child {
  border-bottom: none;
  margin-bottom: 0;
  padding-bottom: 0;
}
```

**What `counter-increment: step-counter` does:** Every time the browser encounters a `.step` element, it adds 1 to `step-counter`. After 4 steps, the counter will have been incremented to 1, 2, 3, 4 respectively.

`display: flex` + `align-items: flex-start` sets up the row layout: number circle on the left, content block on the right, both top-aligned.

### ✅ Verify Step 3.3 Works

Save and refresh. The four step items should now be laid out horizontally (but the number circle isn't visible yet - that comes next). You'll see the text content shifted to the right as if something is beside it - that's the flex layout working, ready for the `::before` circle.

### Step 3.4: Display the Number Circle with `::before`

```css
.step::before {
  content: counter(step-counter);
  display: flex;
  align-items: center;
  justify-content: center;
  min-width: 3rem;
  height: 3rem;
  border-radius: 50%;
  background-color: var(--color-accent);
  color: var(--color-bg-primary);
  font-weight: 700;
  font-size: 1.125rem;
  flex-shrink: 0;
  margin-top: 0.125rem;
}
```

**What this does:**

- `content: counter(step-counter)` - Outputs the current counter value as text ("1", "2", "3", "4")
- `display: flex` + `align-items: center` + `justify-content: center` - Centres the number inside the circle
- `min-width: 3rem; height: 3rem; border-radius: 50%` - Creates the circle (equal width and height → perfect circle)
- `background-color: var(--color-accent)` - Cyan background
- `color: var(--color-bg-primary)` - Dark text on cyan background (high contrast)
- `flex-shrink: 0` - Prevents the circle from shrinking if text is long
- `margin-top: 0.125rem` - Micro-adjustment to optically align the circle with the H3 first line

**Why `::before` becomes a flex child:** Because `.step` is a `display: flex` container, its pseudo-element `::before` is automatically a flex child - it participates in the flex layout alongside `.step-content`.

### ✅ Verify Step 3.4 Works

Save and refresh. You should now see **four cyan circles with numbers 1, 2, 3, 4** down the left side of each step, with the step text to the right. This is the power of CSS counters!

Open DevTools and try adding a 5th step in the HTML - notice the CSS automatically shows "5" without you writing anything.

### Step 3.5: Style the Step Content

```css
.step-content {
  flex: 1;
}

.step-content h3 {
  font-size: 1.125rem;
  margin-bottom: var(--spacing-xs);
}

.step-content p {
  margin: 0;
  line-height: 1.7;
  color: var(--color-text-secondary);
}
```

**What `flex: 1` does:** Makes `.step-content` expand to fill all remaining space in the row (after the fixed-width `::before` circle takes its space). This is shorthand for `flex-grow: 1; flex-shrink: 1; flex-basis: 0`.

### ✅ Verify Step 3.5 Works

Save and refresh. The step headings and paragraphs should now be properly styled with clear typography. The full step layout is complete.

---

## Task 4: Guide - Prerequisites Section

The prerequisites section has two sub-groups: "Required Skills" and "Technical Requirements". We'll style them with uppercase accent labels and checkmark list items.

### Step 4.1: Add Prerequisites Section Background

```css
/* ==========================================
   PREREQUISITES SECTION
   ========================================== */

.prerequisites {
  background-color: var(--color-bg-secondary);
  padding: var(--spacing-2xl) 0;
}

.prerequisites h2 {
  margin-bottom: var(--spacing-xl);
}
```

The section alternates back to `bg-secondary`, continuing the page rhythm.

### ✅ Verify Step 4.1 Works

Save and refresh. The prerequisites section should have the slightly lighter background.

### Step 4.2: Style the Sub-Section Labels

```css
.prerequisites h3 {
  font-size: 0.875rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--color-accent);
  margin-bottom: var(--spacing-sm);
}
```

**What this does:**

- `text-transform: uppercase` - Converts the heading text to all caps without changing the HTML
- `letter-spacing: 0.08em` - Adds space between letters (tracked text), a classic typographic technique for small caps that aids readability
- `font-size: 0.875rem` (14px) - Small size signals "label" rather than "section title"
- Together: a small, spaced, cyan, uppercase label - a professional pattern used in many design systems

### ✅ Verify Step 4.2 Works

Save and refresh. "Required Skills" and "Technical Requirements" should now appear as small cyan uppercase labels.

### Step 4.3: Style the List Items with Checkmarks

```css
.prerequisites ul {
  list-style: none;
  padding: 0;
  margin-bottom: var(--spacing-xl);
}

.prerequisites ul li {
  position: relative;
  padding: var(--spacing-sm) 0 var(--spacing-sm) 1.75rem;
  border-bottom: 1px solid var(--color-bg-tertiary);
  font-size: 0.9375rem;
  line-height: 1.6;
}

.prerequisites ul li:last-child {
  border-bottom: none;
}

.prerequisites ul li::before {
  content: "✓";
  position: absolute;
  left: 0;
  color: var(--color-accent);
  font-weight: 700;
}
```

This uses the same `::before` custom bullet technique from Module 4 - but with `✓` instead of `→`. A checkmark feels appropriate for a "requirements" list.

### ✅ Verify Step 4.3 Works

Save and refresh. Both lists should now have cyan checkmarks on each item, with dividing lines between items. The pattern should look similar to the goals list on the About page.

---

## Task 5: Guide - CTA Section

The call-to-action section has two buttons: "Register Now" (primary) and "Browse Projects" (secondary). These need a Flexbox container with proper gap.

### Step 5.1: Style the CTA Section

```css
/* ==========================================
   CTA SECTION
   ========================================== */

.cta {
  background-color: var(--color-bg-primary);
  padding: var(--spacing-2xl) 0;
  text-align: center;
}

.cta h2 {
  margin-bottom: var(--spacing-md);
}

.cta p {
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.7;
}
```

### ✅ Verify Step 5.1 Works

Save and refresh. The "Ready to Start?" section should now have the dark background with centred text.

### Step 5.2: Style the Button Row

```css
.cta-buttons {
  display: flex;
  justify-content: center;
  gap: var(--spacing-lg);
  flex-wrap: wrap;
  margin-top: var(--spacing-xl);
}
```

**What this does:**

- `display: flex` - Places buttons side-by-side
- `justify-content: center` - Centres the row horizontally
- `gap: var(--spacing-lg)` - **32px gap** between the buttons (this was the missing piece the user noticed)
- `flex-wrap: wrap` - Allows buttons to stack on very narrow screens

### ✅ Verify Step 5.2 Works

Save and refresh. The "Register Now" and "Browse Projects" buttons should now be centred side-by-side with a comfortable gap between them. The Guide page is complete!

---

## Task 6: Contribute - Page Title & Intro

Now open `contribute.html` and start `contribute.css`.

### Step 6.1: Open contribute.css

Open `css/contribute.css` and replace the placeholder with the file header:

```css
/* ==========================================
   CONTRIBUTE PAGE SPECIFIC STYLES (contribute.css)
   Module 5: Guide & Contribute Pages Styling
   ========================================== */
```

### Step 6.2: Page Title Section

```css
/* ==========================================
   PAGE TITLE SECTION
   ========================================== */

.page-title {
  background-color: var(--color-bg-secondary);
  padding: var(--spacing-xl) 0;
  text-align: center;
  border-bottom: 1px solid var(--color-bg-tertiary);
}

.page-title h1 {
  font-size: 2.5rem;
  margin-bottom: var(--spacing-sm);
}

.page-title .subtitle {
  color: var(--color-accent);
  font-size: 1.125rem;
  font-weight: 500;
}
```

### ✅ Verify Step 6.2 Works

Save and refresh `contribute.html`. The "Collaborate with MITS" heading and cyan subtitle should now be styled in the `bg-secondary` section.

### Step 6.3: Intro Section

```css
/* ==========================================
   INTRO SECTION
   ========================================== */

.intro {
  background-color: var(--color-bg-primary);
  padding: var(--spacing-2xl) 0;
  text-align: center;
}

.intro p {
  font-size: 1.0625rem;
  line-height: 1.8;
  max-width: 760px;
  margin: 0 auto;
}
```

The `max-width` + `margin: auto` centres the paragraph at a readable width - the same pattern used for mission text on the About page.

### ✅ Verify Step 6.3 Works

Save and refresh. The intro paragraph should be centred with constrained width against the dark primary background.

---

## Task 7: Contribute - Opportunity Cards

The four opportunity cards need to be laid out in a responsive grid. Look at `contribute.html` - the cards are already inside an `<div class="opportunities-grid">` wrapper (added when preparing Module 5), ready for Grid styling.

### Step 7.1: Add Opportunities Section Background

```css
/* ==========================================
   OPPORTUNITIES SECTION
   ========================================== */

.opportunities {
  background-color: var(--color-bg-secondary);
  padding: var(--spacing-2xl) 0;
}

.opportunities h2 {
  text-align: center;
  margin-bottom: var(--spacing-xl);
}
```

### ✅ Verify Step 7.1 Works

Save and refresh. The "How You Can Contribute" section should now have the `bg-secondary` background (stripe continues).

### Step 7.2: Create the Opportunity Grid

```css
.opportunities-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: var(--spacing-lg);
}
```

This is the same `auto-fit` + `minmax` pattern from Module 4's feature grid. The 280px minimum is slightly wider than the 240px used on the about page - appropriate for cards that contain lists.

### ✅ Verify Step 7.2 Works

Save and refresh. The four opportunity divs should now be side-by-side in a 2×2 grid (or 4 across if your viewport is wide). Try resizing the browser to see them automatically reflow.

### Step 7.3: Style the Opportunity Cards

```css
/* ==========================================
   OPPORTUNITY CARDS
   ========================================== */

.opportunity {
  background-color: var(--color-bg-primary);
  border: 1px solid var(--color-bg-tertiary);
  border-radius: var(--radius-lg);
  padding: var(--spacing-lg);
  transition: all 0.3s ease;
  display: flex;
  flex-direction: column;
}

.opportunity:hover {
  border-color: var(--color-accent);
  transform: translateY(-2px);
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.2);
}
```

**Notice the hover effect:** `translateY(-2px)` is subtler than the 4px lift on feature cards (Module 4). These cards are denser (they contain lists), so a smaller lift keeps the interaction feeling proportional.

### ✅ Verify Step 7.3 Works

Save and refresh. The four cards should appear on the slightly lighter `bg-secondary` background, with `bg-primary` cards inside. Hover over a card to see the cyan border appear and the slight lift.

### Step 7.4: Style the Card Icon, Heading, and Body Text

```css
.opportunity-icon {
  filter: grayscale(1);
}

.opportunity h3 {
  font-size: 1.125rem;
  margin-bottom: var(--spacing-sm);
  line-height: 1.4;
}

.opportunity > p {
  font-size: 0.9375rem;
  line-height: 1.7;
  color: var(--color-text-secondary);
  margin-bottom: var(--spacing-md);
}
```

`.opportunity > p` uses the **direct child combinator** (`>`) to target only the paragraph *directly inside* `.opportunity`, not paragraphs inside the `<ul>` (if there were any). This is a specificity safety measure.

### ✅ Verify Step 7.4 Works

Save and refresh. The greyscale emoji icons, headings, and body text should all be styled. The cards should look complete in the upper half.

### Step 7.5: Style the Inner List

Each opportunity card has a `<ul>` with four bullet points. Let's style them as a minimal list at the bottom of the card:

```css
.opportunity ul {
  list-style: none;
  padding: 0;
  margin: 0;
  margin-top: auto;
}

.opportunity ul li {
  position: relative;
  padding: var(--spacing-xs) 0 var(--spacing-xs) 1.25rem;
  border-bottom: 1px solid var(--color-bg-tertiary);
  font-size: 0.875rem;
  color: var(--color-text-tertiary);
  line-height: 1.5;
}

.opportunity ul li:last-child {
  border-bottom: none;
  padding-bottom: 0;
}

.opportunity ul li::before {
  content: "–";
  position: absolute;
  left: 0;
  color: var(--color-text-tertiary);
}
```

**What `margin-top: auto` does on `.opportunity ul`:** Because `.opportunity` is a `flex-direction: column` container, `margin-top: auto` pushes the list to the *bottom* of the card. If two cards in the same row have different amounts of paragraph text, the lists still align at the bottom. This is the same `flex-grow` / `margin-top: auto` technique used to align elements in flex columns.

### ✅ Verify Step 7.5 Works

Save and refresh. The list items inside each card should now be styled with dash (`–`) bullets, muted grey text, and dividing lines. Hover over the cards again to confirm the border colour change still works.

---

## Task 8: Contribute - Get Involved Section

The final section has a heading, a paragraph, a contact info box, and a CTA button.

### Step 8.1: Style the Get Involved Section

```css
/* ==========================================
   GET INVOLVED SECTION
   ========================================== */

.get-involved {
  background-color: var(--color-bg-primary);
  padding: var(--spacing-2xl) 0;
  text-align: center;
}

.get-involved h2 {
  margin-bottom: var(--spacing-md);
}

.get-involved > .container > p {
  max-width: 600px;
  margin: 0 auto var(--spacing-xl);
  line-height: 1.7;
}
```

> **Note:** `.get-involved > .container > p` uses two `>` combinators. This specifically targets only the `<p>` that is a direct child of `.container`, which is a direct child of `.get-involved`. This prevents the selector accidentally matching paragraphs inside `.contact-info`.

### ✅ Verify Step 8.1 Works

Save and refresh. The introductory paragraph in "Get Involved" should be centred with max-width.

### Step 8.2: Style the Contact Info Box

```css
.contact-info {
  background-color: var(--color-bg-secondary);
  border: 1px solid var(--color-bg-tertiary);
  border-radius: var(--radius-lg);
  padding: var(--spacing-lg);
  max-width: 480px;
  margin: 0 auto var(--spacing-xl);
  text-align: left;
}
```

**Why `text-align: left` on `.contact-info`:** The parent `.get-involved` sets `text-align: center`. The contact box should be centred on the page, but the text *inside* it should be left-aligned for readability. Setting `text-align: left` overrides the inherited value.

### ✅ Verify Step 8.2 Works

Save and refresh. A styled box should appear below the intro paragraph, containing the email, GitHub, and Discussions info.

### Step 8.3: Align Contact Labels and Values

```css
.contact-info p {
  display: flex;
  align-items: baseline;
  gap: var(--spacing-sm);
  margin-bottom: var(--spacing-sm);
  font-size: 0.9375rem;
}

.contact-info p:last-child {
  margin-bottom: 0;
}

.contact-info strong {
  color: var(--color-text-primary);
  min-width: 90px;
  flex-shrink: 0;
}
```

**What `align-items: baseline` does:** Aligns the label and value on their *text baseline* (the invisible line text sits on). This looks more refined than `align-items: center` when labels and values have different amounts of text.

**What `min-width: 90px` on `strong` does:** Forces all labels ("Email:", "GitHub:", "Discussions:") to take the same minimum width. This makes the values after them align in a clean column - like a table, but built with Flexbox.

### ✅ Verify Step 8.3 Works

Save and refresh. The three contact rows inside the box should now have their labels left-aligned in a neat column, with values aligning to the right of each label. The "Email:", "GitHub:", and "Discussions:" labels should line up perfectly.

### Step 8.4: Centre the CTA Button

The "Contact Us" button in the HTML has `class="btn btn-primary"`. Since the section is `text-align: center`, `display: inline-block` buttons will centre automatically. Verify this looks correct.

### ✅ Verify Step 8.4 Works

Save and refresh. The "Contact Us" button should be centred below the contact info box.

---

## Task 9: Version Control with Git

All four pages are now styled! Let's save this milestone to Git.

### Step 9.1: Create Feature Branch

```bash
git checkout -b feat/module-5-workshop
```

### Step 9.2: Check What Changed

```bash
git status
```

You should see:
- `guide.html` (modified - step content restructured)
- `contribute.html` (modified - grid wrapper + icon spans added)
- `css/guide.css` (modified - fully styled)
- `css/contribute.css` (modified - fully styled)

### Step 9.3: Commit Your Work

```bash
git add .
git commit -m "Complete Module 5: Style Guide and Contribute pages, complete 4-page website"
```

### Step 9.4: Merge and Push

```bash
git checkout main
git merge feat/module-5-workshop
git push origin main
```

### ✅ Verify Step 9 Works

Visit your GitHub repository. All four pages and their CSS files should be visible and up to date.

---

## Final Check: Full Website Review

Before marking this module complete, open every page and verify:

### ✅ Guide Page Checklist

- [ ] Page title: cyan subtitle, `bg-secondary` background
- [ ] Four steps: cyan numbered circles (1-4), headings without "Step N:" text
- [ ] Prerequisites: cyan uppercase labels ("REQUIRED SKILLS", "TECHNICAL REQUIREMENTS")
- [ ] Prerequisites: checkmark (✓) bullets on each list item
- [ ] CTA: "Register Now" and "Browse Projects" side-by-side with a clear gap

### ✅ Contribute Page Checklist

- [ ] Page title: cyan subtitle, `bg-secondary` background
- [ ] Intro: centred paragraph with `max-width`
- [ ] Opportunities: 4 cards in a responsive grid, greyscale emoji icons
- [ ] Cards: hover border turns cyan with slight lift
- [ ] Inner lists: dash bullets, muted text, dividing lines
- [ ] Contact box: labels and values neatly aligned
- [ ] "Contact Us" button: centred below the contact box

### ✅ Cross-Page Consistency

- [ ] All 4 pages share the same header and footer appearance
- [ ] Page title sections look identical across About, Guide, and Contribute
- [ ] Card hover effects feel consistent across all pages
- [ ] No page looks noticeably different from the others

---

## Summary: What You Built

This module completed the 4-page MITS website:

| File | New Technique | Result |
|------|---------------|--------|
| `guide.css` | CSS counters (`counter-reset`, `counter-increment`, `counter()`) | Auto-numbered step circles |
| `guide.css` | Flex `::before` as numbered circle | Cyan badge before each step |
| `guide.css` | `text-transform: uppercase` + `letter-spacing` | Styled prereq labels |
| `guide.css` | `flex-wrap` + `gap: var(--spacing-lg)` | Properly-spaced button pair |
| `contribute.css` | `auto-fit` grid (reinforced from Module 4) | Responsive opportunity cards |
| `contribute.css` | Direct child combinator (`>`) | Precise paragraph targeting |
| `contribute.css` | `align-items: baseline` + `min-width` | Aligned label/value contact rows |
| `contribute.css` | `margin-top: auto` on list | Bottom-aligned lists in flex column |

**You now have a complete, professionally styled 4-page website built entirely with HTML and CSS.**

**Ready for Module 6!** Next up: polish and advanced CSS techniques - smooth scroll, animations, print styles.
