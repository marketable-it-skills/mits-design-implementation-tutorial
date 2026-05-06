# Module 7 Workshop: Responsive Design — Mobile First

**Goal:** Transform the polished 4-page MITS website into a fully responsive experience that works beautifully on phones, tablets, and desktops — using only CSS.

**Starting point:** Your Module 6 solution (4 pages + `enhancements.css`)

---

## Task 1: Audit the Current Site in DevTools

Before writing a single line of CSS, see *exactly* what needs fixing.

### Step 1.1: Open the Site in Your Browser

Open `index.html` from your Module 6 solution in Chrome or Firefox.

### Step 1.2: Enter Responsive Mode

- **Chrome / Edge:** Press `F12` → click the phone/tablet icon in the toolbar (or press `Ctrl+Shift+M` / `Cmd+Shift+M`)
- **Firefox:** Press `F12` → click the responsive-design icon

### Step 1.3: Test at Different Widths

Use the width dropdown to test these sizes:

| Width | What to look for |
|---|---|
| 320 px | Does text overflow? Are cards squashed? |
| 375 px | iPhone SE — most common small phone |
| 768 px | iPad portrait |
| 1024 px | iPad landscape / small laptop |

### Step 1.4: Note What's Broken

At 375 px you should observe:
- Navigation links overlap or squash together horizontally
- The hero heading is very large
- Project cards stay 3-column (cramped)
- Buttons may overflow

These are the exact problems `responsive.css` will solve.

---

## Task 2: Create `responsive.css` and Link It

### Step 2.1: Create the File

Inside `css/`, create a new file: **`responsive.css`**

Add this header comment:

```css
/* ============================================================
   RESPONSIVE DESIGN  (responsive.css)
   Module 7 — Loaded last, overrides other stylesheets
   ============================================================ */
```

> **Why last?** CSS cascades — rules defined later override earlier ones. Loading `responsive.css` after all other stylesheets means our breakpoint overrides always win without needing `!important`.

### Step 2.2: Link It in All Four Pages

In **`index.html`**, **`about.html`**, **`guide.html`**, and **`contribute.html`**, add one line after the `enhancements.css` link:

```html
<link rel="stylesheet" href="css/enhancements.css" />
<link rel="stylesheet" href="css/responsive.css" />
```

### Step 2.3: Verify

Save and refresh. Nothing should look different yet — the file is empty.

Open DevTools → Sources (Chrome) or Debugger (Firefox) → confirm `responsive.css` is loaded.

---

## Task 3: Fluid Typography with `clamp()`

Instead of overriding font sizes in every media query, use `clamp()` to make headings scale automatically.

### Step 3.1: Understand `clamp()`

```
font-size: clamp(minimum, preferred, maximum);
```

- **minimum** — the smallest the text will ever get (a `rem` value for readability)
- **preferred** — a viewport-relative value (`vw`) that scales continuously
- **maximum** — the biggest the text will ever get

Example: `clamp(1.75rem, 4vw, 2.5rem)` at various screen widths:

| Viewport | 4vw | Used value |
|---|---|---|
| 320 px | 12.8 px (< 1.75rem=28px) | **1.75rem** (minimum kicks in) |
| 600 px | 24 px (between min & max) | **24px = 1.5rem** |
| 900 px | 36 px (< 2.5rem=40px) | **36px = 2.25rem** |
| 1200 px | 48 px (> 2.5rem=40px) | **2.5rem** (maximum kicks in) |

### Step 3.2: Add Typography to `responsive.css`

```css
/* ============================================================
   RESPONSIVE TYPOGRAPHY WITH clamp()
   No media query needed — scales automatically with viewport.
   ============================================================ */

h1 {
  font-size: clamp(1.75rem, 4vw, 2.5rem);
}

h2 {
  font-size: clamp(1.25rem, 3.5vw, 2rem);
}

h3 {
  font-size: clamp(1.125rem, 2.5vw, 1.5rem);
}

/* Hero heading has a larger scale range */
.hero h1 {
  font-size: clamp(1.875rem, 6vw, 3rem);
}
```

### Step 3.3: Verify

In DevTools responsive mode, drag the viewport width from 320 px to 1200 px and watch the heading sizes smoothly scale. No jumps — just a smooth transition.

---

## Task 4: Add Hamburger HTML to All Four Pages

The CSS hamburger trick requires a hidden `<input type="checkbox">` and a visible `<label>` to be siblings of `<nav>` inside the header.

