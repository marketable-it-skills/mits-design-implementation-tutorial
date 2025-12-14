# MITS Platform Website - Module 1 Solution

This is the complete solution for Module 1: Complete HTML Structure & Basic Layout.

## What's Included

This solution contains a complete 4-page static website with:

- **4 HTML Pages:**
  - `index.html` - Home page with hero, featured projects, and collaboration sections
  - `about.html` - About MITS page with mission and platform features
  - `guide.html` - Getting started guide with registration information
  - `contribute.html` - Collaboration opportunities page

- **6 CSS Files:**
  - `css/base.css` - CSS reset, variables, typography, and base styles
  - `css/layout.css` - Header, footer, and common layout styles
  - `css/index.css` - Home page specific styles
  - `css/about.css` - About page specific styles
  - `css/guide.css` - Guide page specific styles
  - `css/contribute.css` - Contribute page specific styles

## How to View

### Option 1: Direct File Opening
1. Open `index.html` in your web browser
2. Navigate between pages using the navigation menu

### Option 2: Live Server (Recommended)
1. Install the "Live Server" extension in VS Code
2. Right-click on `index.html`
3. Select "Open with Live Server"
4. The site will open in your browser with auto-reload on changes

## Features Implemented

✅ **Semantic HTML5 Structure**
- Proper use of `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`
- Correct heading hierarchy (one H1 per page)
- Accessible navigation menu
- WCAG-compliant markup

✅ **Dark Theme Design**
- Dark background colors matching MITS platform
- High contrast text for readability
- Consistent color scheme using CSS variables

✅ **Responsive Layout**
- CSS Grid for project cards
- Flexbox for navigation and layout elements
- Responsive typography and spacing

✅ **Professional Styling**
- Card-based design for project cards
- Badges and tags for metadata
- Hover effects and transitions
- Sticky header navigation

## File Structure

```
solution/
├── index.html          # Home page
├── about.html          # About MITS page
├── guide.html          # Getting Started page
├── contribute.html     # Collaboration page
├── README.md           # This file
└── css/
    ├── base.css        # Reset, variables, base styles
    ├── layout.css      # Header, footer, common layout
    ├── index.css       # Home page styles
    ├── about.css       # About page styles
    ├── guide.css       # Guide page styles
    └── contribute.css  # Contribute page styles
```

## CSS Architecture

### CSS Variables (Custom Properties)

Defined in `css/base.css`:

```css
/* Colors */
--color-bg-primary: #0f172a;      /* Main background */
--color-bg-secondary: #1e293b;    /* Card background */
--color-bg-tertiary: #334155;     /* Borders */
--color-text-primary: #ffffff;    /* Headings */
--color-text-secondary: #94a3b8;  /* Body text */
--color-accent: #06b6d4;          /* Primary accent */

/* Spacing */
--spacing-xs: 0.5rem;   /* 8px */
--spacing-sm: 1rem;     /* 16px */
--spacing-md: 1.5rem;   /* 24px */
--spacing-lg: 2rem;     /* 32px */
--spacing-xl: 3rem;     /* 48px */
--spacing-2xl: 4rem;    /* 64px */
```

### File Organization

- **base.css** - Foundation styles that apply to all pages
- **layout.css** - Shared layout components (header, footer, sections)
- **[page].css** - Page-specific styles for unique content

## Next Steps

This solution serves as the **starting point** for Module 2, where you'll:
- Enhance the dark theme styling
- Refine colors to match MITS platform exactly
- Remove temporary development borders
- Add more sophisticated visual effects
- Implement advanced CSS techniques

## Validation

All HTML files pass W3C HTML5 validation. To validate yourself:
1. Visit https://validator.w3.org/#validate_by_upload
2. Upload each HTML file
3. Verify no errors

## Browser Compatibility

This solution works in all modern browsers:
- ✅ Chrome/Edge (latest)
- ✅ Firefox (latest)
- ✅ Safari (latest)
- ✅ Opera (latest)

## Notes

- The `--dev-border` variable in `base.css` creates temporary borders to visualize structure. This will be removed in Module 2.
- Navigation uses `class="active"` to highlight the current page.
- All pages share the same header and footer (consistent design).
- The website is fully functional but intentionally basic - styling will be enhanced in later modules.

---

**Module 1 Complete!** 🎉

You've built a solid foundation with semantic HTML and structured CSS. Keep this organized - you'll build on it in every future module!


