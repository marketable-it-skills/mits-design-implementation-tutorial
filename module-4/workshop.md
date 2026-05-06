# Module 4 Workshop: About Page Styling (about.css)

## Goal

Style the About MITS page from scratch using a dedicated `about.css` file. You will create a branded page-title section, a spacious mission area, a custom-bullet goals list, and a responsive feature grid with hover effects - all without touching any other CSS file.

## What You're Starting With

Before this module, you have:

- ✅ Complete HTML structure (4 pages) from Module 1
- ✅ Base CSS with variables, typography, and button components from Modules 2-3
- ✅ Layout CSS with styled header and footer from Module 2
- ✅ `index.css` fully styled from Module 3
- ✅ Empty `about.css` file ready for your styles

## What You'll Build

By the end of this workshop, your About page will have:

- ✅ A styled page-title section with consistent branding
- ✅ A readable mission section with a quoted text callout
- ✅ A goals list with custom accent-coloured arrow bullets
- ✅ A responsive 4-column feature grid (automatic columns, no media queries)
- ✅ Feature cards with icons, hover lift effects, and consistent card styling

---

## Task 1: Verify Starting Point

### Step 1.1: Check Your Project Structure

Open your project in VS Code. Your folder should look like this (module 3 complete):

```
your-project/
├── index.html
├── about.html
├── guide.html
├── contribute.html
├── assets/
│   └── images/
│       ├── logo-dark.svg
│       └── mits-hero-image.webp
└── css/
    ├── base.css         (complete - variables, typography, buttons)
    ├── layout.css       (complete - header, footer, container)
    ├── index.css        (complete - home page styles)
    ├── about.css        ← We will fill this today
    ├── guide.css        (empty - Module 5)
    └── contribute.css   (empty - Module 5)
```

If your structure matches, you're good to go!

### Step 1.2: Open about.html in Your Browser

1. Open `about.html` in your browser (drag it in, or use Live Server)
2. You should see the page with a **working header and footer** but **unstyled content** in between
3. The navigation, logo, and footer all look great - that's `layout.css` working
4. The main content (mission text, goals list, feature cards) looks plain - that's what we'll fix

### Step 1.3: Inspect the HTML Structure

Before writing any CSS, open **DevTools** (F12) and inspect the `<main>` section:

- `.page-title` section (H1 + subtitle)
- `.mission` section (H2 + two paragraphs)
- `.goals` section (H2 + `<ul class="goals-list">` + `<a class="btn">`)
- `.features` section (H2 + `<div class="features-grid">` with four `.feature` divs)

Note the class names carefully - you'll be writing CSS selectors that target these exact classes.

### Step 1.4: Open about.css

Open `css/about.css` in VS Code. It currently contains only a placeholder comment.

Delete the placeholder and add a file header comment:

```css
/* ==========================================
   ABOUT PAGE SPECIFIC STYLES (about.css)
   Module 4: About Page Styling
   ========================================== */
```

### ✅ Verify Step 1 Works