### Step 4.1: Understand the HTML Pattern

```html
<header>
  <div class="container">
    <div class="logo">...</div>

    <!-- 1. Hidden checkbox — stores the open/closed state -->
    <input type="checkbox" id="nav-toggle" class="nav-toggle">

    <!-- 2. Visible button — clicking it checks/unchecks the checkbox -->
    <label for="nav-toggle" class="nav-toggle-label" aria-label="Toggle navigation menu">
      <span></span>   <!-- top bar -->
      <span></span>   <!-- middle bar -->
      <span></span>   <!-- bottom bar -->
    </label>

    <!-- 3. Navigation — shown/hidden via CSS sibling selector -->
    <nav>
      <ul>...</ul>
    </nav>
  </div>
</header>
```

The key insight: `for="nav-toggle"` on the label connects it to the checkbox with `id="nav-toggle"`. When a user clicks the label, the checkbox is toggled — no JavaScript needed.

### Step 4.2: Update All Four HTML Files

In each file, find the header section (it looks the same in all 4):

```html
<div class="container">
  <div class="logo">
    <img src="assets/images/logo-dark.svg" alt="MITS Logo" class="logo-icon" />
    <span>MITS Platform</span>
  </div>
  <nav>
```

Add the checkbox and label **between** the logo div and the nav:

```html
<div class="container">
  <div class="logo">
    <img src="assets/images/logo-dark.svg" alt="MITS Logo" class="logo-icon" />
    <span>MITS Platform</span>
  </div>
  <input type="checkbox" id="nav-toggle" class="nav-toggle">
  <label for="nav-toggle" class="nav-toggle-label" aria-label="Toggle navigation menu">
    <span></span>
    <span></span>
    <span></span>
  </label>
  <nav>
```

Do this in: `index.html`, `about.html`, `guide.html`, `contribute.html`.

### Step 4.3: Verify

Save and refresh. On desktop, nothing should change — the checkbox and label have no visible styles yet. In DevTools, inspect the header to confirm the new elements are present.

---

## Task 5: Style the Hamburger Button (Desktop: Hidden)

Now style the hamburger elements. On desktop it stays invisible; only the CSS for mobile will make it appear.

### Step 5.1: Add the Base Styles to `responsive.css`

```css
/* ============================================================
   CSS-ONLY HAMBURGER NAVIGATION
   Technique: visually hidden checkbox + adjacent label
   The :checked state is toggled by clicking the label.
   CSS sibling selector (~) reveals the nav panel.
   ============================================================ */

/* Hide the checkbox — interaction happens via the <label> */
.nav-toggle {
  display: none;
}

/* Hamburger button — hidden on desktop, shown on mobile */
.nav-toggle-label {
  display: none;
  flex-direction: column;
  justify-content: center;
  gap: 5px;
  cursor: pointer;
  padding: var(--spacing-xs);
  border-radius: var(--radius-sm);
  /* Minimum touch target size (44×44px) */
  min-width: 44px;
  min-height: 44px;
  align-items: center;
}

/* The three hamburger lines */
.nav-toggle-label span {
  display: block;
  width: 22px;
  height: 2px;
  background-color: var(--color-text-primary);
  transition: transform 0.3s ease, opacity 0.3s ease;
  border-radius: 2px;
}
```

### Step 5.2: Verify

Nothing should be visible yet. The hamburger button uses `display: none` — it will only appear inside the `@media (max-width: 767px)` block you'll add in Task 8.

In DevTools → Elements, confirm `.nav-toggle-label` has `display: none` applied from `responsive.css`.

---

## Task 6: Animate Hamburger → X on Open

When the menu opens, the three lines should animate into an × (cross). This uses the `:checked` pseudo-class combined with the `+` adjacent sibling selector.

### Step 6.1: Understand the Selectors

```
.nav-toggle:checked + .nav-toggle-label span:nth-child(1)
         ^         ^  ^                  ^
         |         |  |                  target the 1st span
         |         |  the label immediately after the checkbox
         |         adjacent sibling selector
         when checkbox is checked
```

### Step 6.2: Add Animation to `responsive.css`

These rules go *outside* any media query — they animate whenever the checkbox is checked, regardless of screen size (though the button is only shown on mobile):

> Wait — add these inside the `@media (max-width: 767px)` block you'll create in Task 8 instead. That way the animation code is co-located with the hamburger behavior.

For now, leave a comment as a placeholder:

