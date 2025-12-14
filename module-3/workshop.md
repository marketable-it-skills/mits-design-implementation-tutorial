# Module 3 Workshop: Home Page Styling (index.css)

## Goal

Transform your home page from a functionally structured but plain website into a visually stunning, professional promotional page with styled buttons, hero section with background image, interactive project cards, and polished sections.

## What You're Starting With

Before this module, you have:

- ✅ Complete HTML structure (4 pages) from Module 1
- ✅ Base CSS with variables, typography from Module 2
- ✅ Layout CSS with styled header and footer from Module 2
- ✅ Empty `index.css` file ready for styling

## What You'll Build

By the end of this workshop, your home page will have:

- ✅ Professional button components (primary and secondary styles)
- ✅ Hero section with background image and gradient overlay
- ✅ Styled project cards with hover effects
- ✅ Badges and tags with proper styling
- ✅ Visually distinct sections with proper spacing
- ✅ Complete visual hierarchy

---

## Task 1: Add Hero Image Asset

### Step 1.1: Verify Your Project Structure

First, let's make sure you have the correct starting point. Your project should look like this:

```
your-project/
├── index.html
├── about.html
├── guide.html
├── contribute.html
├── assets/
│   └── images/
│       └── logo-dark.svg
└── css/
    ├── base.css       (complete from Module 2)
    ├── layout.css     (complete from Module 2)
    ├── index.css      (empty - we'll fill this!)
    ├── about.css      (empty)
    ├── guide.css      (empty)
    └── contribute.css (empty)
```

### Step 1.2: Copy Hero Image

Copy the `mits-hero-image.webp` file into your project's `assets/images/` folder.

**For MITS Course Students:** The image is located at:

- `/assets/images/mits-hero-image.webp`

Copy it to:

- `your-project/assets/images/mits-hero-image.webp`

> **Note:** This image shows a modern tech workspace and will be used as the hero section background.

### Step 1.3: Verify Image is Accessible

Open your `index.html` in a browser and open DevTools (F12). Then:

1. Go to the **Network** tab
2. Refresh the page (Ctrl/Cmd + R)
3. You should see `logo-dark.svg` loaded successfully (from Module 2)

We'll verify the hero image works when we add the CSS in Task 3.

---

## Task 2: Button Components

Let's start with buttons! We'll create a reusable button system with base styles and two variants (primary and secondary). Since buttons will be used across all pages, we'll add them to `base.css` for reusability.

### Step 2.1: Open base.css

Open `css/base.css` in your text editor. You should see the CSS variables and typography from Module 2.

### Step 2.2: Add Base Button Styles

Scroll to the bottom of `base.css` (after the `.subtitle` section) and add this code:

```css
/* ==========================================
   BUTTON COMPONENTS
   ========================================== */

/* Base button styles (shared by all buttons) */
.btn {
  display: inline-block;
  padding: 0.75rem 2rem;
  border-radius: var(--radius-md);
  font-weight: 600;
  font-size: 0.9375rem; /* 15px */
  text-decoration: none;
  text-align: center;
  cursor: pointer;
  transition: all 0.3s ease;
  border: none;
}
```

**What this does:**

- `display: inline-block` - Buttons sit inline but accept padding/margin
- `padding: 0.75rem 2rem` - Comfortable button size (12px top/bottom, 32px left/right)
- `border-radius: var(--radius-md)` - Uses our variable (8px rounded corners)
- `transition: all 0.3s ease` - Smooth animation for hover effects
- **No background by default** - Variants will add specific styling

### Step 2.3: Add Primary Button Variant

Add this below the base button styles in `base.css`:

```css
/* Primary button - main call-to-action */
.btn-primary {
  background-color: var(--color-accent);
  color: var(--color-bg-primary);
}

.btn-primary:hover {
  background-color: var(--color-accent-hover);
  color: var(--color-text-primary);
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(6, 182, 212, 0.4);
}
```

**What this does:**

- Uses cyan accent color from our variables
- Dark text on cyan background
- **Hover effect:**
  - Darker cyan background
  - White text for better contrast
  - Moves up 2px (`translateY(-2px)`)
  - Adds glowing shadow

### Step 2.4: Add Secondary Button Variant

Add this below the primary button styles in `base.css`:

```css
/* Secondary button - alternative action */
.btn-secondary {
  background-color: transparent;
  color: var(--color-accent);
  border: 2px solid var(--color-accent);
}

.btn-secondary:hover {
  background-color: rgba(6, 182, 212, 0.1);
  color: var(--color-text-primary);
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(6, 182, 212, 0.4);
}
```

