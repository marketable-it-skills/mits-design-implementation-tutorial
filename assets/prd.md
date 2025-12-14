# MITS Platform Website - Product Requirements Document

## Product Overview

A static, multi-page promotional website for the MITS (Marketable IT Skills) platform built with pure HTML and CSS. This project serves as a design implementation exercise focusing on semantic HTML, modern CSS techniques, responsive design, and accessibility.

### Goals

- Showcase the MITS platform and its educational offerings
- Provide clear information about registration and collaboration opportunities
- Demonstrate professional static website development skills
- Maintain full accessibility (WCAG AA compliance)
- Create a responsive design for all device sizes

### Tech Stack

- **HTML5** - Semantic markup only
- **CSS3** - Modern styling techniques (Grid, Flexbox, custom properties)
- **No JavaScript** - Pure HTML/CSS implementation
- **No frameworks/libraries** - Hand-coded from scratch

## Site Structure

### Pages (4 total)

1. **Home Page** (`index.html`)
2. **About MITS** (`about.html`)
3. **Getting Started & Registration** (`guide.html`)
4. **Collaboration & Contribution** (`contribute.html`)

### Common Components

All pages include:

- **Header** - Brand logo and navigation menu
- **Footer** - Copyright information and contact details

## Page Specifications

### 1. Home Page

**Hero Section**

- Large, visually striking cover image
- H1 heading: "MITS - Marketable IT Skills"
- Subtitle explaining the platform's purpose
- Call-to-action button: "Learn More" → About MITS page

**Introduction Section**

- Brief overview of MITS (2-3 paragraphs)
- Call-to-action button: "Discover More" → About MITS page

**New Courses Section**

- Display 3 featured project task cards (most recent)
- Each card shows:
  - Project name
  - Competition badge
  - Brief description
  - Technology tags
- Additional courses shown in a list format below cards
- Two call-to-action buttons:
  - "Register"
  - "Sign In"

**Collaboration Section**

- Description of contribution opportunities
- Call-to-action button: "Get Involved" → Collaboration page

### 2. About MITS Page

**Page Title Section**

- H1: "About MITS"
- Brief introduction paragraph

**Project Goals Section**

- Detailed explanation of MITS objectives
- Key benefits for students and educators
- Call-to-action button: "Register Now"

**Platform Features Section**

- Description of platform capabilities
- How projects are structured
- What students can expect

### 3. Getting Started & Registration Page

**Page Title Section**

- H1: "Getting Started"

**How to Use Section**

- Step-by-step guide for new users
- Registration process explained
- Navigation tips

**Prerequisites Section**

- Required skills and knowledge
- Technical requirements (GitHub account, etc.)

**Call-to-Action Section**

- "Register" button (prominent)
- "Browse Projects" button

### 4. Collaboration & Contribution Page

**Page Title Section**

- H1: "Collaborate with MITS"

**Contribution Opportunities Section**

- How educators can contribute
- How experts can help develop content
- Partnership opportunities

**Get Involved Section**

- Contact information
- Call-to-action button: "Contact Us"

## Design Requirements

### MITS Platform Branding

The website must match the visual identity of the existing MITS platform:

**Brand Elements:**

- **Logo**: Cube/box icon (isometric perspective)
- **Platform Name**: "Web Technologies" or "MITS Platform"
- **Tagline**: "Marketable IT Skills - Real Competition Tasks for Vocational Education"

**Design Philosophy:**

- **Dark-first design** - Professional developer/technical aesthetic
- **Card-based interface** - Clear content organization
- **Tag system** - Multi-colored technology and category tags
- **Competition context** - Clear competition badges and identifiers
- **International support** - Language flags and multilingual UI
- **Search-focused** - Prominent search functionality
- **Filter-driven** - Multiple filter options for content discovery

**Reference Screenshot:**

- See: `.claude/course-resources/mits-design-implementation-tutorial/assets/mist-platform.png`
- All design decisions should reference this actual platform interface

### Visual Style

- **Dark theme** - Modern dark interface matching MITS platform
- **Clean and professional** - Technical/developer aesthetic
- **Modern and approachable** - Engaging for young learners
- **Consistent branding** - MITS colors and typography throughout
- **Card-based layout** - Project cards in grid format
- **Subtle depth** - Shadows and layering for visual hierarchy

