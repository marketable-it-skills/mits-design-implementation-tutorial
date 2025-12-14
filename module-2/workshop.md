# Module 2 Workshop: CSS Fundamentals - Base & Layout

## Goal

Transform your unstyled HTML website into a professionally styled dark-themed site by implementing `base.css` and `layout.css`. You'll work incrementally, testing after each step to see immediate results.

**Starting Point**: Module 1 solution (HTML structure with empty CSS files)  
**End Result**: Fully styled website with dark theme, typography, header, footer, and layout

---

## Task 1: CSS Reset & Variables

### Step 1.1: Open base.css

Navigate to your project and open `css/base.css` in your code editor.

Currently, this file is empty (or has a comment). We'll add the foundation styles first.

### Step 1.2: Add CSS Reset

Add the following CSS reset at the top of `base.css`:

```css
/* ==========================================
   CSS RESET & BASE STYLES
   ========================================== */

/* Box Model Fix */
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

**What this does:**

- `box-sizing: border-box` - Makes width/height calculations include padding and border (easier to work with)
- `margin: 0; padding: 0` - Removes default browser spacing from all elements
- `*::before, *::after` - Applies to pseudo-elements too

> **Note:** This "resets" browser defaults so we start from a clean slate. Different browsers have different default styles, and this makes them consistent.

### Step 1.3: Add CSS Custom Properties (Variables)

Below the reset, add your design system variables:

```css
/* CSS Custom Properties (Variables) */
:root {
  /* Colors - Dark Theme */
  --color-bg-primary: #0f172a; /* slate-900 - main background */
  --color-bg-secondary: #1e293b; /* slate-800 - card background */
  --color-bg-tertiary: #334155; /* slate-700 - subtle borders */

  --color-text-primary: #ffffff; /* white - headings */
  --color-text-secondary: #94a3b8; /* slate-400 - body text */
  --color-text-tertiary: #64748b; /* slate-500 - muted text */

  --color-accent: #06b6d4; /* cyan-500 - primary accent */
  --color-accent-hover: #0891b2; /* cyan-600 - hover state */

  /* Spacing Scale */
  --spacing-xs: 0.5rem; /* 8px */
  --spacing-sm: 1rem; /* 16px */
  --spacing-md: 1.5rem; /* 24px */
  --spacing-lg: 2rem; /* 32px */
  --spacing-xl: 3rem; /* 48px */
  --spacing-2xl: 4rem; /* 64px */

  /* Typography */
  --font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    "Helvetica Neue", Arial, sans-serif;

  /* Layout */
  --container-max-width: 1200px;

  /* Border Radius */
  --radius-sm: 0.375rem; /* 6px */
  --radius-md: 0.5rem; /* 8px */
  --radius-lg: 0.75rem; /* 12px */
}
```

**What this does:**

- `:root` - Defines variables globally (available everywhere)
- `--color-*` - Color palette for dark theme
- `--spacing-*` - Consistent spacing scale
- `--font-family` - System font stack (fast, native-looking)
- Variables make it easy to change colors/spacing in one place

> **Note:** CSS custom properties (variables) are a modern CSS feature. Use them with `var(--variable-name)`. They're like a design system in code!

### Step 1.4: Verify It Works

1. Open `index.html` in your browser
2. Open **Browser DevTools** (F12 or right-click → Inspect)
3. Go to the **Elements** tab
4. Click on `<html>` element
5. In the **Styles** panel, scroll down to `:root` section
6. You should see all your CSS variables listed!

**What you'll see in the browser:**

- Page still looks unstyled (default black text on white)
- BUT: The reset removed default margins (text touches the edges now)
- Variables are defined and ready to use

> **Tip:** You can hover over color variables in DevTools to see a color preview!

---

## Task 2: Base Typography

### Step 2.1: Add HTML and Body Styles

In `base.css`, below your variables, add:

```css
/* Base Typography */
html {
  font-size: 16px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  font-family: var(--font-family);
  background-color: var(--color-bg-primary);
  color: var(--color-text-secondary);
  line-height: 1.6;
  min-height: 100vh;
}
```

**What this does:**

- `html font-size: 16px` - Sets base size for `rem` units
- Font smoothing - Makes text look crisp on Mac/Windows
- `body` uses our CSS variables for font, colors, spacing
- `min-height: 100vh` - Body takes at least full viewport height

### Step 2.2: Style Headings

Add heading styles:

```css
/* Headings */
h1,
h2,
h3,
h4,
h5,
h6 {
  color: var(--color-text-primary);
  font-weight: 700;
  line-height: 1.2;
  margin-bottom: var(--spacing-sm);
}

h1 {
  font-size: 2.5rem; /* 40px */
}

