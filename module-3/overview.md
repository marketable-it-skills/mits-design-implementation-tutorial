# Module 3: Home Page Styling (index.css)

## Overview

In this module, you'll transform your professionally structured website into a visually stunning home page with complete styling. You'll add reusable button components to `base.css` and implement `index.css` for page-specific styles including a hero section with background image, project cards with hover effects, and polished sections that guide users through your site.

By the end of this module, your home page will look like a professional promotional website with proper component styling, visual hierarchy, and interactive elements.

## What You'll Build

Starting from Module 2's foundational layout (with header, footer, and typography), you'll add:

- **Button Components** - Reusable primary and secondary button styles with hover effects
- **Hero Section** - Eye-catching header with background image and gradient overlay
- **Project Cards** - Interactive cards with badges, tags, and hover animations
- **Call-to-Action Sections** - Styled sections that guide users to take action
- **Visual Hierarchy** - Color, spacing, and sizing that directs attention

## What are CSS Components?

**Components** in CSS are reusable patterns that can be applied to multiple elements. For example, a button component has:

- **Base styles** (`.btn`) - Shared properties like padding, border-radius, transitions
- **Variants** (`.btn-primary`, `.btn-secondary`) - Different appearances for different contexts

This approach (often called "Object-Oriented CSS" or OOCSS) makes your CSS:

- **Maintainable** - Change button styles in one place, affects all buttons
- **Consistent** - All buttons share the same base behavior
- **Flexible** - Easy to create new variants (`.btn-danger`, `.btn-success`, etc.)

## Key Concepts You'll Learn

### 1. Button Design Patterns

Learn to create flexible, reusable button components:

```css
/* Base button (shared styles) */
.btn {
  padding: 0.75rem 2rem;
  border-radius: var(--radius-md);
  transition: all 0.3s ease;
}

/* Primary variant */
.btn-primary {
  background-color: var(--color-accent);
  color: var(--color-bg-primary);
}

/* Secondary variant */
.btn-secondary {
  background-color: transparent;
  border: 2px solid var(--color-accent);
}
```

### 2. Background Images with CSS

Learn to use images as backgrounds for sections:

- `background-image` - Set the image URL
- `background-size: cover` - Make image fill entire container
- `background-position: center` - Center the image
- `background-repeat: no-repeat` - Prevent tiling

### 3. Gradient Overlays

Learn to layer gradients over images for text readability:

```css
.hero {
  background-image: linear-gradient(
      135deg,
      rgba(15, 23, 42, 0.95) 0%,
      rgba(30, 41, 59, 0.85) 100%
    ), url("../assets/images/mits-hero-image.webp");
}
```

The gradient (with `rgba` for transparency) creates a dark overlay, making white text readable.

### 4. Card Components

Learn to build flexible, interactive card patterns:

- Base card styles (background, border, padding)
- Hover effects (transform, box-shadow)
- Internal layout (headings, badges, tags, descriptions)
- Visual hierarchy (size, color, spacing)

### 5. Visual Hierarchy

Learn to guide user attention through:

- **Size** - Larger elements draw attention first (h1 > h2 > body text)
- **Color** - Bright accent colors stand out against dark backgrounds
- **Spacing** - More spacing creates emphasis
- **Position** - Elements at the top are seen first

## Why This Matters

### Professional Development Skills

This module teaches you how real websites are built:

1. **Component-Based Design** - Modern CSS uses reusable components (same concept as React components)
2. **Design Systems** - Variables and consistent patterns create cohesive designs
3. **User Experience** - Visual hierarchy and interactive elements guide users
4. **Performance** - CSS transforms and transitions are hardware-accelerated

### Career-Ready Techniques

These patterns appear in:

- **Bootstrap, Tailwind** - Framework buttons and cards use these same patterns
- **UI Libraries** - All component libraries implement button variants this way
- **Design Systems** - Companies like Google, Apple use component thinking
- **Modern Frameworks** - React, Vue components still need CSS styling

## What You'll Learn

By completing this module, you'll be able to:

- ✅ Create reusable button components with base + variant pattern
- ✅ Use background images effectively with gradients and positioning
- ✅ Build interactive card components with hover effects
- ✅ Layer gradients over images for text readability
- ✅ Apply CSS transforms for smooth animations
- ✅ Use transitions to make interactions feel smooth
- ✅ Create visual hierarchy through color, size, and spacing
- ✅ Organize page-specific CSS separate from base styles
- ✅ Build professional-looking promotional websites

## PRD Connection

This module implements **Page Specifications → Home Page** from the PRD:

- **Hero Section** - Large heading, subtitle, CTA button with background
- **Featured Projects** - Project cards with badges, tags, descriptions
- **Call-to-Action Buttons** - Primary and secondary button styles
- **Collaboration Section** - Styled section encouraging user action

