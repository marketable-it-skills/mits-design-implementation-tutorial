# Module 6: Polish & Advanced CSS Techniques

## Overview

In this module, you'll elevate your complete 4-page website from "styled" to "polished" by adding a suite of professional enhancements via a single new file: `enhancements.css`. This file is linked by all four pages and adds smooth scrolling, a skip-to-content link, keyboard focus indicators, button press feedback, a page fade-in animation, motion-safe design, and a print stylesheet. None of these changes require any JavaScript.

## What You'll Build

A new `css/enhancements.css` file (linked in all 4 HTML pages) that adds:

- **Smooth scroll** - Browser-native smooth scrolling for anchor links
- **Skip link** - A visually hidden "Skip to main content" link that appears on keyboard focus (an accessibility must-have)
- **Keyboard focus rings** - Branded cyan outline that appears only for keyboard navigation (not mouse clicks)
- **Button active state** - Subtle "press" scale effect when buttons are clicked
- **Page fade-in animation** - `main` content fades in smoothly on every page load
- **`prefers-reduced-motion` support** - All animations and transitions disabled for users who need them to be
- **Print stylesheet** - Clean, readable output when a page is printed

## What is Progressive Enhancement?

**Progressive enhancement** means starting with a solid, functional baseline and then adding layers of improvement for capable browsers and user preferences. `enhancements.css` is a textbook example:

- The website works perfectly without it (all content and layout intact)
- Loading it adds polish that doesn't break anything if missing
- It's the last stylesheet linked, so it has the highest specificity for its rules

This is also why `enhancements.css` is a single file rather than split across page-specific files - these enhancements apply everywhere and belong in one place.

## Key Concepts You'll Learn

### 1. `scroll-behavior: smooth`

One CSS property, one line, instantly smooth scrolling:

```css
html {
  scroll-behavior: smooth;
}
```

Test it by clicking the "Skip to main content" link (which targets `#main-content`) after this module.

### 2. Skip Links (Accessibility)

A **skip link** is a visually hidden anchor that allows keyboard users to jump past repeated navigation to the main content. It is required for WCAG 2.4.1 (Level A) compliance.

```css
.skip-link {
  position: absolute;
  top: -100%;   /* hidden above the viewport */
}

.skip-link:focus {
  top: 0;       /* slides in when Tab is pressed */
}
```

The trick is `position: absolute; top: -100%` which moves it off-screen without using `display: none` (which would make it untabbable). On `:focus`, `top: 0` slides it back into view.

### 3. `:focus` vs `:focus-visible`

| Pseudo-class | Triggers on | Use for |
|---|---|---|
| `:focus` | Mouse click AND keyboard Tab | Removing browser default (then replace) |
| `:focus-visible` | Keyboard Tab only | Your branded focus ring |

The pattern: remove the outline with `:focus`, then re-add a nicer one with `:focus-visible`. Mouse users never see it; keyboard users always see it.

```css
:focus         { outline: none; }
:focus-visible { outline: 2px solid var(--color-accent); outline-offset: 3px; }
```

### 4. `@keyframes` Animations

```css
@keyframes fadeInUp {
  from { opacity: 0; transform: translateY(20px); }
  to   { opacity: 1; transform: translateY(0); }
}

main {
  animation: fadeInUp 0.5s ease both;
}
```

- `@keyframes` defines the start and end state of an animation
- `animation: name duration timing fill-mode` applies it
- `both` fill mode: element starts in the `from` state before the animation runs (prevents a flash of fully-visible content)

### 5. `prefers-reduced-motion`

An OS-level setting where users can request less motion. CSS can detect this:

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

This is a WCAG 2.3.3 (Level AAA) criterion and a basic courtesy to users with vestibular disorders. Using `0.01ms` instead of `0` ensures callback events still fire for JavaScript (not an issue here, but good practice).

### 6. `@media print`

Entirely separate styles applied only when the page is printed:

```css
@media print {
  header, footer, .btn { display: none !important; }
  body { background: white; color: black; }
}
```

The dark theme looks terrible on paper. Print styles swap it for black text on white, remove decorative backgrounds, and hide navigation that's useless in a printed document.

### 7. Button `:active` State

```css
.btn:active {
  transform: translateY(0) scale(0.97);
  transition-duration: 0.1s;
}
```

The `:active` state applies while a button is being held down. A tiny scale-down (to 97%) gives tactile "press" feedback without being distracting. The fast `0.1s` duration makes it snap.

## Why This Matters

### The Complete Layer Stack

After Module 6, every page loads CSS in this order:

```
base.css           → variables, reset, typography, buttons
layout.css         → header, footer, container
[page].css         → page-specific sections and components
enhancements.css   → site-wide polish (this module)
```

This is a professional CSS architecture: global → structural → component → enhancement. Each layer builds on the previous without tight coupling.

### Accessibility Is Not Optional

