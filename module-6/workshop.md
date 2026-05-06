# Module 6 Workshop: Polish & Advanced CSS Techniques

## Goal

Add professional polish to your complete 4-page website by creating `enhancements.css` - a single file of site-wide improvements including smooth scroll, a skip link, keyboard focus rings, button press feedback, a page fade-in animation, reduced-motion support, and print styles.

## What You're Starting With

Before this module, you have:

- ✅ All 4 pages fully styled (Modules 3-5)
- ✅ `base.css`, `layout.css`, and four page-specific CSS files
- ✅ Professional design with consistent components and spacing

## What You'll Build

By the end of this workshop:

- ✅ `enhancements.css` linked on all 4 pages
- ✅ Smooth scrolling on all anchor links
- ✅ Skip-to-content link for keyboard/screen reader users
- ✅ Branded cyan focus rings for keyboard navigation
- ✅ Button `:active` press feedback
- ✅ Page fade-in animation on every page load
- ✅ Full animation shutdown for reduced-motion users
- ✅ Clean, print-friendly output

---

## Task 1: Create enhancements.css

### Step 1.1: Create the File

In your project's `css/` folder, create a new file: `css/enhancements.css`

Your CSS folder should now look like this:

```
css/
├── base.css
├── layout.css
├── index.css
├── about.css
├── guide.css
├── contribute.css
└── enhancements.css   ← NEW
```

### Step 1.2: Add the File Header

Open `enhancements.css` and add the file header:

```css
/* ==========================================
   ENHANCEMENTS (enhancements.css)
   Module 6: Polish & Advanced CSS Techniques
   Site-wide progressive enhancements - linked by all pages
   ========================================== */
```

### ✅ Verify Step 1 Works

The file exists and is ready. No styles yet, so no visual change - that comes in the next task.

---

## Task 2: Link enhancements.css in All Pages

`enhancements.css` needs to be the **last stylesheet** in every HTML file - it overrides earlier layers where needed.

### Step 2.1: Update index.html

Open `index.html`. In `<head>`, add the new link **after** `index.css`:

```html
<link rel="stylesheet" href="css/base.css" />
<link rel="stylesheet" href="css/layout.css" />
<link rel="stylesheet" href="css/index.css" />
<link rel="stylesheet" href="css/enhancements.css" />
```

### Step 2.2: Add Skip Link HTML to index.html

Immediately after `<body>` (before the header), add:

```html
<body>
  <a href="#main-content" class="skip-link">Skip to main content</a>
  <!-- Header with Navigation -->
```

### Step 2.3: Add id to the main element in index.html

Find `<main>` and add `id="main-content"`:

```html
<main id="main-content">
```

### Step 2.4: Repeat for about.html

```html
<!-- In <head>, after about.css: -->
<link rel="stylesheet" href="css/enhancements.css" />
```

```html
<!-- In <body>, before the header: -->
<a href="#main-content" class="skip-link">Skip to main content</a>
```

```html
<!-- On the <main> tag: -->
<main id="main-content">
```

### Step 2.5: Repeat for guide.html

Same three changes: add `enhancements.css` link, skip link, `id="main-content"`.

### Step 2.6: Repeat for contribute.html

Same three changes.

### ✅ Verify Step 2 Works

Open any page in your browser. It should look **identical** to before (enhancements.css is empty). Open DevTools → Network tab, refresh - you should see `enhancements.css` loaded with a 200 status.

---

## Task 3: Smooth Scroll

One line gives you smooth scrolling everywhere - for all anchor links (`href="#section"`) and for the skip link you'll add next.

### Step 3.1: Add Smooth Scroll

In `enhancements.css`:

```css
/* ==========================================
   SMOOTH SCROLLING
   ========================================== */

html {
  scroll-behavior: smooth;
}
```

**What this does:** Instructs the browser to animate the scroll position instead of jumping instantly when navigating to an anchor (`href="#section-id"`).

### ✅ Verify Step 3 Works

Open `index.html`. If your footer has anchor links, try clicking them. If not, test it properly after Task 4 - the skip link will give you a perfect test case.

> **Note:** `scroll-behavior: smooth` is automatically disabled by the `prefers-reduced-motion` rule we'll add in Task 8. It's safe to add it now.

---

## Task 4: Skip-to-Content Link