**Design Requirements** implemented:

- **Buttons** - Primary (cyan), Secondary (outlined), Hover effects
- **Cards** - Dark background, borders, hover lift effect
- **Badges & Tags** - Color-coded labels with rounded corners
- **Visual Hierarchy** - Proper heading sizes, color contrast

## Prerequisites

Before starting this module, you should have:

- ✅ **Completed Module 1** - HTML structure for all pages
- ✅ **Completed Module 2** - Base CSS (variables, typography) and Layout CSS (header, footer)
- ✅ **Text Editor** - VS Code (or equivalent) open
- ✅ **Browser** - Chrome/Firefox with DevTools open
- ✅ **Git** - Repository initialized and connected to GitHub

**Skills from Previous Modules:**

- HTML semantic markup
- CSS custom properties (variables)
- CSS selectors and specificity
- Box model and spacing
- Flexbox and Grid basics
- Git feature branch workflow

## Time Estimate

⏱️ **75-90 minutes**

**Breakdown:**

- Task 1: Add Hero Image (5 min)
- Task 2: Button Components (10 min)
- Task 3: Hero Section Styling (15 min)
- Task 4: Introduction Section (10 min)
- Task 5: Project Cards - Base (15 min)
- Task 6: Project Cards - Content (15 min)
- Task 7: CTA Buttons (5 min)
- Task 8: Collaboration Section (5 min)
- Task 9: Git Workflow (10 min)

## Module Structure

This module includes **9 incremental tasks**, each with testing to see immediate results:

1. **Task 1: Add Hero Image** - Copy image asset to project
2. **Task 2: Button Components** - Add reusable button styles to base.css (primary, secondary)
3. **Task 3: Hero Section** - Add background image and gradient overlay
4. **Task 4: Introduction Section** - Style intro text and spacing
5. **Task 5: Project Cards - Base Styles** - Card containers and hover effects
6. **Task 6: Project Cards - Content Styling** - Badges, tags, descriptions
7. **Task 7: CTA Buttons** - Center and space button group
8. **Task 8: Collaboration Section** - Final section styling
9. **Task 9: Version Control with Git** - Commit and push your work

**Learning Approach:** Each task is small and testable. You'll see your page transform step-by-step, making it easy to debug and understand each concept in isolation.

## Expected Result

**Before Module 3 (Module 2 complete):**

- Dark-themed website with styled header and footer
- Beautiful typography and spacing
- Functional navigation
- **BUT**: No button styling, no background images, no card effects

**After Module 3 (This module complete):**

- **Stunning hero section** with background image and call-to-action
- **Styled buttons** that respond to hover with smooth animations
- **Professional project cards** with badges, tags, and hover effects
- **Visually distinct sections** that guide user attention
- **Complete visual hierarchy** - home page looks like a real promotional website

**Visual Transformation:**

Your home page will go from "functional but plain" to "professional and polished" - the kind of design you'd see on real tech company websites.

## What's NOT in This Module

To keep this module focused, we're NOT covering:

- ❌ **Other page styling** - `about.css`, `guide.css`, `contribute.css` remain empty (can be exercises)
- ❌ **Responsive design** - Mobile/tablet views come in Module 7
- ❌ **Advanced animations** - Keyframe animations come later
- ❌ **Forms** - No forms in this project
- ❌ **JavaScript** - Pure HTML/CSS course

These topics are either out of scope or covered in later modules.

## Tips for Success

### Before You Start

1. **Open DevTools** - Keep browser DevTools (F12) open throughout
2. **Refresh Often** - Ctrl/Cmd + R to see changes (or use Live Server)
3. **Check Hover Effects** - Test button and card hovers after implementing
4. **Compare with Solution** - If stuck, check Module 3 solution folder

### During the Workshop

- ✅ **Test after every step** - Don't skip verification steps!
- ✅ **Read explanations** - Understand WHY, not just WHAT
- ✅ **Experiment** - Try changing colors, sizes, spacing
- ✅ **Take breaks** - Rest your eyes every 20-30 minutes

### Common Mistakes to Avoid

- ❌ **Skipping testing** - Always verify each step works before moving on
- ❌ **Copy-pasting blindly** - Understand what each CSS property does
- ❌ **Forgetting paths** - Background image path is relative: `../assets/images/`
- ❌ **Missing commas** - CSS gradient syntax requires commas between colors
- ❌ **Not using variables** - Use `var(--color-accent)`, not hard-coded colors

## Ready to Start?

Head over to [workshop.md](workshop.md) to begin styling your home page!

**Remember:** Each step includes testing/verification. You'll see your site transform in real-time, making this an engaging and rewarding module! 🎨