The skip link and `:focus-visible` rules are accessibility requirements (WCAG 2.1). Implementing them from the start is far easier than retrofitting them later. Keyboard-only navigation is used by:

- Users with motor impairments who can't use a mouse
- Screen reader users
- Power users who prefer keyboard shortcuts
- Users on devices with limited pointing precision

### Performance Mindset

`enhancements.css` demonstrates a principle: **enhancement layers should degrade gracefully**. If a browser doesn't support `@keyframes`, the page still works perfectly - content just doesn't animate in. This is called **fault tolerance** and is a hallmark of well-written CSS.

## What You'll Learn

By completing this module, you'll be able to:

- ✅ Enable smooth scroll site-wide with one CSS property
- ✅ Build a visually hidden skip link that appears on keyboard focus
- ✅ Differentiate `:focus` and `:focus-visible` and use both correctly
- ✅ Write `@keyframes` animations with `from`/`to` syntax
- ✅ Apply an animation to an element with the `animation` shorthand
- ✅ Add a button `:active` "press" state with `scale()`
- ✅ Use `@media (prefers-reduced-motion)` to disable motion on request
- ✅ Write a `@media print` stylesheet for readable printed output
- ✅ Structure CSS in enhancement layers (base → layout → page → enhancements)

## PRD Connection

This module implements **Design Requirements → Interactions & Accessibility**:

- Smooth, polished transitions
- Keyboard-navigable interface
- Accessible focus management
- Print-friendly output

## Prerequisites

- ✅ **Completed Module 5** - All 4 pages fully styled
- ✅ **Browser DevTools** - Needed to test animations and focus states
- ✅ **Keyboard** - Needed to test the skip link and focus rings (press Tab)

## Time Estimate

⏱️ **60-75 minutes**

**Breakdown:**

- Task 1: Verify starting point & create `enhancements.css` (5 min)
- Task 2: Add `enhancements.css` link + skip link HTML to all pages (10 min)
- Task 3: Smooth scroll (3 min)
- Task 4: Skip link CSS (8 min)
- Task 5: `:focus-visible` keyboard focus rings (8 min)
- Task 6: Button `:active` state (5 min)
- Task 7: Page fade-in animation (10 min)
- Task 8: `prefers-reduced-motion` (5 min)
- Task 9: Print stylesheet (8 min)
- Task 10: Git workflow (5 min)

## Module Structure

1. **Task 1: Create enhancements.css** - New file, file header, link in all pages
2. **Task 2: HTML Updates** - Skip link element + `id="main-content"` on all pages
3. **Task 3: Smooth Scroll** - One line on `html`
4. **Task 4: Skip Link** - Visually hidden until focused
5. **Task 5: Focus Visible** - `:focus` reset + `:focus-visible` branded ring
6. **Task 6: Button Active State** - `:active` scale press effect
7. **Task 7: Page Fade-In** - `@keyframes fadeInUp` on `main`
8. **Task 8: Reduced Motion** - `@media (prefers-reduced-motion: reduce)`
9. **Task 9: Print Styles** - `@media print` for clean printed output
10. **Task 10: Version Control** - Commit and push

## Expected Result

**Before Module 6 (Module 5 complete):**
- 4 fully styled pages
- Browser-default focus outlines (blue/orange ring on everything clicked)
- No animation on page load
- Dark theme appears if you try to print

**After Module 6 (This module complete):**
- Smooth scrolling on all anchor links
- "Skip to main content" link appears at the top when you press Tab
- Cyan branded focus rings on navigation links and buttons (keyboard only)
- Buttons give satisfying press feedback when clicked
- Page content fades in smoothly on load
- Animations disabled for users who prefer reduced motion
- Print-friendly white/black output

## What's NOT in This Module

- ❌ **Scroll-triggered animations** - Requires JavaScript (`IntersectionObserver`); out of scope for pure HTML/CSS course
- ❌ **CSS transitions on page navigation** - Requires JavaScript; out of scope
- ❌ **JavaScript interactions** - Pure HTML/CSS course
- ❌ **Responsive design** - Media queries for layout come in Module 7

## Tips for Testing This Module

### Testing the Skip Link
1. Open any page in the browser
2. Press **Tab** once - the skip link should appear at the top
3. Press **Enter** - the page should scroll to the main content and move focus to it

### Testing Focus Rings
1. Press **Tab** repeatedly to navigate through the page
2. You should see a cyan outline around the focused element
3. Click anywhere with the mouse - no outline should appear on the clicked element

### Testing Reduced Motion
1. In Windows: Settings → Accessibility → Visual Effects → Animation effects
2. In macOS: System Settings → Accessibility → Display → Reduce Motion
3. Refresh any page - the fade-in animation should be gone

### Testing Print Styles
1. In the browser, press **Ctrl/Cmd + P** (print preview)
2. You should see white background, black text, no header/footer/buttons

## Ready to Start?

Head to [workshop.md](workshop.md) to add these professional polish touches to your complete website!