### Color Scheme (Based on MITS Platform)

**Dark Theme Colors:**

- **Background**: Very dark blue/slate (`#0F172A` or `#0B1120` - slate-950)
- **Card Background**: Dark slate (`#1E293B` or similar - slate-800/900)
- **Card Border**: Subtle border (`#334155` - slate-700)
- **Primary Text**: White (`#FFFFFF`) for headings
- **Secondary Text**: Light slate (`#94A3B8` - slate-400) for descriptions
- **Tertiary Text**: Medium slate (`#64748B` - slate-500) for labels

**Accent Colors:**

- **Primary Accent**: Cyan/bright blue (`#06B6D4` or `#00D9FF`) for technology tags
- **Technology Tags**: Various blue shades:
  - Bright cyan: `#00D9FF` (frontend, design)
  - Sky blue: `#38BDF8` (backend, database)
  - Blue: `#3B82F6` (frameworks)
  - Indigo: `#6366F1` (languages)
- **Competition Badges**: Neutral gray/slate (`#475569` background, `#94A3B8` text)
- **Language Indicators**: Flag emoji + text in subtle badge

**Interactive States:**

- **Hover**: Lighter card background (`#2D3748` or slate-700)
- **Focus**: Bright cyan ring/outline (`#06B6D4`)
- **Active**: Slightly scaled or elevated shadow

### Typography (MITS Platform Style)

- **Font Family**: Sans-serif, likely Inter or similar modern geometric font
- **Headings**:
  - H1: Bold, white (`font-weight: 700`), 2.5rem - 3rem
  - H2: Bold, white, 2rem (section headings)
  - H3: Bold, white, 1.5rem (card titles - "ES2025 TRAINING HU SI7 - Module A")
  - Subtitle: Regular, slate-400, 0.875rem (card subtitles)
- **Body text**:
  - Regular, slate-400 (`#94A3B8`)
  - Line height: 1.6-1.8
  - Font size: 0.875rem (14px) for descriptions
- **Navigation**: White, 0.875rem - 1rem
- **Tags/Badges**:
  - Small text (0.75rem - 12px)
  - Medium font-weight (500)
  - Colored based on tag type
- **Minimum font size**: 12px for tags, 14px for body text

### Layout & Spacing (MITS Platform Style)

**Header:**

- Dark background (slate-900)
- Logo (cube icon) on left
- "Web Technologies" badge with count
- Search bar with placeholder and keyboard shortcut (⌘K)
- Filter dropdowns (tags, languages, competition)
- User avatar on right
- Height: ~64px
- Padding: 1rem horizontal

**Filter Bar:**

- Competition filter pills (horizontal scroll)
- Outlined style for inactive, filled for active
- Small padding (0.5rem horizontal, 0.25rem vertical)
- Gap between pills: 0.5rem
- Margin bottom: 2rem

**Content Container:**

- Max-width: ~1400px
- Padding: 2rem - 3rem horizontal
- Centered on page

**Card Grid:**

- Display: CSS Grid
- Desktop (≥1024px): 3 columns
- Tablet (768-1023px): 2 columns
- Mobile (<768px): 1 column
- Gap: 1.5rem - 2rem
- Margin bottom: 3rem

**Individual Cards:**

- Padding: 1.5rem
- Border-radius: 0.5rem (8px)
- Border: 1px solid slate-700
- Background: slate-800/900
- Card spacing (internal):
  - Title: margin-bottom 0.5rem
  - Subtitle: margin-bottom 0.75rem
  - Badges row: margin-bottom 0.75rem
  - Tags: margin-bottom 1rem
  - Description: no bottom margin

**Spacing Scale:**

- Base unit: 4px
- Scale: 4, 8, 12, 16, 24, 32, 48, 64px

## Responsive Breakpoints

- **Mobile**: < 768px (single column, stacked navigation)
- **Tablet**: 768px - 1023px (2-column layouts where appropriate)
- **Desktop**: ≥ 1024px (multi-column, full navigation)

## Accessibility Requirements