Save the file. Refresh `about.html` - it should look exactly the same (we haven't added any rules yet). This confirms `about.css` is correctly linked in the HTML.

> **Note:** The HTML file already includes `<link rel="stylesheet" href="css/about.css">` from Module 1. If styles don't appear later, this is the first thing to check.

---

## Task 2: Page Title Section

The page-title section is the first thing visitors see after the header. It should clearly identify the page and feel like it belongs to the same website as the home page.

### Step 2.1: Add Page Title Background

In `about.css`, after the file header comment, add:

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
```

**What this does:**

- `background-color: var(--color-bg-secondary)` - Slightly lighter than the main background (slate-800), creating visual separation from the header
- `padding: var(--spacing-xl) 0` - 48px top/bottom padding for a spacious feel
- `text-align: center` - Centers the heading and subtitle
- `border-bottom` - A subtle divider between the title and the next section

### ✅ Verify Step 2.1 Works

Save and refresh `about.html`. The "About MITS" heading should now be inside a slightly lighter section with good top/bottom padding.

### Step 2.2: Style the Page Title Heading

```css
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

**What this does:**

- H1 stays at `2.5rem` (consistent with `base.css` default, no change needed here)
- `.subtitle` gets the accent colour (`cyan-500`) to add a pop of colour - this creates a visual hierarchy: white H1 → cyan subtitle

### ✅ Verify Step 2.2 Works

Save and refresh. The subtitle "Real Competition Tasks for Real-World Skills" should now appear in cyan below the white H1 heading.

---

## Task 3: Mission Section

The mission section contains the core "why" of the MITS platform. It needs to be easy to read, with enough spacing to feel important.

### Step 3.1: Add Mission Section Background

```css
/* ==========================================
   MISSION SECTION
   ========================================== */

.mission {
  background-color: var(--color-bg-primary);
  padding: var(--spacing-2xl) 0;
}
```

**What this does:**

- `var(--color-bg-primary)` is the darkest background (`slate-900`) - this creates a **stripe** effect alternating with the `page-title` section (which used `bg-secondary`)
- Large `var(--spacing-2xl)` padding (64px) gives the text breathing room

### ✅ Verify Step 3.1 Works

Save and refresh. You should see a clear background colour change between the page title section and the mission section.

### Step 3.2: Style Mission Text

```css
.mission h2 {
  margin-bottom: var(--spacing-lg);
}

.mission p {
  font-size: 1.0625rem; /* 17px - slightly larger than base 16px */
  line-height: 1.8;
  max-width: 760px;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: var(--spacing-md);
}
```

**What this does:**

- `font-size: 1.0625rem` (17px) - Slightly larger than body text to signal importance
- `line-height: 1.8` - Generous line height for long-form reading comfort
- `max-width: 760px; margin: auto` - Constrains the text width for readability. Lines longer than ~70-80 characters are hard to read. Centering with auto margins keeps it aligned to the page centre.

### ✅ Verify Step 3.2 Works

Save and refresh. The mission text should now have comfortable spacing and a restrained width rather than stretching the full container.

### Step 3.3: Add First Paragraph Emphasis

The first paragraph in the mission section introduces the platform. Let's give it a subtle left border to signal importance (a common pattern in editorial design):

```css
.mission p:first-of-type {
  border-left: 3px solid var(--color-accent);
  padding-left: var(--spacing-md);
  color: var(--color-text-primary);
}
```

**What this does:**

- `p:first-of-type` selects only the **first** `<p>` inside `.mission` - no class needed
- A 3px cyan left border turns it into a subtle "blockquote" style callout
- `color: var(--color-text-primary)` (white) makes the first paragraph stand out from the slightly dimmer secondary text of the second paragraph

### ✅ Verify Step 3.3 Works

Save and refresh. The first paragraph should now have a left cyan border and appear slightly brighter than the second paragraph. Together they create a clear hierarchy.

---

## Task 4: Goals List

The goals section lists five specific platform goals using a `<ul>` with a class of `goals-list`. We'll replace the default browser bullets with styled arrow characters using CSS pseudo-elements.

### Step 4.1: Add Goals Section Background

```css
/* ==========================================
   GOALS SECTION
   ========================================== */

.goals {
  background-color: var(--color-bg-secondary);
  padding: var(--spacing-2xl) 0;
}

.goals h2 {
  margin-bottom: var(--spacing-xl);
}
```

**What this does:** Alternates back to `bg-secondary` (the same colour as `page-title`), continuing the stripe rhythm. 64px bottom padding on the section, 48px gap below the heading before the list begins.

### ✅ Verify Step 4.1 Works

Save and refresh. The goals section background should alternate back to the slightly lighter colour.

### Step 4.2: Reset List Styles

Before adding custom bullets, remove the browser defaults:

```css
.goals-list {
  list-style: none;
  margin: 0 0 var(--spacing-xl) 0;
  padding: 0;
  max-width: 760px;
  margin-left: auto;
  margin-right: auto;
}
```

**What this does:**

- `list-style: none` - Removes default browser bullet points
- `max-width: 760px; margin: auto` - Matches the mission text width for consistency
- `margin-bottom: var(--spacing-xl)` (48px) - Space before the CTA button

### ✅ Verify Step 4.2 Works

Save and refresh. The goals list bullets should disappear and the list should be centred with constrained width.

### Step 4.3: Style Individual List Items

```css
.goals-list li {
  position: relative;
  padding: var(--spacing-md) 0 var(--spacing-md) 2.5rem;
  border-bottom: 1px solid var(--color-bg-tertiary);
  font-size: 1rem;
  line-height: 1.6;
}

.goals-list li:last-child {
  border-bottom: none;
}
```

**What this does:**

- `position: relative` - Required so the `::before` pseudo-element can be positioned *relative to each list item*
- `padding-left: 2.5rem` - Makes space for the custom bullet we'll add in the next step
- `border-bottom` - Adds a separator line between items for readability
- `li:last-child` - Removes the bottom border from the last item (no border at the bottom of the list)

### ✅ Verify Step 4.3 Works

Save and refresh. The list items should now have dividing lines between them with generous padding.

### Step 4.4: Add Custom Arrow Bullets

```css
.goals-list li::before {
  content: "→";
  position: absolute;
  left: 0;
  top: var(--spacing-md);
  color: var(--color-accent);
  font-weight: 700;
  font-size: 1.125rem;
}
```

**What this does:**

- `content: "→"` - Inserts a right-arrow character as the custom bullet
- `position: absolute` - Takes the arrow out of the normal text flow (won't push list text to the right)
- `left: 0` and `top: var(--spacing-md)` - Positions it at the start of the list item, aligned with the first line of text
- `color: var(--color-accent)` - Cyan arrow to match the overall accent colour scheme

### ✅ Verify Step 4.4 Works

Save and refresh. Each list item should now have a cyan → arrow on the left, aligned with the text.

### Step 4.5: Style the Goals CTA Button

The HTML has a `<a href="guide.html" class="btn">Register Now</a>` button. Since `.btn` from `base.css` is the base style only (no colour variant), it currently has no background. Let's make it a primary button:

Open `about.html` and update the button class:

```html
<a href="guide.html" class="btn btn-primary">Register Now</a>
```

> **Why update the HTML?** The HTML intentionally used `.btn` (no variant) in Module 3 - it was a placeholder. Now that we're styling this page properly, we choose the correct variant. This is how real development works: HTML and CSS evolve together.

Then in `about.css`, centre the button:

```css
.goals .btn {
  display: block;
  width: fit-content;
  margin: 0 auto;
}
```

**What this does:** `display: block; width: fit-content; margin: auto` is the classic CSS pattern for centring an inline element horizontally without using Flexbox.

### ✅ Verify Step 4.5 Works

Save both files and refresh. The "Register Now" button should appear centred below the goals list, styled in cyan (primary button style).

---

## Task 5: Feature Grid Layout

The features section has four `.feature` divs inside a `.features-grid` container. We'll use CSS Grid with `auto-fit` and `minmax` to create a responsive layout without any media queries.

### Step 5.1: Add Features Section Background

```css
/* ==========================================
   FEATURES SECTION
   ========================================== */

.features {
  background-color: var(--color-bg-primary);
  padding: var(--spacing-2xl) 0;
}

.features h2 {
  text-align: center;
  margin-bottom: var(--spacing-xl);
}
```

**Stripe continues:** Back to dark primary background, alternating with goals (secondary). The `text-align: center` on the H2 centres the section title above the grid.

### ✅ Verify Step 5.1 Works

Save and refresh. The features section should have the darkest background.

### Step 5.2: Create the Auto-Fit Grid

```css
.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: var(--spacing-lg);
}
```

**What this does (in detail):**

- `repeat(auto-fit, ...)` - Creates as many columns as fit in the container
- `minmax(240px, 1fr)` - Each column is:
  - Minimum: 240px (cards never get smaller than this)
  - Maximum: `1fr` (columns share remaining space equally)
- On a 1200px container: `1200 / 240 = 5` → browser fills with 4 columns (our 4 cards each get ~285px)
- Resize the browser to see columns automatically collapse from 4 → 2 → 1

### ✅ Verify Step 5.2 Works

Save and refresh. The four feature divs should now be side-by-side in a grid row. Try resizing your browser - they should automatically reflow!

---

## Task 6: Feature Card Styling

Now let's style each individual feature card with the same design language as the project cards from Module 3.

### Step 6.1: Feature Card Base Styles

```css
/* ==========================================
   FEATURE CARDS
   ========================================== */

.feature {
  background-color: var(--color-bg-secondary);
  border: 1px solid var(--color-bg-tertiary);
  border-radius: var(--radius-lg);
  padding: var(--spacing-lg);
  transition: all 0.3s ease;
  display: flex;
  flex-direction: column;
}
```

**What this does:**

- Same `bg-secondary` + `bg-tertiary border` + `radius-lg` + padding combination as `.project-card` in Module 3 - **visual consistency across pages**
- `transition: all 0.3s ease` - Prepares the card for smooth hover animation
- `display: flex; flex-direction: column` - Stacks card content vertically, needed to control spacing inside the card

### ✅ Verify Step 6.1 Works

Save and refresh. The four feature cards should now have the dark-with-border card appearance, identical to the project cards on the home page.

### Step 6.2: Feature Card Hover Effect

```css
.feature:hover {
  background-color: var(--color-bg-tertiary);
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.3);
  border-color: var(--color-accent);
}
```

**What this does:**

- `translateY(-4px)` - Lifts the card 4px upward on hover
- `box-shadow` - Adds a drop shadow for depth
- `border-color: var(--color-accent)` - Border turns cyan on hover - this is a **new addition** compared to project cards, adding a bit of extra flair

### ✅ Verify Step 6.2 Works

Save and refresh. Hover over each feature card - they should lift up with a cyan border and shadow. This is the same satisfying effect as the project cards on the home page.

### Step 6.3: Feature Card Icon

The feature H3 headings include emoji icons (📚, 🎯, 💼, 🌍). To make them look intentional and consistent with the monochrome dark theme, wrap each emoji in a `<span class="feature-icon">` in `about.html`:

```html
<h3><span class="feature-icon">📚</span> Curated Projects</h3>
<h3><span class="feature-icon">🎯</span> Structured Learning</h3>
<h3><span class="feature-icon">💼</span> Industry Relevance</h3>
<h3><span class="feature-icon">🌍</span> Multilingual Support</h3>
```

Then add the heading and icon styles to `about.css`:

```css
.feature h3 {
  font-size: 1.125rem;
  margin-bottom: var(--spacing-sm);
  line-height: 1.4;
}

.feature-icon {
  filter: grayscale(1);
}
```

**What this does:**

- Wrapping the emoji in a `<span>` gives CSS a target that contains *only* the icon, not the heading text
- `filter: grayscale(1)` desaturates the emoji completely - turning colourful emoji into neutral grey tones that fit the dark monochrome palette
- The heading text is unaffected because the filter is scoped to `.feature-icon` only

### Step 6.4: Feature Card Body Text

```css
.feature p {
  font-size: 0.9375rem; /* 15px */
  line-height: 1.7;
  color: var(--color-text-secondary);
  margin: 0;
  flex-grow: 1;
}
```

**What this does:**

- `font-size: 0.9375rem` (15px) - Slightly smaller than body text, appropriate for card descriptions
- `flex-grow: 1` - In a Flex column container, this makes the paragraph expand to fill remaining space. If cards were different heights, text would push up to the top and empty space goes to the bottom (useful for equal-height cards with "read more" links)
- `margin: 0` - Removes the default paragraph bottom margin (handled by the card's padding)

### ✅ Verify Step 6.3-6.4 Works

Save and refresh. The feature cards should look polished: emoji + heading + descriptive text, consistent across all four cards. The cards should all be the same height within a row.

---

## Task 7: Version Control with Git

You've completed the About page styling! Let's save your work to Git.

### Step 7.1: Create Feature Branch

```bash
git checkout -b feat/module-4-workshop
```

This creates and switches to a new branch for your Module 4 work.

### Step 7.2: Check What Changed

```bash
git status
```

You should see:
- `about.html` (modified - updated button class)
- `css/about.css` (modified - new styles added)

### Step 7.3: Stage Your Changes

```bash
git add .
```

### Step 7.4: Commit Your Work

```bash
git commit -m "Complete Module 4: Style About page with mission, goals list, and feature grid"
```

A good commit message explains **what** was done and **why** it matters - future you will thank present you.

### Step 7.5: Merge and Push

```bash
git checkout main
git merge feat/module-4-workshop
git push origin main
```

### ✅ Verify Step 7 Works

Visit your GitHub repository. You should see the updated `about.html` and `css/about.css` in the repository.

---

## Final Check: Full Page Review

Before marking this module complete, do a full visual review of `about.html`:

### ✅ Checklist

- [ ] **Page title section** - Cyan subtitle, centred, `bg-secondary` background
- [ ] **Mission section** - First paragraph has cyan left border, text is constrained width
- [ ] **Goals list** - Custom cyan → bullets, dividing lines, centred "Register Now" button
- [ ] **Features grid** - 4 cards in a row, hover lifts with cyan border
- [ ] **Consistent with home page** - Header, footer, button styles match `index.html`
- [ ] **No broken styles** - Check other pages still look correct (`index.html` especially)

### Bonus Challenges (Optional)

If you finish early and want to explore further:

1. **Experiment with `minmax` values** - Change `minmax(240px, 1fr)` to `minmax(300px, 1fr)` and notice how the grid adjusts
2. **Try a different bullet character** - Change `"→"` to `"✓"` or `"•"` in `.goals-list li::before`
3. **Add an accent line** - Give `.mission h2` a bottom border using `border-bottom: 2px solid var(--color-accent); padding-bottom: var(--spacing-sm)`
4. **Compare both pages side by side** - Open `index.html` and `about.html` in separate browser tabs to spot any inconsistencies

---

## Summary: What You Built

In this module, you created `about.css` and styled the entire About page:

| Section | Technique Used |
|---------|---------------|
| Page Title | Section padding, accent-coloured subtitle |
| Mission | `max-width` for readability, `p:first-of-type` pseudo-class, left border callout |
| Goals | `list-style: none`, `::before` pseudo-element, custom arrow bullets |
| Features | `auto-fit` + `minmax` Grid, hover lift effect, `flex-direction: column` |

**Key CSS Concepts Practiced:**

- ✅ Page-specific CSS file organisation
- ✅ Section background alternation for visual rhythm
- ✅ CSS pseudo-elements (`::before`) for custom list bullets
- ✅ CSS Grid `auto-fit` + `minmax` for responsive layouts
- ✅ Consistent hover effects with `transform` and `box-shadow`
- ✅ Maintaining design consistency across multiple pages

**You're ready for Module 5!** Next up: styling the Guide and Contribute pages to complete the full 4-page website.