```css
/* Hamburger → X animation:
   Added inside @media (max-width: 767px) block in Task 8 */
```

---

## Task 7: Tablet Breakpoint — Two-Column Grids

### Step 7.1: Add the Tablet Media Query

```css
/* ============================================================
   TABLET (max-width: 1023px)
   Two-column layouts, slightly tighter spacing
   ============================================================ */

@media (max-width: 1023px) {
  /* Project cards: 3-col → 2-col */
  .projects-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  /* Hero: trim padding a little */
  .hero {
    padding: 5rem 0;
  }
}
```

> **Why only these two?** Most other grids use `auto-fit` with `minmax()` — they already reflow themselves. You only need to override the *fixed* `repeat(3, 1fr)` grid.

### Step 7.2: Verify

In DevTools, set width to 900 px. The 3-column project card grid should become 2 columns. The feature grid (About page) should already handle itself.

Check `about.html`, `index.html` at tablet width.

---

## Task 8: Mobile Breakpoint — Single Column

### Step 8.1: Open the Mobile Media Query Block

```css
/* ============================================================
   MOBILE (max-width: 767px)
   Single-column layouts, hamburger navigation
   ============================================================ */

@media (max-width: 767px) {

```

### Step 8.2: Container Padding

Less padding on narrow screens to avoid wasted space:

```css
  /* ---- CONTAINER ---- */
  .container {
    padding: 0 var(--spacing-sm); /* 16px sides instead of 24px */
  }
```

### Step 8.3: Section Spacing

```css
  /* ---- SECTIONS ---- */
  section {
    padding: var(--spacing-xl) 0; /* 48px — keeps breathing room */
  }
```

### Step 8.4: Show the Hamburger Button

```css
  /* ---- HAMBURGER — show on mobile ---- */
  .nav-toggle-label {
    display: flex;
  }
```

### Step 8.5: Hamburger → X Animation

```css
  /* Animate bars into an × when menu opens */
  .nav-toggle:checked + .nav-toggle-label span:nth-child(1) {
    transform: translateY(7px) rotate(45deg);
  }

  .nav-toggle:checked + .nav-toggle-label span:nth-child(2) {
    opacity: 0;
    transform: scaleX(0);
  }

  .nav-toggle:checked + .nav-toggle-label span:nth-child(3) {
    transform: translateY(-7px) rotate(-45deg);
  }
```

> **The math:** Each bar is 2 px tall with a 5 px gap between bars. Total height = 16 px, centre = 8 px. Bar 1's centre is at 1 px; it needs to move 7 px down. Bar 3's centre is at 15 px; it needs to move 7 px up.

### Step 8.6: Project Cards and Grids

```css
  /* ---- PROJECT CARDS: 1-column on mobile ---- */
  .projects-grid {
    grid-template-columns: 1fr;
  }

  /* ---- FOOTER ---- */
  footer .footer-grid {
    grid-template-columns: 1fr;
  }

  /* ---- OPPORTUNITY GRID (contribute page) ---- */
  .opportunities-grid {
    grid-template-columns: 1fr;
  }
```

### Step 8.7: Hero Section

```css
  /* ---- HERO ---- */
  .hero {
    padding: 4rem 0;
  }

  .hero-buttons {
    flex-wrap: wrap;
    justify-content: center;
  }

  .hero-buttons .btn {
    width: 100%;
    max-width: 280px;
    text-align: center;
  }
```

### Step 8.8: CTA Buttons

```css
  /* ---- CTA BUTTONS — stack vertically ---- */
  .cta-buttons {
    flex-direction: column;
    align-items: center;
  }

  .cta-buttons .btn {
    width: 100%;
    max-width: 280px;
    text-align: center;
  }
```

### Step 8.9: Close the Media Query

```css
} /* end @media (max-width: 767px) */
```

### Step 8.10: Verify

Set DevTools to 375 px (iPhone SE). Check:
- [ ] Container has 16 px side padding
- [ ] Project cards are single column on `index.html`
- [ ] Footer columns stack on all pages
- [ ] CTA buttons stack vertically on `guide.html`
- [ ] Hero buttons stack on `index.html`
- [ ] Hamburger icon is visible in the header (three bars)

---

## Task 9: Mobile Navigation Panel

The hamburger button is now visible, but clicking it doesn't do anything yet. Time to connect it to the nav.

### Step 9.1: Hide the Nav by Default on Mobile

Add these rules *inside* the `@media (max-width: 767px)` block (before the closing `}`):