The **skip link** is a visually hidden anchor that appears when a keyboard user presses Tab on the page. It lets them jump straight to the main content without tabbing through every navigation item on every page.

### Step 4.1: How It Works (HTML is Already Done)

You added `<a href="#main-content" class="skip-link">` in Task 2. The CSS now needs to:
1. Hide it visually (off-screen, not `display: none` - that would make it untabbable)
2. Slide it in when focused

### Step 4.2: Add the Skip Link Styles

```css
/* ==========================================
   SKIP TO CONTENT LINK (ACCESSIBILITY)
   ========================================== */

.skip-link {
  position: absolute;
  top: -100%;
  left: var(--spacing-sm);
  background-color: var(--color-accent);
  color: var(--color-bg-primary);
  padding: var(--spacing-sm) var(--spacing-md);
  border-radius: 0 0 var(--radius-md) var(--radius-md);
  font-weight: 600;
  font-size: 0.9375rem;
  z-index: 999;
  text-decoration: none;
  transition: top 0.2s ease;
}

.skip-link:focus {
  top: 0;
}
```

**What this does:**

- `position: absolute; top: -100%` - Moves the link completely above the viewport. It's in the DOM and tabbable, just not visible.
- `transition: top 0.2s ease` - Animates it sliding down when focused
- `.skip-link:focus { top: 0 }` - When Tab focuses this link, it drops into view at the very top of the page
- `z-index: 999` - Ensures it appears above the sticky header
- `border-radius: 0 0 ...` - Rounds only the bottom corners (it connects to the top of the viewport)

### ✅ Verify Step 4 Works

1. Open any page in the browser
2. Press **Tab** once
3. A cyan "Skip to main content" button should appear at the top
4. Press **Enter** - the page should scroll to the main content area

If you don't see it, check:
- The skip link HTML is the first child of `<body>` (before the header)
- `id="main-content"` is on the `<main>` tag

---

## Task 5: Keyboard Focus Rings

By default, browsers show a blue or orange outline on focused elements. We'll replace this with our branded cyan outline - but **only for keyboard navigation**, not for mouse clicks.

### Step 5.1: Remove Default Outlines

```css
/* ==========================================
   FOCUS VISIBLE (KEYBOARD NAVIGATION)
   ========================================== */

:focus {
  outline: none;
}
```

> **Important:** This removes the outline for ALL focus, including keyboard. The next step adds it back only for keyboard navigation via `:focus-visible`.

### Step 5.2: Add Branded Focus Ring for Keyboard Only

```css
:focus-visible {
  outline: 2px solid var(--color-accent);
  outline-offset: 3px;
  border-radius: var(--radius-sm);
}
```

**The key difference:**

- `:focus` triggers when any element receives focus (mouse click OR keyboard Tab)
- `:focus-visible` triggers only when the browser determines focus should be visible (keyboard navigation, not mouse clicks)

**Result:** Mouse users clicking buttons see no outline change (cleaner look). Keyboard users tabbing through the page see a clear cyan ring (accessible navigation).

### ✅ Verify Step 5 Works

**Test keyboard navigation:**
1. Press Tab repeatedly and watch the focused element - you should see a clean cyan outline moving through the navigation links and buttons
2. Click a button with the mouse - no outline should appear after clicking

**Test focus ring on navigation:**
- Tab to the header navigation links - cyan outline on each link
- Tab to any button - cyan outline appears

---

## Task 6: Button Active State

The `:active` pseudo-class applies while an element is being held down. A subtle scale effect gives physical "press" feedback.

### Step 6.1: Add the Active State

```css
/* ==========================================
   BUTTON ACTIVE STATE
   ========================================== */

.btn:active {
  transform: translateY(0) scale(0.97);
  box-shadow: none;
  transition-duration: 0.1s;
}
```

**What this does:**

- `scale(0.97)` - Scales the button to 97% of its size (barely perceptible, but feels right)
- `translateY(0)` - Overrides the hover `translateY(-2px)` lift to bring it back to baseline (pressing down, not up)
- `box-shadow: none` - Removes the hover glow when pressed (clicked)
- `transition-duration: 0.1s` - Very fast response - pressing should feel instant

### ✅ Verify Step 6 Works