h2 {
  font-size: 2rem; /* 32px */
}

h3 {
  font-size: 1.5rem; /* 24px */
}

h4 {
  font-size: 1.25rem; /* 20px */
}
```

**What this does:**

- All headings get white color (`--color-text-primary`)
- Bold weight (700) and tight line-height (1.2)
- Clear size hierarchy: H1 is biggest, H4 is smallest
- Consistent bottom margin using our spacing scale

### Step 2.3: Style Paragraphs, Links, and Lists

Add styles for text elements:

```css
/* Paragraphs */
p {
  margin-bottom: var(--spacing-sm);
}

/* Links */
a {
  color: var(--color-accent);
  text-decoration: none;
  transition: color 0.2s ease;
}

a:hover {
  color: var(--color-accent-hover);
}

/* Lists */
ul,
ol {
  list-style-position: inside;
  margin-bottom: var(--spacing-sm);
}

/* Remove list styling from navigation */
nav ul {
  list-style: none;
}

/* Subtitle styling */
.subtitle {
  font-size: 1.25rem;
  color: var(--color-text-secondary);
  margin-bottom: var(--spacing-md);
}
```

**What this does:**

- Paragraphs get bottom margin for spacing
- Links are cyan (`--color-accent`) with hover effect
- Lists have consistent styling
- Navigation lists have no bullets
- Subtitle class for hero section subtitles

### Step 2.4: Verify Typography Changes

1. Refresh your browser (or use Live Server auto-refresh)
2. **What you should see:**
   - ✅ Dark background (#0f172a - dark slate blue)
   - ✅ White headings (H1, H2, H3)
   - ✅ Gray body text (easier to read than pure white)
   - ✅ Cyan links (bright blue-green)
   - ✅ Hover over links → darker cyan
   - ✅ Proper spacing between elements

**Before/After:**

- Before: Black text on white background
- After: White/gray text on dark background with proper typography hierarchy

> **Congratulations!** Your site now has a dark theme and professional typography. This is the most dramatic visual change in the course!

---

## Task 3: Container Class

Now let's add the container class to `layout.css` to center and constrain content width.

### Step 3.1: Open layout.css

Open `css/layout.css` in your code editor. Currently it's empty.

### Step 3.2: Add Container Class

Add this code to `layout.css`:

```css
/* ==========================================
   LAYOUT - STRUCTURAL STYLES
   ========================================== */

/* Container */
.container {
  max-width: var(--container-max-width);
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}
```

**What this does:**

- `max-width: 1200px` - Content never wider than 1200px
- `margin: 0 auto` - Centers the container horizontally
- `padding: 0 1.5rem` - Adds horizontal padding (gutters)
- `.container` class is already on all your sections from Module 1

> **Note:** The container pattern is used on almost every professional website. It keeps content readable on large screens.

### Step 3.3: Verify Container Works

1. Refresh your browser
2. **What you should see:**
   - ✅ Content is now centered (not touching left edge)
   - ✅ On wide screens, content has max-width (not full-width)
   - ✅ Content has padding on sides (breathing room)

**Test this:**

- Make browser window very wide → content stops growing at 1200px
- Make browser narrow → content shrinks but keeps padding on sides

> **Tip:** Resize your browser window to see the container in action!

---

## Task 4: Header Structure

Let's style the header with Flexbox to position the logo and navigation. First, we'll replace the emoji with the real MITS logo.

### Step 4.1: Add the MITS Logo

Before styling the header, let's add the real MITS logo to replace the emoji placeholder.

1. **Create the assets folder structure:**

   - In your project root, create: `assets/images/`

2. **Download the logo:**

   - Download `logo-dark.svg` from the course resources
   - Save it to `assets/images/logo-dark.svg`

3. **Update all HTML files to use the logo:**

Open `index.html`, find the logo section (around line 21), and replace:

```html
<span class="logo-icon">📦</span>
```

With:

```html
<img src="assets/images/logo-dark.svg" alt="MITS Logo" class="logo-icon" />
```

Repeat this for all 4 HTML files:

- ✅ `index.html`
- ✅ `about.html`
- ✅ `guide.html`
- ✅ `contribute.html`

> **Note:** Now you have the professional MITS logo (a cube with a checkmark) instead of the emoji!

### Step 4.2: Add Header Styles

In `layout.css`, below the container, add:

```css
/* Header */
header {
  background-color: var(--color-bg-secondary);
  padding: var(--spacing-md) 0;
  border-bottom: 1px solid var(--color-bg-tertiary);
  position: sticky;
  top: 0;
  z-index: 100;
}

header .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

**What this does:**

