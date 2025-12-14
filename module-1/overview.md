# Module 1: Complete HTML Structure & Basic Layout

## Overview

In this module, you'll create the foundation for the entire MITS Platform Website by building all 4 HTML pages with proper semantic structure. By the end of this module, you'll have a complete multi-page website skeleton with semantic HTML5 markup, placeholder content, and basic CSS that makes the structure visible and organized.

## What is Semantic HTML?

**Semantic HTML** means using HTML elements that clearly describe their meaning and purpose, both to developers and to browsers/screen readers.

### Non-Semantic vs Semantic

**Non-semantic approach:**

```html
<div class="header">
  <div class="nav">
    <div class="nav-item">Home</div>
  </div>
</div>
```

**Semantic approach:**

```html
<header>
  <nav>
    <a href="index.html">Home</a>
  </nav>
</header>
```

### Why Semantic HTML Matters

- **Accessibility** - Screen readers understand the structure and can navigate properly
- **SEO** - Search engines better understand your content hierarchy
- **Maintainability** - Code is self-documenting and easier to read
- **Best Practices** - Following web standards ensures compatibility

### Key Semantic Elements

- `<header>` - Site header with logo and navigation
- `<nav>` - Navigation menu
- `<main>` - Primary page content
- `<section>` - Thematic grouping of content
- `<article>` - Self-contained content (like project cards)
- `<footer>` - Site footer with copyright and contact info

In this module, you'll learn how to structure an entire multi-page website using these semantic elements!

## What You'll Learn

- Creating a **multi-page website** with proper HTML5 structure
- Using **semantic HTML5 elements** (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`)
- Organizing **heading hierarchy** (H1 → H6) correctly
- Structuring **navigation menus** that work across all pages
- Creating **CSS file organization** for maintainable stylesheets
- Linking CSS files (implementation comes in Module 2)
- **Validating HTML** with W3C validator
- Setting up **meta tags** for SEO and viewport
- **Professional Git workflow** - Version control from day one

## Why This Matters

This module establishes the foundation for everything that follows. A solid HTML structure is critical because:

1. **HTML comes first** - You should complete your HTML structure before styling
2. **Semantic markup is forever** - Good structure makes all future work easier
3. **Accessibility from day one** - Building accessible HTML from the start is much easier than retrofitting
4. **Multi-page consistency** - Learning to structure related pages ensures consistency
5. **Content before presentation** - Separating HTML (content) from CSS (styling) is a fundamental web development principle

## PRD Connection

This module implements the foundational structure from the PRD:

> **Site Structure → Pages (4 total)**
>
> 1. Home Page (index.html)
> 2. About MITS (about.html)
> 3. Getting Started & Registration (guide.html)
> 4. Collaboration & Contribution (contribute.html)

> **Common Components**
>
> All pages include:
>
> - Header - Brand logo and navigation menu
> - Footer - Copyright information and contact details

We're creating all 4 pages with placeholder content and proper semantic structure. The CSS files will be linked but remain empty - we'll implement the styling starting in Module 2.

## Prerequisites

Before starting this module, ensure you have:

- **Basic HTML knowledge** - Understanding of tags, attributes, elements
- **Basic CSS knowledge** - Selectors, properties, values
- **Code editor** - VS Code recommended (with Live Server extension)
- **Modern web browser** - Chrome, Firefox, Edge, or Safari
- **Basic file management** - Creating folders, organizing files

## Time Estimate

⏱️ **30-45 minutes** (HTML structure only, no CSS implementation)

## Module Structure

1. **Task 1**: Create project folder structure and all 4 HTML files
2. **Task 2**: Set up CSS file organization (files will remain empty)
3. **Task 3**: Create the Home Page (index.html) with complete semantic structure
4. **Task 4**: Create About, Guide, and Contribute pages with semantic structure
5. **Task 5**: Verify CSS file links (no implementation yet)
6. **Task 6**: Test HTML structure and navigation
7. **Task 7**: Validate HTML with W3C Validator
8. **Task 8**: Version Control with Git (initialize repository, create branch, commit, push to GitHub)

## Expected Result

By the end of this module, you'll have:

**4 Complete HTML Pages:**

- Home page with hero, intro, featured projects, and collaboration sections
- About page with project goals and platform features
- Guide page with getting started information
- Contribute page with collaboration opportunities

**Proper Semantic Structure:**

- Header with logo and navigation on all pages
- Semantic sections (`<section>`, `<article>`)
- Footer on all pages
- Proper heading hierarchy (one H1 per page)

**CSS Files Created (but empty):**

- All 6 CSS files created and linked
- Files are empty - implementation comes in Module 2

**Git Repository Setup:**

- Local Git repository initialized
- Code committed with professional workflow
- Repository published on GitHub
- Ready for collaborative development

**Visual Result:**

- All 4 pages accessible via navigation
- **Unstyled appearance** (browser default styling)
- Plain text on white background
- All content readable and accessible
- Working links between pages

The site will look completely unstyled at this stage - **that's intentional!** We're focusing on solid HTML structure first. In Module 2, we'll implement `base.css` and `layout.css` to transform this into a beautiful dark-themed design.

Let's get started! 🚀