**What this does:**

- Transparent background with cyan border (outlined style)
- **Hover effect:**
  - Subtle cyan background (10% opacity)
  - White text for better contrast
  - Same lift and shadow effects as primary button

### Step 2.5: Verify Buttons Work

Save `base.css` and refresh your browser. You should see:

- ✅ All buttons have solid cyan backgrounds (from `.btn-primary`)
- ✅ "Sign In" button has outline style (from `.btn-secondary`)
- ✅ All buttons have smooth hover effects

**Test:** Hover over each button and verify:

- Primary buttons ("Learn More", "Discover More", "Register", "Get Involved"):
  - Get slightly darker cyan background
  - Text turns white for better contrast
  - Lift up with a glowing shadow
- Secondary button ("Sign In"):
  - Gets subtle cyan background
  - Text turns white
  - Lifts up with a glowing shadow
- All transitions are smooth (not instant)

> **Important:** Make sure your HTML buttons use both classes:
>
> - Primary buttons: `class="btn btn-primary"`
> - Secondary buttons: `class="btn btn-secondary"`
>
> If a button only has `class="btn"`, it won't have proper styling!

---

## Task 3: Hero Section with Background Image

Now let's create a stunning hero section with the background image and gradient overlay.

### Step 3.1: Add Hero Section Styles

Add this to `css/index.css`:

```css
/* ==========================================
   HERO SECTION
   ========================================== */

.hero {
  background-image: linear-gradient(
      135deg,
      rgba(15, 23, 42, 0.85) 0%,
      rgba(30, 41, 59, 0.75) 100%
    ), url("../assets/images/mits-hero-image.webp");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  padding: 8rem 0;
  text-align: center;
  position: relative;
}
```

**What this does:**

- **`background-image`**: Layers two backgrounds:
  1. `linear-gradient(...)` - Dark semi-transparent overlay (on top)
  2. `url(...)` - Hero image (behind overlay)
- **`background-size: cover`** - Image fills entire section, maintaining aspect ratio
- **`background-position: center`** - Centers the image
- **`padding: 8rem 0`** - Large vertical padding (128px) for dramatic effect

> **Important:** The gradient overlay uses `rgba()` with alpha values (0.85, 0.75) to create transparency, allowing the image to show through while keeping text readable.

### Step 3.2: Style Hero Text

Add this below the hero section styles:

```css
.hero h1 {
  font-size: 3rem; /* 48px */
  font-weight: 700;
  margin-bottom: 1.5rem;
  line-height: 1.1;
}

.hero .subtitle {
  font-size: 1.25rem; /* 20px */
  margin-bottom: 2rem;
  color: var(--color-text-secondary);
}

.hero .btn {
  margin-top: 1rem;
}
```

**What this does:**

- Extra-large h1 (48px) for maximum impact
- Subtitle is slightly muted (secondary text color)
- Button has extra top margin for spacing

### Step 3.3: Verify Hero Section

Save and refresh your browser. You should see:

- ✅ Hero section with background image visible
- ✅ Dark gradient overlay making text readable
- ✅ Large, bold heading "MITS - Marketable IT Skills"
- ✅ Subtitle below heading
- ✅ Styled "Learn More" button

**Test:**

- Resize your browser window - image should scale smoothly
- Text should be easily readable against the background
- If image doesn't appear, check the path: `../assets/images/mits-hero-image.webp`

> **Troubleshooting:** If image doesn't show, verify:
>
> 1. Image file is in `assets/images/mits-hero-image.webp`
> 2. Path uses `../` to go up from `css/` folder
> 3. Check browser DevTools Console for 404 errors

---

## Task 4: Introduction Section

Let's style the introduction section below the hero.

### Step 4.1: Add Introduction Section Styles

Add this to `css/index.css`:

```css
/* ==========================================
   INTRODUCTION SECTION
   ========================================== */

.intro {
  background-color: var(--color-bg-secondary); /* slate-800 */
  padding: var(--spacing-2xl) 0; /* 64px top/bottom */
  text-align: center;
}

.intro h2 {
  margin-bottom: var(--spacing-md); /* 24px */
}

.intro p {
  font-size: 1rem;
  line-height: 1.7;
  margin-bottom: var(--spacing-md);
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
}

.intro .btn {
  margin-top: var(--spacing-md); /* 24px */
}
```