- Dark background (`--color-bg-secondary` - slightly lighter than body)
- Padding top/bottom for breathing room
- Subtle bottom border
- **`position: sticky`** - Header sticks to top when scrolling!
- `z-index: 100` - Header stays above other content
- **Flexbox** - Positions logo left, nav right

### Step 4.3: Style the Logo

Add logo styles:

```css
/* Logo */
.logo {
  display: flex;
  align-items: center;
  gap: var(--spacing-xs);
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--color-text-primary);
}

.logo-icon {
  width: 2rem;
  height: 2rem;
  display: block;
}
```

**What this does:**

- Logo uses Flexbox to align logo image and text
- `gap` adds space between logo and text
- Bold, white text
- Logo image sized to 2rem (32px) square

> **Note:** Your HTML should use the MITS logo SVG: `<img src="assets/images/logo-dark.svg" alt="MITS Logo" class="logo-icon" />`

### Step 4.4: Verify Header Layout

1. Refresh your browser
2. **What you should see:**
   - ✅ Header has dark background bar across top
   - ✅ Logo on the left
   - ✅ Navigation links on the right
   - ✅ Header is sticky (scroll down → header stays at top!)

**Test sticky header:**

- Scroll down the page
- Header should stick to the top as you scroll
- This makes navigation always accessible

---

## Task 5: Navigation Styling

Let's polish the navigation menu with Flexbox and hover effects.

### Step 5.1: Style Navigation Menu

In `layout.css`, add navigation styles:

```css
/* Navigation */
nav ul {
  display: flex;
  gap: var(--spacing-md);
  list-style: none;
  margin: 0;
}

nav a {
  color: var(--color-text-secondary);
  font-weight: 500;
  padding: var(--spacing-xs) var(--spacing-sm);
  border-radius: var(--radius-sm);
  transition: all 0.2s ease;
}

nav a:hover {
  color: var(--color-text-primary);
  background-color: var(--color-bg-tertiary);
}

nav a.active {
  color: var(--color-accent);
  background-color: rgba(6, 182, 212, 0.1);
}
```

**What this does:**

- `display: flex` - Arranges nav links horizontally
- `gap: 1.5rem` - Space between links
- Links have padding for larger click area
- Rounded corners (`border-radius`)
- **Hover effect** - Brightens text, adds background
- **Active link** - Cyan color shows current page

### Step 5.2: Verify Navigation Styling

1. Refresh your browser
2. **What you should see:**
   - ✅ Navigation links in a horizontal row
   - ✅ Proper spacing between links
   - ✅ Hover over links → background appears, text brightens
   - ✅ Current page link is highlighted in cyan
   - ✅ Professional, polished look

**Test navigation:**

- Hover over each link → see hover effect
- Current page (e.g., "Home" on index.html) should be cyan
- Click through pages → active link changes

---

## Task 6: Main Content & Sections

Add spacing to main content and sections.

### Step 6.1: Style Main and Sections

In `layout.css`, add:

```css
/* Main Content */
main {
  min-height: 50vh;
}

/* Sections */
section {
  padding: var(--spacing-2xl) 0;
}

/* Remove excessive padding from first section */
section:first-child {
  padding-top: var(--spacing-xl);
}
```

**What this does:**

- `main min-height: 50vh` - Main content takes at least half the viewport
- Sections have large vertical padding (top/bottom)
- First section has less top padding (closer to header)

### Step 6.2: Verify Section Spacing

1. Refresh your browser
2. **What you should see:**
   - ✅ Sections have generous vertical spacing
   - ✅ Content breathes (not cramped)
   - ✅ Proper spacing between sections

---

## Task 7: Footer Structure

Finally, let's style the footer with CSS Grid.

### Step 7.1: Add Footer Styles

In `layout.css`, add footer styles:

```css
/* Footer */
footer {
  background-color: var(--color-bg-secondary);
  padding: var(--spacing-xl) 0 var(--spacing-md);
  margin-top: var(--spacing-2xl);
  border-top: 1px solid var(--color-bg-tertiary);
}

.footer-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: var(--spacing-lg);
  margin-bottom: var(--spacing-lg);
}

.footer-section h4 {
  color: var(--color-text-primary);
  margin-bottom: var(--spacing-sm);
  font-size: 1.125rem;
}

.footer-section p {
  color: var(--color-text-tertiary);
  font-size: 0.875rem;
  margin-bottom: var(--spacing-xs);
}

.footer-section ul {
  list-style: none;
}

.footer-section ul li {
  margin-bottom: var(--spacing-xs);
}

.footer-section a {
  color: var(--color-text-tertiary);
  font-size: 0.875rem;
  transition: color 0.2s ease;
}

.footer-section a:hover {
  color: var(--color-accent);
}

.footer-bottom {
  text-align: center;
  padding-top: var(--spacing-md);
  border-top: 1px solid var(--color-bg-tertiary);
}

.footer-bottom p {
  color: var(--color-text-tertiary);
  font-size: 0.875rem;
  margin: 0;
}
```