Open any page and click a button (the "Register Now" or "Browse Projects" buttons work well). Hold the mouse button down - you should see the button very slightly shrink. Release - it springs back. The effect is subtle but gives the interaction a satisfying, polished feel.

---

## Task 7: Page Fade-In Animation

A gentle fade-in on the `main` content area makes page loads feel more intentional and polished.

### Step 7.1: Define the Keyframe Animation

```css
/* ==========================================
   PAGE FADE-IN ANIMATION
   ========================================== */

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
```

**What `@keyframes` does:** Defines an animation as a sequence of style states. `from` is the starting state, `to` is the ending state. The browser interpolates between them.

- `opacity: 0 → 1` - Content fades in from invisible
- `translateY(20px → 0)` - Content rises up 20px as it appears (subtle upward movement)

### Step 7.2: Apply the Animation to main

```css
main {
  animation: fadeInUp 0.5s ease both;
}
```

**Breaking down the `animation` shorthand:**

| Value | Property | Meaning |
|-------|----------|---------|
| `fadeInUp` | `animation-name` | Which `@keyframes` to use |
| `0.5s` | `animation-duration` | Half a second |
| `ease` | `animation-timing-function` | Starts fast, slows at the end |
| `both` | `animation-fill-mode` | Apply `from` state before animation starts, keep `to` state after it ends |

The `both` fill mode is important - without it, `main` would be fully visible for a flash before the animation begins, then jump to `opacity: 0` and animate.

### ✅ Verify Step 7 Works

Reload any page. The main content should smoothly fade up from below. The header and footer don't animate (they're outside `<main>`), which is correct - they're "chrome" that should always be visible.

Open DevTools → **Elements** panel → find `<main>`. You can disable the animation temporarily by removing the `animation` property in DevTools to compare the before/after feel.

---

## Task 8: Respect Reduced Motion Preferences

Some users experience dizziness or nausea from animations due to vestibular disorders. Operating systems provide a "reduce motion" setting that CSS can detect. We must honour it.

### Step 8.1: Add the Reduced Motion Media Query

```css
/* ==========================================
   RESPECT USER'S MOTION PREFERENCES
   ========================================== */

@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

**What this does:**

- `@media (prefers-reduced-motion: reduce)` - Activates when the user has enabled "Reduce Motion" in their OS settings
- Setting durations to `0.01ms` instead of `0` ensures the final animation state is immediately applied (content ends up visible), and any JavaScript listening for `animationend` events still fires
- `!important` - Overrides any animation/transition declarations in other stylesheets
- `scroll-behavior: auto` - Disables the smooth scroll from Task 3

### ✅ Verify Step 8 Works

**On Windows:** Settings → Accessibility → Visual Effects → turn off "Animation effects"  
**On macOS:** System Settings → Accessibility → Display → check "Reduce motion"

Reload the page - the `main` content should appear instantly without fading in.

> **Tip:** You can also test this in Chrome DevTools: open DevTools → Rendering tab → check "Emulate CSS media feature prefers-reduced-motion: reduce"

Remember to turn the OS setting back on after testing!

---

## Task 9: Print Styles

Press Ctrl/Cmd + P on any of your pages right now - the dark theme will appear in the print preview, making it unreadable on paper. The `@media print` query lets you define completely different styles for printing.

### Step 9.1: Hide Non-Content Elements

```css
/* ==========================================
   PRINT STYLES
   ========================================== */