**What this does:**

- Different background color (slate-800) creates visual separation from hero section
- Centered text for introductory content
- Paragraphs limited to 800px width for readability
- `margin-left: auto` + `margin-right: auto` centers the text block
- Proper spacing between elements

### Step 4.2: Verify Introduction Section

Save and refresh. You should see:

- ✅ Introduction section with darker background (visual separation from hero)
- ✅ Centered text with paragraphs not too wide (easier to read)
- ✅ Good spacing between heading, paragraphs, and button
- ✅ "Discover More" button styled and centered

---

## Task 5: Project Cards - Base Styles

Now let's style the project cards! We'll do this in two steps: base styles (this task) and content styling (next task).

### Step 5.1: Add Recently Added Projects Section Styles

Add this to `css/index.css`:

```css
/* ==========================================
   FEATURED PROJECTS SECTION
   ========================================== */

.featured-projects {
  padding: var(--spacing-2xl) 0; /* 64px top/bottom */
}

.featured-projects h2 {
  text-align: center;
  margin-bottom: var(--spacing-xl); /* 48px */
}
```

> **Note:** The CSS class is still `.featured-projects` for consistency, but the heading text will say "Recently Added Projects" in the HTML.

### Step 5.2: Add Projects Grid

Add this below the section styles:

```css
.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--spacing-lg); /* 32px */
  margin-bottom: var(--spacing-xl); /* 48px */
}
```

**What this does:**

- CSS Grid with 3 equal columns
- 32px gap between cards
- 48px margin below grid (before CTA buttons)

### Step 5.3: Add Base Card Styles

Add this below the grid styles:

```css
.project-card {
  background-color: var(--color-bg-secondary); /* slate-800 */
  border: 1px solid var(--color-bg-tertiary); /* slate-700 */
  border-radius: var(--radius-lg); /* 12px */
  padding: var(--spacing-md); /* 24px */
  transition: all 0.3s ease;
}

.project-card:hover {
  background-color: var(--color-bg-tertiary); /* slate-700 */
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.3);
}
```

**What this does:**

- Dark card background (slate-800)
- Subtle border (slate-700)
- Rounded corners (12px)
- **Hover effect:**
  - Slightly lighter background
  - Lifts up 4px
  - Adds dramatic shadow

### Step 5.4: Verify Card Base Styles

Save and refresh. You should see:

- ✅ Three project cards in a grid layout
- ✅ Cards have dark background and rounded corners
- ✅ Hover over cards - they lift up with shadow effect
- ✅ 32px gap between cards

**Test:** Hover slowly over each card and observe the smooth lift animation.

---

## Task 6: Project Cards - Content Styling

Now let's style the content inside the cards: headings, subtitles, badges, and tags.

### Step 6.1: Style Card Headings

Add this to `css/index.css`:

```css
/* Card headings */
.project-card h3 {
  font-size: 1.125rem; /* 18px */
  margin-bottom: var(--spacing-xs); /* 8px */
  color: var(--color-text-primary); /* white */
}

.card-subtitle {
  font-size: 0.875rem; /* 14px */
  color: var(--color-text-tertiary); /* slate-500 */
  margin-bottom: var(--spacing-sm); /* 16px */
}
```

### Step 6.2: Style Badges Container

Add this below the heading styles:

```css
/* Badges container */
.badges {
  display: flex;
  gap: var(--spacing-xs); /* 8px */
  margin-bottom: var(--spacing-sm); /* 16px */
  flex-wrap: wrap;
}
```

### Step 6.3: Style Individual Badges

Add this below the badges container:

```css
/* Badge styles */
.badge {
  display: inline-block;
  background-color: rgba(59, 130, 246, 0.2); /* blue with 20% opacity */
  color: rgb(96, 165, 250); /* light blue */
  padding: 0.25rem 0.75rem; /* 4px 12px */
  border-radius: var(--radius-sm); /* 6px */
  font-size: 0.75rem; /* 12px */
  font-weight: 500;
}

.badge-lang {
  display: inline-block;
  background-color: rgba(34, 197, 94, 0.2); /* green with 20% opacity */
  color: rgb(134, 239, 172); /* light green */
  padding: 0.25rem 0.75rem;
  border-radius: var(--radius-sm);
  font-size: 0.75rem;
  font-weight: 500;
}
```

**What this does:**