```css
  /* ---- NAVIGATION PANEL ---- */
  /* Hidden by default; revealed when checkbox is :checked */
  nav ul {
    display: none;
    position: absolute;
    top: 100%;   /* directly below the header */
    left: 0;
    right: 0;
    flex-direction: column;
    gap: 0;
    background-color: var(--color-bg-secondary);
    border-top: 1px solid var(--color-bg-tertiary);
    border-bottom: 1px solid var(--color-bg-tertiary);
    padding: var(--spacing-xs) 0;
    z-index: 99;
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
  }
```

> **Why `position: absolute; top: 100%`?** The `<header>` already has `position: sticky`, which establishes it as the containing block for absolutely-positioned children. `top: 100%` means "start right below the header". `left: 0; right: 0` spans the full header width.

### Step 9.2: Show Nav When Checkbox Is Checked

```css
  /* ~ selects nav as a sibling that follows .nav-toggle */
  .nav-toggle:checked ~ nav ul {
    display: flex;
  }
```

### Step 9.3: Verify the Open/Close

Set DevTools to 375 px. Click the hamburger icon:
- [ ] Nav panel slides in below the header
- [ ] Nav items appear in a vertical list
- [ ] Clicking the hamburger again closes the menu
- [ ] The icon animates to × when open, back to ≡ when closed

---

## Task 10: Touch-Friendly Nav Links

Small anchor tags are hard to tap accurately on a phone. Make every nav link a full-width touch target.

### Step 10.1: Add Link Styles Inside the Mobile Block

```css
  /* ---- TOUCH-FRIENDLY NAV LINKS ---- */
  /* Full-width rows with 44px+ tap height */
  nav ul li a {
    display: block;
    padding: 0.875rem var(--spacing-md);  /* 14px top/bottom = 44px total height */
    border-radius: 0;
    font-size: 1rem;
  }

  nav ul li a:hover,
  nav ul li a.active {
    background-color: var(--color-bg-tertiary);
    color: var(--color-primary);
  }
```

> **The 44 px rule:** `padding: 0.875rem` = 14 px × 2 sides = 28 px of padding + ~20 px text height ≈ 48 px total — comfortably above the 44 px minimum.

### Step 10.2: Reduced-Motion Support for Hamburger

Outside all media queries, at the bottom of the file:

```css
/* ============================================================
   REDUCED MOTION — hamburger animation
   ============================================================ */

@media (prefers-reduced-motion: reduce) {
  .nav-toggle-label span {
    transition: none;
  }
}
```

### Step 10.3: Final Verification — Complete Responsive Checklist

Test all four pages at 375 px, 768 px, and 1200 px:

**375 px (phone)**
- [ ] Hamburger visible, nav hidden by default
- [ ] Open/close works, icon animates to ×
- [ ] Nav links are full-width, easy to tap
- [ ] Project cards: 1 column
- [ ] Hero buttons: stacked, full width
- [ ] CTA buttons: stacked, full width
- [ ] Section spacing feels comfortable
- [ ] No horizontal scroll

**768 px (tablet)**
- [ ] Full nav bar visible (no hamburger)
- [ ] Project cards: 2 columns

**1200 px (desktop)**
- [ ] Everything looks identical to Module 6

---

## Task 11: Version Control with Git

### Step 11.1: Create Feature Branch

```bash
git checkout -b feat/module-7-responsive
```

### Step 11.2: Stage and Commit

```bash
git add .
git commit -m "Complete Module 7: responsive design with CSS-only hamburger menu"
```

### Step 11.3: Merge and Push

```bash
git checkout main
git merge feat/module-7-responsive
git push origin main
```

> **Pro tip:** Make commits after completing each major task, not just at the end. Future-you (and your team) will thank present-you when reading `git log`.

---

## Summary

You've added responsive design to a desktop-first website using only CSS:

| Technique | What it does |
|---|---|
| `clamp()` | Fluid typography without media query clutter |
| CSS-only hamburger | Mobile nav toggle — zero JavaScript |
| `@media (max-width: 1023px)` | Tablet layout (2-col grids) |
| `@media (max-width: 767px)` | Mobile layout (1-col, stacked, large tap targets) |
| `position: absolute; top: 100%` | Nav panel drops below the sticky header |
| `.nav-toggle:checked ~ nav ul` | Opens the panel with a sibling selector |

The MITS website now works beautifully from a 320 px phone to a 4 K monitor — no frameworks, no JavaScript, just well-structured CSS.