@media print {
  header,
  footer,
  nav,
  .btn,
  .skip-link {
    display: none !important;
  }
```

**Why hide these?**

- `header` + `nav` - Navigation is useless on paper (you can't click links)
- `footer` - Often contains contact info already shown in the page body
- `.btn` - Buttons do nothing in print; they look strange on paper
- `.skip-link` - Screen-only accessibility feature

### Step 9.2: Reset Colours for Print

```css
  body {
    background: white;
    color: black;
  }

  h1, h2, h3, h4 {
    color: black;
  }

  a {
    color: black;
    text-decoration: underline;
  }
```

**Why:** Printers can't reproduce dark backgrounds cheaply. Black on white saves ink and is far more readable in hard copy.

### Step 9.3: Remove Section Backgrounds

```css
  .hero,
  .page-title,
  .intro,
  .mission,
  .goals,
  .how-to-use,
  .prerequisites,
  .cta,
  .features,
  .featured-projects,
  .opportunities,
  .get-involved,
  .collaboration {
    background: white !important;
    padding: 0.75rem 0;
  }

  .hero {
    background-image: none !important;
  }

  .project-card,
  .feature,
  .opportunity,
  .contact-info {
    background: white !important;
    border: 1px solid #ccc !important;
    box-shadow: none !important;
  }
```

### Step 9.4: Prevent Awkward Page Breaks

```css
  .project-card,
  .feature,
  .opportunity,
  .step {
    break-inside: avoid;
  }
}
```

`break-inside: avoid` tells the browser not to split these elements across two printed pages. A card cut in half at the bottom of a page looks broken.

### ✅ Verify Step 9 Works

Press **Ctrl/Cmd + P** (or File → Print) in your browser.

The print preview should show:
- ✅ White background
- ✅ Black text
- ✅ No header or navigation
- ✅ No buttons
- ✅ No cyan accent colours
- ✅ Cards with simple grey borders

> **Tip:** Try printing the Guide page - the numbered step circles will print in grey (greyscale printer) and the steps text should read clearly.

---

## Task 10: Version Control with Git

You've polished every aspect of the website! Let's commit this milestone.

### Step 10.1: Create Feature Branch

```bash
git checkout -b feat/module-6-workshop
```

### Step 10.2: Check What Changed

```bash
git status
```

You should see:
- All 4 HTML files modified (skip link, main id, enhancements.css link)
- `css/enhancements.css` added (new file)

### Step 10.3: Commit

```bash
git add .
git commit -m "Complete Module 6: Add enhancements.css with smooth scroll, skip link, focus rings, animations, and print styles"
```

### Step 10.4: Merge and Push

```bash
git checkout main
git merge feat/module-6-workshop
git push origin main
```

### ✅ Verify Step 10 Works

Visit your GitHub repository and confirm `css/enhancements.css` is present.

---

## Final Check: Full Enhancements Review

### ✅ Interaction Checklist

- [ ] Press **Tab** on any page → "Skip to main content" link appears in cyan at the top
- [ ] Press **Enter** on the skip link → page scrolls smoothly to `<main>`
- [ ] Tab through the navigation → clean cyan outline ring on each link
- [ ] Click a navigation link with the mouse → no outline ring appears
- [ ] Hover over a button → lift + glow effect (from previous modules)
- [ ] Click and hold a button → button scales down slightly (`scale(0.97)`)
- [ ] Reload any page → `<main>` content fades in smoothly

### ✅ Accessibility Checklist

- [ ] `<main id="main-content">` exists on all 4 pages
- [ ] Skip link HTML is first child of `<body>` on all 4 pages
- [ ] `enhancements.css` is linked (last) in all 4 HTML `<head>` sections

### ✅ Print Checklist

- [ ] **Ctrl/Cmd + P** on `index.html` → white background, no header, no buttons
- [ ] **Ctrl/Cmd + P** on `guide.html` → step numbers visible, no dark backgrounds
- [ ] **Ctrl/Cmd + P** on `about.html` → feature cards with light borders

---

## Summary: What You Built

| Feature | CSS Technique | File |
|---------|--------------|------|
| Smooth scroll | `scroll-behavior: smooth` on `html` | `enhancements.css` |
| Skip link | `position: absolute; top: -100%` → `:focus { top: 0 }` | `enhancements.css` + all HTML |
| Focus rings | `:focus` reset + `:focus-visible` branded outline | `enhancements.css` |
| Button press | `.btn:active { scale(0.97) }` | `enhancements.css` |
| Page fade-in | `@keyframes fadeInUp` on `main` | `enhancements.css` |
| Reduced motion | `@media (prefers-reduced-motion: reduce)` | `enhancements.css` |
| Print styles | `@media print` | `enhancements.css` |

**Complete CSS architecture after Module 6:**

```
base.css         → Reset, variables, typography, buttons
layout.css       → Header, footer, container, navigation
index.css        → Home page sections
about.css        → About page sections
guide.css        → Guide page sections
contribute.css   → Contribute page sections
enhancements.css → Site-wide polish (this module)
```

**Ready for Module 7!** Next up: Responsive Design - making this beautiful website work on mobile, tablet, and every screen size in between.