- ✅ **Semantic HTML** - Proper use of heading hierarchy, nav, main, footer, etc.
- ✅ **Keyboard Navigation** - All interactive elements accessible via keyboard
- ✅ **Focus Indicators** - Visible focus states on all links and buttons
- ✅ **Color Contrast** - WCAG AA compliance (4.5:1 minimum)
- ✅ **Alt Text** - Descriptive alternative text for all images
- ✅ **Skip Links** - Skip to main content link at top of page
- ✅ **ARIA Labels** - Where semantic HTML is insufficient

## SEO Requirements

### Meta Tags (Required on all pages)

**Basic Meta Tags:**

```html
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<meta
  name="description"
  content="[Page-specific description, 150-160 characters]"
/>
<meta
  name="keywords"
  content="MITS, vocational education, IT skills, web development"
/>
<meta name="author" content="MITS Initiative" />
```

**Open Graph Tags (Social Media Sharing):**

```html
<meta property="og:title" content="[Page Title] - MITS Platform" />
<meta property="og:description" content="[Page-specific description]" />
<meta property="og:type" content="website" />
<meta property="og:url" content="[Page URL]" />
<meta property="og:image" content="[Social sharing image URL]" />
```

**Page-Specific Descriptions:**

- **Home**: "MITS - Marketable IT Skills platform offers hands-on web development projects from real WorldSkills and EuroSkills competitions for vocational education."
- **About**: "Learn about the MITS initiative, bringing real competition tasks to vocational IT education in Hungary and Finland."
- **Guide**: "Getting started with MITS platform - registration guide, prerequisites, and how to begin your web development learning journey."
- **Contribute**: "Join MITS as an educator or expert. Contribute to vocational IT education and help develop meaningful project tasks."

### Title Tags

Each page must have a unique, descriptive title (50-60 characters):

- **Home**: `MITS - Marketable IT Skills Platform`
- **About**: `About MITS | Marketable IT Skills Initiative`
- **Guide**: `Getting Started & Registration | MITS Platform`
- **Contribute**: `Collaboration & Contribution | MITS Platform`

### Semantic HTML for SEO

- ✅ Use `<article>` for project cards and content sections
- ✅ Use `<section>` for distinct page sections
- ✅ Use proper heading hierarchy (H1 once per page, then H2-H6 in order)
- ✅ Use `<nav>` for navigation menus
- ✅ Use `<time>` element for dates (if applicable)
- ✅ Use descriptive link text (avoid "click here")

### Image Optimization

- ✅ **Alt text** - Descriptive, keyword-rich (but natural)
- ✅ **File names** - Descriptive, use hyphens (e.g., `mits-platform-hero.jpg`)
- ✅ **File format** - WebP with JPG/PNG fallback
- ✅ **File size** - Optimized, compressed (< 200KB per image)
- ✅ **Dimensions** - Appropriate size, no oversized images

### URL Structure

Clean, descriptive URLs:

- ✅ `index.html` or `/` - Home
- ✅ `about.html` or `/about` - About MITS
- ✅ `guide.html` or `/guide` - Getting Started
- ✅ `contribute.html` or `/contribute` - Collaboration

### Additional SEO Elements

**Sitemap** (`sitemap.xml`):

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url><loc>[base-url]/</loc><priority>1.0</priority></url>
  <url><loc>[base-url]/about.html</loc><priority>0.8</priority></url>
  <url><loc>[base-url]/guide.html</loc><priority>0.8</priority></url>
  <url><loc>[base-url]/contribute.html</loc><priority>0.6</priority></url>