**What this does:**

- Dark footer background (matches header)
- Top border separates from content
- **CSS Grid** - Creates flexible column layout
- `auto-fit` - Columns adjust based on screen width
- `minmax(250px, 1fr)` - Min 250px, max equal width
- Footer sections styled with smaller text
- Copyright centered at bottom

### Step 7.2: Verify Footer Layout

1. Refresh your browser
2. Scroll to the bottom of the page
3. **What you should see:**
   - ✅ Footer has dark background
   - ✅ Content organized in columns (3 on wide screens)
   - ✅ Copyright centered at bottom
   - ✅ Links have hover effects
   - ✅ Professional, organized appearance

**Test responsive columns:**

- Wide screen → 3 columns
- Narrow browser → fewer columns (Grid adjusts automatically)

---

---

## Task 8: Version Control with Git

Let's commit your Module 2 work using the Git workflow you learned in Module 1.

### Step 8.1: Create Feature Branch

Switch to your project folder in the terminal and create a feature branch for Module 2:

```bash
git checkout -b feat/module-2-css-fundamentals
```

**What this does:** Creates and switches to a new branch for your Module 2 work (CSS fundamentals).

### Step 8.2: Stage and Commit Your Work

Stage all your changes:

```bash
git add .
```

Check what will be committed:

```bash
git status
```

You should see your updated CSS files (`base.css`, `layout.css`) and any updated HTML files.

Commit your work with a meaningful message:

```bash
git commit -m "Complete Module 2: CSS fundamentals - base and layout"
```

> **Tip:** You could have made multiple commits during Module 2 - after completing base.css, then again after layout.css. Multiple commits help track your progress!

### Step 8.3: Merge to Main Branch

Switch back to main:

```bash
git checkout main
```

Merge your feature branch:

```bash
git merge feat/module-2-css-fundamentals
```

### Step 8.4: Push to GitHub

Push your updated code to GitHub:

```bash
git push origin main
```

Your Module 2 work is now backed up on GitHub!

### Step 8.5: Verify on GitHub

1. Go to your GitHub repository
2. Refresh the page
3. Check that `css/base.css` and `css/layout.css` now have content
4. View your commit history - you should see your Module 2 commit

**Great job!** Your code is version controlled and your portfolio is growing! 🚀

---

## Congratulations! 🎉

You've completed Module 2! Your website has been transformed:

### What You've Accomplished

✅ **Implemented base.css**

- CSS reset for consistency
- CSS custom properties (design system)
- Typography hierarchy
- Dark theme colors

✅ **Implemented layout.css**

- Container pattern for centered content
- Styled header with Flexbox
- Polished navigation with hover effects
- Organized footer with CSS Grid
- Proper spacing throughout

### Visual Transformation

**Before Module 2:**

- Unstyled HTML (browser defaults)
- Black text on white background
- No layout structure

**After Module 2:**

- Professional dark theme
- Beautiful typography
- Structured header and footer
- Centered, well-spaced content
- Hover effects and interactions

### Skills You've Learned

- ✅ CSS reset and box model
- ✅ CSS custom properties (variables)
- ✅ Typography hierarchy
- ✅ Flexbox for 1-dimensional layouts
- ✅ CSS Grid for 2-dimensional layouts
- ✅ Sticky positioning
- ✅ Container pattern
- ✅ Hover effects and transitions
- ✅ Git feature branch workflow (continued practice)

## Test All Pages

Make sure to test all 4 pages:

1. **index.html** - Home page ✅
2. **about.html** - About MITS ✅
3. **guide.html** - Getting Started ✅
4. **contribute.html** - Collaboration ✅

All pages should now have:

- Dark theme
- Styled header and footer
- Proper typography
- Consistent layout

## What's Next?

**Module 3**: Page-Specific CSS

- Hero section styling with gradients
- Button styles for CTAs
- Project card components
- Unique layouts for each page

Your foundation is solid - now we'll add the unique styles that make each page special! 🚀

## Troubleshooting

### "My colors aren't showing"

- Check that you saved `base.css`
- Verify CSS file is linked in HTML `<head>`
- Check browser DevTools Console for errors

### "Navigation isn't horizontal"

- Make sure `display: flex` is on `nav ul`
- Check for typos in class names
- Clear browser cache and refresh

### "Header isn't sticky"

- Verify `position: sticky` and `top: 0` on `header`
- Some older browsers don't support sticky (use modern browser)

### "Footer columns aren't working"

- Check `display: grid` on `.footer-content`
- Verify `grid-template-columns` property
- Resize browser to see Grid in action