- Badges have semi-transparent blue background (EuroSkills badge)
- Language badges have semi-transparent green background (🇬🇧 EN)
- Small text (12px) with medium weight

### Step 6.4: Style Tags Container and Tags

Add this below the badge styles:

```css
/* Tags container */
.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem; /* 8px */
  margin: var(--spacing-sm) 0; /* 16px top/bottom */
}

/* Individual tags */
.tag {
  display: inline-block;
  background-color: rgba(6, 182, 212, 0.15); /* cyan with 15% opacity */
  color: var(--color-accent); /* cyan-500 */
  padding: 0.25rem 0.625rem; /* 4px 10px */
  border-radius: var(--radius-sm); /* 6px */
  font-size: 0.75rem; /* 12px */
  font-weight: 500;
}
```

**What this does:**

- Tags have semi-transparent cyan background (matches accent color)
- Slightly smaller than badges for visual hierarchy
- Flex container allows tags to wrap to multiple lines if needed

### Step 6.5: Style Card Description

Add this below the tag styles:

```css
/* Card description text */
.card-description {
  font-size: 0.875rem; /* 14px */
  line-height: 1.6;
  color: var(--color-text-secondary); /* slate-400 */
  margin-top: var(--spacing-sm); /* 16px */
  margin-bottom: 0;
}
```

### Step 6.6: Verify Card Content Styling

Save and refresh. You should see:

- ✅ Card headings in white, proper size
- ✅ Subtitles in muted gray
- ✅ Blue badges for "EuroSkills 2025 Training - Hungary"
- ✅ Green badges for language (🇬🇧 EN)
- ✅ Cyan tags for technologies (frontend, HTML5, CSS3, etc.)
- ✅ Description text in readable gray
- ✅ Proper spacing between all elements

**Test:** Verify all three cards look consistent with proper visual hierarchy.

---

## Task 7: CTA Buttons

Let's style the call-to-action button group below the project cards.

### Step 7.1: Add CTA Buttons Styles

Add this to `css/index.css`:

```css
/* ==========================================
   CTA BUTTONS SECTION
   ========================================== */

.cta-buttons {
  display: flex;
  justify-content: center;
  gap: var(--spacing-sm); /* 16px */
  flex-wrap: wrap;
  margin-top: var(--spacing-xl); /* 48px */
}
```

**What this does:**

- Flexbox centers buttons horizontally
- 16px gap between buttons
- `flex-wrap: wrap` allows buttons to stack on narrow screens
- 48px top margin separates from cards

### Step 7.2: Verify CTA Buttons

Save and refresh. You should see:

- ✅ "Register" (primary) and "Sign In" (secondary) buttons centered
- ✅ Buttons have proper spacing between them
- ✅ Buttons maintain hover effects from Task 2

---

## Task 8: Collaboration Section

Let's style the final section that encourages user collaboration.

### Step 8.1: Add Collaboration Section Styles

Add this to `css/index.css`:

```css
/* ==========================================
   COLLABORATION SECTION
   ========================================== */

.collaboration {
  background-color: var(--color-bg-secondary); /* slate-800 */
  padding: var(--spacing-2xl) 0; /* 64px top/bottom */
  text-align: center;
}

.collaboration h2 {
  margin-bottom: var(--spacing-md); /* 24px */
}

.collaboration p {
  font-size: 1rem;
  line-height: 1.7;
  margin-bottom: var(--spacing-lg); /* 32px */
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
}

.collaboration .btn {
  margin-top: var(--spacing-sm); /* 16px */
}
```

**What this does:**

- Different background color (slate-800) makes section stand out
- Centered text for call-to-action
- Paragraphs limited to 800px for readability
- Large padding for visual impact
- No extra top margin needed (spacing handled by section padding)

### Step 8.2: Verify Collaboration Section

Save and refresh. You should see:

- ✅ Collaboration section with darker background
- ✅ Centered heading and text
- ✅ Text width limited for readability
- ✅ "Get Involved" button styled and centered
- ✅ Section visually distinct from others

---

## Task 9: Version Control with Git

Excellent work! Your home page now looks professional and polished. Let's save your work with Git.

### Step 9.1: Create Feature Branch

```bash
git checkout -b feat/module-3-home-page-styling
```

This creates and switches to a new feature branch for your Module 3 work.

### Step 9.2: Stage Your Changes

```bash
git add .
```

This stages all your modified files (index.css and any other changes).

### Step 9.3: Commit Your Work

