# Emmet Guide for MITS Project

Emmet is a powerful toolkit built into VS Code that helps you write HTML and CSS faster using abbreviations. This guide focuses on the Emmet shortcuts most useful for building the MITS Platform Website.

## What is Emmet?

Emmet lets you type short abbreviations that expand into full HTML/CSS code. Just type the abbreviation and press `Tab` to expand it.

---

## Essential HTML Emmet Shortcuts for This Project

### 1. HTML5 Boilerplate

**Type:** `!` + `Tab`

**Expands to:**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body></body>
</html>
```

**When to use:** Starting any new HTML page (index.html, about.html, etc.)

---

### 2. Link CSS Files

**Type:** `link:css` + `Tab`

**Expands to:**

```html
<link rel="stylesheet" href="style.css" />
```

**When to use:** Adding CSS links in the `<head>` section

**For this project:**

```
link:css
```

Then modify to: `href="css/base.css"`

---

### 3. Header with Container and Navigation

**Type:** `header>.container>(.logo>span.logo-icon+span)+nav>ul>li*4>a` + `Tab`

**Expands to:**

```html
<header>
  <div class="container">
    <div class="logo">
      <span class="logo-icon"></span>
      <span></span>
    </div>
    <nav>
      <ul>
        <li><a href=""></a></li>
        <li><a href=""></a></li>
        <li><a href=""></a></li>
        <li><a href=""></a></li>
      </ul>
    </nav>
  </div>
</header>
```

**When to use:** Creating the header structure on each page

---

### 4. Section with Container

**Type:** `section.hero>.container` + `Tab`

**Expands to:**

```html
<section class="hero">
  <div class="container"></div>
</section>
```

**When to use:** Creating any section (hero, intro, featured-projects, etc.)

---

### 5. Multiple Project Cards

**Type:** `article.project-card*3>h3+p.card-subtitle+.badges+.tags+p.card-description` + `Tab`

**Expands to:**

```html
<article class="project-card">
  <h3></h3>
  <p class="card-subtitle"></p>
  <div class="badges"></div>
  <div class="tags"></div>
  <p class="card-description"></p>
</article>
<article class="project-card">
  <h3></h3>
  <p class="card-subtitle"></p>
  <div class="badges"></div>
  <div class="tags"></div>
  <p class="card-description"></p>
</article>
<article class="project-card">
  <h3></h3>
  <p class="card-subtitle"></p>
  <div class="badges"></div>
  <div class="tags"></div>
  <p class="card-description"></p>
</article>
```

**When to use:** Creating the 3 project cards on the home page

---

### 6. Footer Structure

**Type:** `footer>.container>.footer-content>.footer-section*3>h4+p*2` + `Tab`

**Expands to:**

```html
<footer>
  <div class="container">
    <div class="footer-content">
      <div class="footer-section">
        <h4></h4>
        <p></p>
        <p></p>
      </div>
      <div class="footer-section">
        <h4></h4>
        <p></p>
        <p></p>
      </div>
      <div class="footer-section">
        <h4></h4>
        <p></p>
        <p></p>
      </div>
    </div>
  </div>