</urlset>
```

**Robots.txt**:

```
User-agent: *
Allow: /
Sitemap: [base-url]/sitemap.xml
```

### Content SEO Best Practices

- ✅ **Unique content** per page (no duplicate content)
- ✅ **Keyword usage** - Natural integration in headings and body text
- ✅ **Internal linking** - Link between related pages
- ✅ **Content length** - Sufficient content per page (minimum 300 words)
- ✅ **Readability** - Clear, scannable content structure

## Technical Requirements

### HTML

- Valid HTML5 markup
- Semantic elements (header, nav, main, article, section, footer)
- Proper heading hierarchy (no skipped levels)
- Accessible forms (labels, fieldsets where appropriate)

### CSS

- Mobile-first approach
- CSS Grid and Flexbox for layouts
- CSS custom properties (variables) for theming
- No inline styles (external stylesheet only)
- Organized, commented code

### Browser Support

- Chrome/Edge (last 2 versions)
- Firefox (last 2 versions)
- Safari (last 2 versions)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Content Guidelines

### Project Cards (MITS Platform Design)

Each project card must follow this exact structure:

**Card Layout (Top to Bottom):**

1. **Module Title** (H3)

   - Text: "ES2025 TRAINING HU SI7 - Module A" (example)
   - Style: Bold, white, 1.125rem
   - Margin-bottom: 0.5rem

2. **Project Display Name** (Subtitle)

   - Text: "SkillShare Academy - Static Website Design"
   - Style: Regular, slate-400, 0.875rem
   - Margin-bottom: 0.75rem

3. **Badges Row** (Flexbox)

   - **Competition Badge**:
     - Text: "EuroSkills 2025 Training Competition - Hungary"
     - Style: Rounded, slate-700 background, slate-300 text
     - Padding: 0.25rem 0.75rem
     - Font-size: 0.75rem
   - **Language Badge**:
     - Flag emoji (🇬🇧) + "EN" or "🇭🇺 HU"
     - Style: Same as competition badge
     - Margin-left: 0.5rem
   - Margin-bottom: 0.75rem

4. **Technology Tags** (Flexbox wrap)

   - Multiple colored pills
   - Colors cycle through: cyan, sky, blue, indigo
   - Examples: "frontend", "static website", "responsive design", "HTML5", "CSS3"
   - Style:
     - Background: Semi-transparent cyan/blue (`bg-cyan-500/20`)
     - Text: Bright cyan/blue (`text-cyan-400`)
     - Padding: 0.25rem 0.625rem
     - Border-radius: 0.375rem
     - Font-size: 0.75rem
     - Gap: 0.5rem
   - Margin-bottom: 1rem

5. **Description** (Paragraph)
   - Text: Project description (2-3 lines, truncated)
   - Style: slate-400, 0.875rem, line-height 1.6
   - Text overflow: ellipsis after 3 lines

**Card Interactions:**

- Hover: Background lightens to slate-700, subtle scale (1.02)
- Cursor: pointer
- Transition: all 200ms ease
- Focus: Cyan outline (2px, offset 2px)

### Call-to-Action Buttons

- **Primary CTA**: Bold, high contrast (e.g., "Register Now")
- **Secondary CTA**: Subtle, outlined style (e.g., "Learn More")
- Clear, action-oriented text
- Hover/focus states for interactivity

### Navigation (MITS Platform Header)

**Header Structure:**

**Left Section:**

- **Logo**: Cube/box icon (white, ~24px)
- **Platform Name Badge**:
  - Text: "Web Technologies" with count badge "17"
  - Style: Dark background, white text, rounded
  - Dropdown icon on right

**Center Section:**

- **Search Bar**:
  - Placeholder: "Search test projects..."
  - Icon: Magnifying glass (left)
  - Keyboard shortcut: "⌘ K" badge (right)
  - Style: Dark slate-800 background, slate-400 text
  - Border-radius: 0.5rem
  - Padding: 0.5rem 1rem
  - Width: ~300px

**Right Section:**

- **Filter Dropdowns**:
  - "Select tags and technologies..."
  - "Languages"
  - "Competition"
  - Style: Dark background, dropdown icon
- **Settings Icon** (optional)
- **User Avatar**: Circular, ~40px

**Mobile Navigation:**

- Hamburger menu icon (three lines)
- Collapsible menu
- Pure CSS implementation using checkbox + label technique
- Smooth transitions

**Active State:**

- Filter pills: Filled background when active
- Current page: Underline or highlighted in menu

## Success Metrics

- ✅ Valid HTML and CSS (W3C validators)
- ✅ Accessible (Lighthouse score ≥ 90)
- ✅ Responsive across all breakpoints
- ✅ Fast loading (< 2 seconds on 3G)
- ✅ Professional visual appearance
- ✅ Clear information hierarchy
- ✅ Functional navigation on all pages

## Constraints

- **No JavaScript** - All functionality must work with HTML/CSS only
- **No frameworks** - Pure HTML/CSS implementation
- **No build tools** - Direct HTML/CSS files
- **Static content** - No server-side processing required