```bash
git commit -m "Complete Module 3: Home page styling with buttons, hero, and cards"
```

**Write meaningful commit messages!** This one explains what you accomplished.

### Step 9.4: Merge to Main Branch

```bash
git checkout main
git merge feat/module-3-home-page-styling
```

This switches to main branch and merges your feature branch.

### Step 9.5: Push to GitHub

```bash
git push origin main
```

This uploads your changes to GitHub.

> **Tip:** Make commits after completing each major task, not just at the end! Example:
>
> ```bash
> git add css/index.css
> git commit -m "Add button component styles"
> # Continue working...
> git add css/index.css
> git commit -m "Add hero section with background image"
> ```
>
> This creates a detailed history of your work.

### Step 9.6: Verify on GitHub

Visit your repository on GitHub and verify:

- ✅ New commits appear in history
- ✅ `css/index.css` has your new styles
- ✅ Repository is up to date

---

## Congratulations! 🎉

You've completed Module 3! Your home page now has:

- ✅ **Professional button components** with primary and secondary variants
- ✅ **Stunning hero section** with background image and gradient overlay
- ✅ **Interactive project cards** with hover effects, badges, and tags
- ✅ **Visual hierarchy** that guides user attention
- ✅ **Polished sections** with proper spacing and styling
- ✅ **Better visual separation** between sections with alternating backgrounds

## Files Modified in Module 3

### `css/base.css` ✏️

- Added `--color-bg-secondary-dark` variable for footer
- Added complete button component system (`.btn`, `.btn-primary`, `.btn-secondary`)
- Buttons now reusable across all pages!

### `css/layout.css` ✏️

- Updated footer background to use `--color-bg-secondary-dark`
- Removed unnecessary `margin-top` from footer
- Improved visual separation between collaboration section and footer

### `css/index.css` ✏️

- Added hero section with background image and gradient
- Added introduction section with background color
- Added project cards with grid layout and hover effects
- Added badges and tags styling
- Added CTA buttons layout
- Added collaboration section styling

### `assets/images/` 📁

- Added `mits-hero-image.webp` for hero background

## What You've Accomplished

### Technical Skills

- ✅ Created reusable CSS components (button pattern)
- ✅ Used background images with gradients
- ✅ Built interactive components with transforms and transitions
- ✅ Applied visual hierarchy principles
- ✅ Organized page-specific CSS

### Professional Practices

- ✅ Incremental development (testing after each step)
- ✅ Git feature branch workflow
- ✅ Meaningful commit messages
- ✅ Component-based thinking

## Skills You've Learned

1. **Component Design Patterns** - Base styles + variants (`.btn` + `.btn-primary`)
2. **Background Images** - `background-image`, `background-size: cover`, layering
3. **Gradient Overlays** - `linear-gradient` with `rgba()` for text readability
4. **CSS Transforms** - `translateY()` for hover lift effects
5. **Box Shadows** - Adding depth and emphasis
6. **Visual Hierarchy** - Using color, size, spacing to guide attention
7. **Flexbox & Grid** - Layout patterns for buttons and cards
8. **CSS Transitions** - Smooth animations for better UX

## What's Next?

### Module 7: Responsive Design (Coming Soon)

You'll make your site work perfectly on mobile, tablet, and desktop devices using media queries and responsive patterns.

### Optional Exercises

Want to practice more? Try styling the other pages:

1. **about.html** - Style the about page sections
2. **guide.html** - Style the getting started guide
3. **contribute.html** - Style the contribution page

**Hint:** These pages have simpler layouts than the home page. You can reuse button styles and section patterns!

### Experimentation Ideas

- 🎨 Try different button colors (create `.btn-danger`, `.btn-success`)
- 🎨 Experiment with different hero image overlays
- 🎨 Adjust card hover effects (try different transforms)
- 🎨 Add more spacing or change colors
- 🎨 Create new badge colors for different categories

## Resources

- [MDN: background-image](https://developer.mozilla.org/en-US/docs/Web/CSS/background-image)
- [MDN: CSS Transforms](https://developer.mozilla.org/en-US/docs/Web/CSS/transform)
- [MDN: CSS Transitions](https://developer.mozilla.org/en-US/docs/Web/CSS/transition)
- [MDN: linear-gradient](https://developer.mozilla.org/en-US/docs/Web/CSS/gradient/linear-gradient)

---

**Ready for more?** Continue to Module 7 when it's released, or experiment with styling the other pages on your own! 🚀