</footer>
```

**When to use:** Creating footer structure

---

### 7. Badges and Tags

**Type:** `span.badge*2` + `Tab`

**Expands to:**

```html
<span class="badge"></span> <span class="badge"></span>
```

**When to use:** Creating badge or tag elements

---

### 8. Button Links

**Type:** `a.btn.btn-primary{Register}+a.btn.btn-secondary{Sign In}` + `Tab`

**Expands to:**

```html
<a href="" class="btn btn-primary">Register</a>
<a href="" class="btn btn-secondary">Sign In</a>
```

**When to use:** Creating call-to-action buttons

---

## Key Emmet Syntax Explained

### Basic Operators

| Symbol | Meaning                 | Example                   | Result                          |
| ------ | ----------------------- | ------------------------- | ------------------------------- |
| `>`    | Child                   | `div>p`                   | `<div><p></p></div>`            |
| `+`    | Sibling                 | `h1+p`                    | `<h1></h1><p></p>`              |
| `*`    | Multiply                | `li*3`                    | `<li></li><li></li><li></li>`   |
| `.`    | Class                   | `div.container`           | `<div class="container"></div>` |
| `#`    | ID                      | `div#header`              | `<div id="header"></div>`       |
| `{}`   | Text content            | `a{Click here}`           | `<a href="">Click here</a>`     |
| `()`   | Grouping                | `div>(header>nav)+footer` | Groups elements together        |
| `[]`   | Custom attributes       | `a[href="#"]`             | `<a href="#"></a>`              |
| `^`    | Climb up (go to parent) | `div>p^div`               | `<div><p></p></div><div></div>` |

### Class and Attribute Shortcuts

```
div.hero → <div class="hero"></div>
section.page-title → <section class="page-title"></section>
a[href="index.html"] → <a href="index.html"></a>
input[type="text" placeholder="Name"] → <input type="text" placeholder="Name">
```

---

## Most Useful Shortcuts for This Project

### Create Navigation Menu

```
nav>ul>li*4>a[href=""]
```

Expands to:

```html
<nav>
  <ul>
    <li><a href=""></a></li>
    <li><a href=""></a></li>
    <li><a href=""></a></li>
    <li><a href=""></a></li>
  </ul>
</nav>
```

---

### Create Feature Grid

```
.features-grid>.feature*4>h3+p
```

Expands to:

```html
<div class="features-grid">
  <div class="feature">
    <h3></h3>
    <p></p>
  </div>
  <div class="feature">
    <h3></h3>
    <p></p>
  </div>
  <div class="feature">
    <h3></h3>
    <p></p>
  </div>
  <div class="feature">
    <h3></h3>
    <p></p>
  </div>
</div>
```

---

### Create Steps (for Guide Page)

```
.step*4>h3+p
```

Expands to:

```html
<div class="step">
  <h3></h3>
  <p></p>
</div>
<div class="step">
  <h3></h3>
  <p></p>
</div>
<div class="step">
  <h3></h3>
  <p></p>
</div>
<div class="step">
  <h3></h3>
  <p></p>
</div>
```

---

### Create Opportunity Cards (for Contribute Page)

```
.opportunity*4>h3+p+ul>li*4
```

Expands to:

```html
<div class="opportunity">
  <h3></h3>
  <p></p>
  <ul>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
  </ul>
</div>
<!-- (repeated 4 times) -->
```

---

## CSS Emmet Shortcuts

Emmet also works in CSS files! Here are the most useful ones for this project:

### Common CSS Properties

| Type            | Expands to                         |
| --------------- | ---------------------------------- |
| `m10`           | `margin: 10px;`                    |
| `mt10`          | `margin-top: 10px;`                |
| `p20`           | `padding: 20px;`                   |
| `w100`          | `width: 100px;`                    |
| `h50`           | `height: 50px;`                    |
| `bgc`           | `background-color: #fff;`          |
| `c`             | `color: #000;`                     |
| `df`            | `display: flex;`                   |
| `dg`            | `display: grid;`                   |
| `fz16`          | `font-size: 16px;`                 |
| `fw700`         | `font-weight: 700;`                |
| `tac`           | `text-align: center;`              |
| `bd`            | `border: 1px solid #000;`          |
| `br10`          | `border-radius: 10px;`             |
| `pos:r`         | `position: relative;`              |
| `pos:a`         | `position: absolute;`              |
| `d:f+jc:c+ai:c` | Flexbox centering (multiple props) |

### CSS Variables

For custom properties (CSS variables):

```
--color-bg-primary: #0f172a;
--spacing-lg: 2rem;
```

---

## Pro Tips for This Project

### 1. Combine Multiple Elements

Instead of typing each element separately, combine them:

```
section.hero>.container>h1+p.subtitle+a.btn
```

This creates the entire hero section structure at once!

---

### 2. Use Numbering for Different Classes

```
li.nav-item$*4
```

Creates:

```html
<li class="nav-item1"></li>
<li class="nav-item2"></li>
<li class="nav-item3"></li>
<li class="nav-item4"></li>
```

---

### 3. Wrap Existing Code

1. Select the code you want to wrap
2. Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac)
3. Type "Emmet: Wrap with Abbreviation"
4. Enter your abbreviation (e.g., `div.container`)

---

### 4. Lorem Ipsum for Placeholder Text

```
lorem
lorem10  (generates 10 words)
lorem*3  (generates 3 paragraphs)
```

---

### 5. Comment Shortcut

```
<!-- Type: c + Tab -->
<!-- Expands to: comment -->
```

---

## Practice Exercises

Try these Emmet abbreviations for common patterns in this project:

### Exercise 1: Complete Page Structure

```
html:5>head>meta:vp+title{MITS Platform}+link:css*3^body>header+main+footer
```

### Exercise 2: Project Card Grid

```
.projects-grid>article.project-card*3>h3{Project Title}+p.card-subtitle+.badges>span.badge*2^.tags>span.tag*4^p.card-description
```

### Exercise 3: Footer with Three Sections

```
footer>.container>.footer-content>.footer-section*3>(h4+p*2)^.footer-bottom>p
```

---

## Keyboard Shortcuts in VS Code

- **Expand Abbreviation**: `Tab` (after typing abbreviation)
- **Wrap with Abbreviation**: `Ctrl+Shift+P` → "Emmet: Wrap with Abbreviation"
- **Balance (Select matching tags)**: `Ctrl+Shift+A` (useful for selecting HTML blocks)
- **Go to Matching Pair**: `Ctrl+Shift+\` (jump between opening/closing tags)

---

## When to Use Emmet in This Project

### ✅ **Use Emmet for:**

- Creating initial HTML structure (`!`)
- Building repetitive elements (navigation items, cards, list items)
- Creating sections with containers
- Building footer structure
- Creating multiple similar elements at once

### ❌ **Don't overuse Emmet for:**

- Single, simple elements (just type `<div>` - it's faster)
- When you need to think about structure (Emmet is fast, but plan first!)
- Complex nested structures (can be hard to read/debug)

---

## Summary: Most Used Emmet in This Project

| Task                      | Emmet Abbreviation                                      |
| ------------------------- | ------------------------------------------------------- |
| HTML5 boilerplate         | `!`                                                     |
| Link CSS file             | `link:css`                                              |
| Section with container    | `section.class-name>.container`                         |
| Multiple list items       | `ul>li*4>a`                                             |
| Project cards             | `article.project-card*3>h3+p+div*2+p`                   |
| Footer structure          | `footer>.container>.footer-content>.footer-section*3`   |
| Div with multiple classes | `div.container.hero.main`                               |
| Button group              | `div.cta-buttons>a.btn.btn-primary+a.btn.btn-secondary` |

---

## Try It Now!

Open VS Code, create a new HTML file, and try:

```
section.hero>.container>h1{MITS - Marketable IT Skills}+p.subtitle{Real Competition Tasks}+a.btn{Learn More}
```

Press `Tab` and watch the magic happen! ✨

---

## Additional Resources

- **Emmet Cheat Sheet**: [https://docs.emmet.io/cheat-sheet/](https://docs.emmet.io/cheat-sheet/)
- **VS Code Emmet Documentation**: [https://code.visualstudio.com/docs/editor/emmet](https://code.visualstudio.com/docs/editor/emmet)

---

**Remember:** Emmet is a tool to speed up your workflow. Use it when it saves time, but don't force it if typing manually is clearer!

Happy coding! 🚀

