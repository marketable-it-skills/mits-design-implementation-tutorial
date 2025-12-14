# Module 1 Workshop: Complete HTML Structure & Basic Layout

## Goal

Create all 4 pages of the MITS Platform Website with complete semantic HTML5 structure, placeholder content, and basic CSS for structure visualization.

---

## Task 1: Create Project Folder Structure

### Step 1.1: Create the Project Folder

Create a new folder for your project. You can name it anything you like, such as:

```
mits-website
```

### Step 1.2: Create the CSS Subfolder

Inside your project folder, create a subfolder called `css`:

```
mits-website/
└── css/
```

### Step 1.3: Create All HTML Files

In the root of your project folder, create 4 empty HTML files:

- `index.html` (Home page)
- `about.html` (About MITS page)
- `guide.html` (Getting Started page)
- `contribute.html` (Collaboration page)

Your folder structure should now look like:

```
mits-website/
├── index.html
├── about.html
├── guide.html
├── contribute.html
└── css/
```

---

## Task 2: Create CSS Files

### Step 2.1: Create the Base CSS Files

Inside the `css/` folder, create 6 CSS files:

- `base.css` - CSS reset, variables, typography base
- `layout.css` - Header, footer, common layout
- `index.css` - Home page specific styles
- `about.css` - About page specific styles
- `guide.css` - Guide page specific styles
- `contribute.css` - Contribute page specific styles

Your complete folder structure:

```
mits-website/
├── index.html
├── about.html
├── guide.html
├── contribute.html
└── css/
    ├── base.css
    ├── layout.css
    ├── index.css
    ├── about.css
    ├── guide.css
    └── contribute.css
```

---

## Task 3: Create the Home Page (index.html)

### Step 3.1: Add the HTML5 Document Structure

Open `index.html` and add the basic HTML5 structure:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta
      name="description"
      content="MITS - Marketable IT Skills platform for vocational education"
    />
    <title>MITS - Marketable IT Skills Platform</title>

    <!-- CSS Files -->
    <link rel="stylesheet" href="css/base.css" />
    <link rel="stylesheet" href="css/layout.css" />
    <link rel="stylesheet" href="css/index.css" />
  </head>
  <body>
    <!-- Content will go here -->
  </body>
</html>
```

> **Note:** The `<meta name="viewport">` tag is crucial for responsive design on mobile devices.

### Step 3.2: Add the Header with Navigation

Inside the `<body>` tag, add the header:

```html
<body>
  <!-- Header with Navigation -->
  <header>
    <div class="container">
      <div class="logo">
        <span class="logo-icon">📦</span>
        <span>MITS Platform</span>
      </div>
      <nav>
        <ul>
          <li><a href="index.html" class="active">Home</a></li>
          <li><a href="about.html">About</a></li>
          <li><a href="guide.html">Guide</a></li>
          <li><a href="contribute.html">Contribute</a></li>
        </ul>
      </nav>
    </div>
  </header>

  <!-- More content will go here -->
</body>
```

> **Note:** The `class="active"` will help us highlight the current page in navigation. We'll style this in later tasks.

### Step 3.3: Add the Main Content Area with Hero Section

After the header, add the `<main>` element with a hero section:

```html
<!-- Main Content -->
<main>
  <!-- Hero Section -->
  <section class="hero">
    <div class="container">
      <h1>MITS - Marketable IT Skills</h1>
      <p class="subtitle">Real Competition Tasks for Vocational Education</p>
      <a href="about.html" class="btn">Learn More</a>
    </div>
  </section>

  <!-- More sections will go here -->
</main>
```

> **Note:** Each page should have only ONE `<h1>` tag for proper heading hierarchy and SEO.

### Step 3.4: Add the Introduction Section

After the hero section (inside `<main>`), add the intro section:

```html
<!-- Introduction Section -->
<section class="intro">
  <div class="container">
    <h2>Welcome to MITS Platform</h2>
    <p>
      The MITS (Marketable IT Skills) platform provides real competition tasks
      from European and international programming and web development
      competitions, adapted for vocational education. Our goal is to bridge the
      gap between classroom learning and industry-ready skills.
    </p>
    <p>
      Students work on authentic projects that mirror real-world challenges,
      building portfolios while learning modern web technologies, best
      practices, and professional development workflows.
    </p>
    <a href="about.html" class="btn">Discover More</a>
  </div>
</section>
```

### Step 3.5: Add the Featured Projects Section

After the intro section, add the featured projects section with 3 project cards:

```html
<!-- Featured Projects Section -->
<section class="featured-projects">
  <div class="container">
    <h2>Featured Projects</h2>

    <div class="projects-grid">
      <!-- Project Card 1 -->
      <article class="project-card">
        <h3>ES2025 TRAINING HU S17 - Module A</h3>
        <p class="card-subtitle">SkillShare Academy - Static Website Design</p>

        <div class="badges">
          <span class="badge">EuroSkills 2025 Training - Hungary</span>
          <span class="badge-lang">🇬🇧 EN</span>
        </div>

        <div class="tags">
          <span class="tag">frontend</span>
          <span class="tag">static website</span>
          <span class="tag">HTML5</span>
          <span class="tag">CSS3</span>
        </div>

        <p class="card-description">
          Create a professional static website for SkillShare Academy using
          semantic HTML5 and modern CSS3 techniques. Includes responsive design,
          accessibility, and SEO optimization.
        </p>
      </article>

      <!-- Project Card 2 -->
      <article class="project-card">
        <h3>ES2025 TRAINING HU S17 - Module B</h3>
        <p class="card-subtitle">SkillShare Academy - Dynamic Website</p>

        <div class="badges">
          <span class="badge">EuroSkills 2025 Training - Hungary</span>
          <span class="badge-lang">🇬🇧 EN</span>
        </div>

        <div class="tags">
          <span class="tag">backend</span>
          <span class="tag">server-side</span>
          <span class="tag">authentication</span>
          <span class="tag">MySQL</span>
        </div>

        <p class="card-description">
          Build a server-side rendered administrative interface with role-based
          access control, user authentication, and database integration for the
          SkillShare Academy platform.
        </p>
      </article>

      <!-- Project Card 3 -->
      <article class="project-card">
        <h3>ES2025 TRAINING HU S17 - Module C</h3>
        <p class="card-subtitle">SkillShare Academy REST API</p>

        <div class="badges">
          <span class="badge">EuroSkills 2025 Training - Hungary</span>
          <span class="badge-lang">🇬🇧 EN</span>
        </div>

        <div class="tags">
          <span class="tag">backend</span>
          <span class="tag">api</span>
          <span class="tag">rest api</span>
          <span class="tag">database</span>
        </div>

        <p class="card-description">
          Develop a RESTful API for the SkillShare Academy platform with proper
          authentication, data validation, and database operations following
          industry best practices.
        </p>
      </article>
    </div>

    <!-- Call-to-Action Buttons -->
    <div class="cta-buttons">
      <a href="guide.html" class="btn btn-primary">Register</a>
      <a href="guide.html" class="btn btn-secondary">Sign In</a>
    </div>
  </div>
</section>
```

> **Note:** We're using `<article>` for project cards because each card is self-contained content that could stand alone.

### Step 3.6: Add the Collaboration Section

After the featured projects section, add the collaboration section:

```html
<!-- Collaboration Section -->
<section class="collaboration">
  <div class="container">
    <h2>Collaborate with MITS</h2>
    <p>
      Are you an educator or industry expert? Join us in creating real-world
      learning experiences for vocational students. We're looking for partners
      to contribute competition tasks, provide mentorship, and help shape the
      future of IT education.
    </p>
    <a href="contribute.html" class="btn">Get Involved</a>
  </div>
</section>
```

### Step 3.7: Add the Footer

After the `</main>` closing tag, add the footer:

```html
<!-- Footer -->
<footer>
  <div class="container">
    <div class="footer-content">
      <div class="footer-section">
        <h4>MITS Platform</h4>
        <p>Marketable IT Skills for Vocational Education</p>
      </div>

      <div class="footer-section">
        <h4>Contact</h4>
        <p>Email: info@mits-platform.org</p>
        <p>GitHub: github.com/marketable-it-skills</p>
      </div>

      <div class="footer-section">
        <h4>Quick Links</h4>
        <ul>
          <li><a href="about.html">About</a></li>
          <li><a href="guide.html">Guide</a></li>
          <li><a href="contribute.html">Contribute</a></li>
        </ul>
      </div>
    </div>

    <div class="footer-bottom">
      <p>&copy; 2025 MITS Initiative. All rights reserved.</p>
    </div>
  </div>
</footer>
```

### Step 3.8: Verify Complete Structure

Your complete `index.html` should now have:

- ✅ `<!DOCTYPE html>` declaration
- ✅ `<head>` with meta tags and CSS links
- ✅ `<header>` with logo and navigation
- ✅ `<main>` with 4 sections (hero, intro, featured projects, collaboration)
- ✅ `<footer>` with contact info and links

---

## Task 4: Create the Other 3 Pages

### Step 4.1: Create the About Page (about.html)

Create `about.html` with this structure:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta
      name="description"
      content="Learn about the MITS platform and our mission"
    />
    <title>About MITS - Marketable IT Skills Platform</title>

    <!-- CSS Files -->
    <link rel="stylesheet" href="css/base.css" />
    <link rel="stylesheet" href="css/layout.css" />
    <link rel="stylesheet" href="css/about.css" />
  </head>
  <body>
    <!-- Header with Navigation -->
    <header>
      <div class="container">
        <div class="logo">
          <span class="logo-icon">📦</span>
          <span>MITS Platform</span>
        </div>
        <nav>
          <ul>
            <li><a href="index.html">Home</a></li>
            <li><a href="about.html" class="active">About</a></li>
            <li><a href="guide.html">Guide</a></li>
            <li><a href="contribute.html">Contribute</a></li>
          </ul>
        </nav>
      </div>
    </header>

    <!-- Main Content -->
    <main>
      <!-- Page Title Section -->
      <section class="page-title">
        <div class="container">
          <h1>About MITS</h1>
          <p class="subtitle">Real Competition Tasks for Real-World Skills</p>
        </div>
      </section>

      <!-- Mission Section -->
      <section class="mission">
        <div class="container">
          <h2>Our Mission</h2>
          <p>
            The MITS (Marketable IT Skills) initiative bridges the gap between
            vocational education and industry demands by providing access to
            authentic competition tasks from EuroSkills, WorldSkills, and other
            international programming competitions.
          </p>
          <p>
            We believe students learn best when working on real-world projects
            that have been validated by industry experts and used in competitive
            settings. Our platform makes these high-quality learning resources
            accessible to vocational schools worldwide.
          </p>
        </div>
      </section>

      <!-- Project Goals Section -->
      <section class="goals">
        <div class="container">
          <h2>Project Goals</h2>
          <ul class="goals-list">
            <li>
              <strong>Bridge theory and practice</strong> - Connect classroom
              learning with industry-ready skills through authentic projects
            </li>
            <li>
              <strong>Provide quality resources</strong> - Curate and adapt
              competition tasks for educational settings
            </li>
            <li>
              <strong>Support educators</strong> - Offer ready-to-use project
              specifications and teaching materials
            </li>
            <li>
              <strong>Build portfolios</strong> - Help students create
              professional portfolios with real project work
            </li>
            <li>
              <strong>Foster best practices</strong> - Teach modern development
              workflows, version control, and professional standards
            </li>
          </ul>
          <a href="guide.html" class="btn">Register Now</a>
        </div>
      </section>

      <!-- Platform Features Section -->
      <section class="features">
        <div class="container">
          <h2>Platform Features</h2>
          <div class="features-grid">
            <div class="feature">
              <h3>📚 Curated Projects</h3>
              <p>
                Access to 25+ competition tasks from EuroSkills, WorldSkills,
                and regional competitions, adapted for educational use.
              </p>
            </div>

            <div class="feature">
              <h3>🎯 Structured Learning</h3>
              <p>
                Each project includes detailed specifications, learning
                objectives, and step-by-step guidance for students.
              </p>
            </div>

            <div class="feature">
              <h3>💼 Industry Relevance</h3>
              <p>
                Work on tasks that reflect real industry challenges and current
                technology trends.
              </p>
            </div>

            <div class="feature">
              <h3>🌍 Multilingual Support</h3>
              <p>
                Projects available in multiple languages to serve diverse
                student populations.
              </p>
            </div>
          </div>
        </div>
      </section>
    </main>

    <!-- Footer -->
    <footer>
      <div class="container">
        <div class="footer-content">
          <div class="footer-section">
            <h4>MITS Platform</h4>
            <p>Marketable IT Skills for Vocational Education</p>
          </div>

          <div class="footer-section">
            <h4>Contact</h4>
            <p>Email: info@mits-platform.org</p>
            <p>GitHub: github.com/marketable-it-skills</p>
          </div>

          <div class="footer-section">
            <h4>Quick Links</h4>
            <ul>
              <li><a href="about.html">About</a></li>
              <li><a href="guide.html">Guide</a></li>
              <li><a href="contribute.html">Contribute</a></li>
            </ul>
          </div>
        </div>

        <div class="footer-bottom">
          <p>&copy; 2025 MITS Initiative. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </body>
</html>
```

> **Note:** Notice how the `class="active"` is on the "About" link now, not "Home".

### Step 4.2: Create the Guide Page (guide.html)

Create `guide.html` with this structure:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta
      name="description"
      content="Getting started with MITS platform - Registration and user guide"
    />
    <title>Getting Started - MITS Platform</title>

    <!-- CSS Files -->
    <link rel="stylesheet" href="css/base.css" />
    <link rel="stylesheet" href="css/layout.css" />
    <link rel="stylesheet" href="css/guide.css" />
  </head>
  <body>
    <!-- Header with Navigation -->
    <header>
      <div class="container">
        <div class="logo">
          <span class="logo-icon">📦</span>
          <span>MITS Platform</span>
        </div>
        <nav>
          <ul>
            <li><a href="index.html">Home</a></li>
            <li><a href="about.html">About</a></li>
            <li><a href="guide.html" class="active">Guide</a></li>
            <li><a href="contribute.html">Contribute</a></li>
          </ul>
        </nav>
      </div>
    </header>

    <!-- Main Content -->
    <main>
      <!-- Page Title Section -->
      <section class="page-title">
        <div class="container">
          <h1>Getting Started</h1>
          <p class="subtitle">Your Guide to MITS Platform</p>
        </div>
      </section>

      <!-- How to Use Section -->
      <section class="how-to-use">
        <div class="container">
          <h2>How to Use MITS Platform</h2>

          <div class="step">
            <h3>Step 1: Create an Account</h3>
            <p>
              Register for a free account using your GitHub credentials. This
              will allow you to access project specifications and track your
              progress.
            </p>
          </div>

          <div class="step">
            <h3>Step 2: Browse Projects</h3>
            <p>
              Explore our collection of competition tasks. Filter by technology,
              difficulty level, or competition source to find projects that
              match your learning goals.
            </p>
          </div>

          <div class="step">
            <h3>Step 3: Start Building</h3>
            <p>
              Each project includes detailed specifications, starter files, and
              expected outcomes. Follow the guidelines and build at your own
              pace.
            </p>
          </div>

          <div class="step">
            <h3>Step 4: Share Your Work</h3>
            <p>
              Submit your completed projects to your portfolio, share with
              instructors, or showcase to potential employers.
            </p>
          </div>
        </div>
      </section>

      <!-- Prerequisites Section -->
      <section class="prerequisites">
        <div class="container">
          <h2>Prerequisites</h2>

          <h3>Required Skills</h3>
          <ul>
            <li>Basic HTML, CSS, and JavaScript knowledge</li>
            <li>Understanding of web development fundamentals</li>
            <li>Familiarity with code editors and browsers</li>
          </ul>

          <h3>Technical Requirements</h3>
          <ul>
            <li>
              <strong>GitHub Account</strong> - For version control and project
              submissions
            </li>
            <li>
              <strong>Code Editor</strong> - VS Code, Sublime Text, or similar
            </li>
            <li><strong>Modern Browser</strong> - Chrome, Firefox, or Edge</li>
            <li>
              <strong>Node.js</strong> (optional) - For projects requiring build
              tools
            </li>
          </ul>
        </div>
      </section>

      <!-- Call-to-Action Section -->
      <section class="cta">
        <div class="container">
          <h2>Ready to Start?</h2>
          <p>
            Join thousands of students building real-world projects and
            developing marketable IT skills.
          </p>
          <div class="cta-buttons">
            <a href="#" class="btn btn-primary">Register Now</a>
            <a href="index.html" class="btn btn-secondary">Browse Projects</a>
          </div>
        </div>
      </section>
    </main>

    <!-- Footer -->
    <footer>
      <div class="container">
        <div class="footer-content">
          <div class="footer-section">
            <h4>MITS Platform</h4>
            <p>Marketable IT Skills for Vocational Education</p>
          </div>

          <div class="footer-section">
            <h4>Contact</h4>
            <p>Email: info@mits-platform.org</p>
            <p>GitHub: github.com/marketable-it-skills</p>
          </div>

          <div class="footer-section">
            <h4>Quick Links</h4>
            <ul>
              <li><a href="about.html">About</a></li>
              <li><a href="guide.html">Guide</a></li>
              <li><a href="contribute.html">Contribute</a></li>
            </ul>
          </div>
        </div>

        <div class="footer-bottom">
          <p>&copy; 2025 MITS Initiative. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </body>
</html>
```

### Step 4.3: Create the Contribute Page (contribute.html)

Create `contribute.html` with this structure:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta
      name="description"
      content="Collaborate with MITS - Contribute to vocational IT education"
    />
    <title>Collaborate - MITS Platform</title>

    <!-- CSS Files -->
    <link rel="stylesheet" href="css/base.css" />
    <link rel="stylesheet" href="css/layout.css" />
    <link rel="stylesheet" href="css/contribute.css" />
  </head>
  <body>
    <!-- Header with Navigation -->
    <header>
      <div class="container">
        <div class="logo">
          <span class="logo-icon">📦</span>
          <span>MITS Platform</span>
        </div>
        <nav>
          <ul>
            <li><a href="index.html">Home</a></li>
            <li><a href="about.html">About</a></li>
            <li><a href="guide.html">Guide</a></li>
            <li><a href="contribute.html" class="active">Contribute</a></li>
          </ul>
        </nav>
      </div>
    </header>

    <!-- Main Content -->
    <main>
      <!-- Page Title Section -->
      <section class="page-title">
        <div class="container">
          <h1>Collaborate with MITS</h1>
          <p class="subtitle">
            Help Shape the Future of Vocational IT Education
          </p>
        </div>
      </section>

      <!-- Introduction Section -->
      <section class="intro">
        <div class="container">
          <p>
            The MITS platform thrives on collaboration between educators,
            industry professionals, and competition organizers. Whether you're a
            teacher looking to share your expertise, a developer wanting to give
            back, or an organization with competition tasks to contribute, we
            welcome your involvement.
          </p>
        </div>
      </section>

      <!-- Contribution Opportunities Section -->
      <section class="opportunities">
        <div class="container">
          <h2>How You Can Contribute</h2>

          <div class="opportunity">
            <h3>🎓 Educators & Teachers</h3>
            <p>
              Share your teaching experience by creating course materials,
              workshop guides, or tutorial content. Help us adapt competition
              tasks for classroom use and provide feedback on learning
              resources.
            </p>
            <ul>
              <li>Develop teaching materials and lesson plans</li>
              <li>Create tutorial videos or written guides</li>
              <li>Review and test educational content</li>
              <li>Share classroom success stories</li>
            </ul>
          </div>

          <div class="opportunity">
            <h3>💻 Industry Professionals</h3>
            <p>
              Bring real-world expertise to vocational education. Contribute
              competition tasks, provide technical mentorship, or review student
              projects to ensure industry relevance.
            </p>
            <ul>
              <li>Submit and adapt competition tasks</li>
              <li>Mentor students on projects</li>
              <li>Provide code reviews and technical feedback</li>
              <li>Share industry best practices</li>
            </ul>
          </div>

          <div class="opportunity">
            <h3>🏆 Competition Organizers</h3>
            <p>
              Partner with us to make competition tasks accessible for
              educational purposes. We ensure proper attribution and handle the
              adaptation process for classroom use.
            </p>
            <ul>
              <li>License tasks for educational use</li>
              <li>Collaborate on task adaptation</li>
              <li>Promote skills competitions to students</li>
              <li>Build bridges between education and competition</li>
            </ul>
          </div>

          <div class="opportunity">
            <h3>🌟 Open Source Contributors</h3>
            <p>
              Help improve the MITS platform itself. Contribute code, fix bugs,
              improve documentation, or suggest new features on our GitHub
              repository.
            </p>
            <ul>
              <li>Contribute to platform development</li>
              <li>Improve documentation</li>
              <li>Report and fix bugs</li>
              <li>Suggest new features</li>
            </ul>
          </div>
        </div>
      </section>

      <!-- Get Involved Section -->
      <section class="get-involved">
        <div class="container">
          <h2>Get Involved</h2>
          <p>
            Interested in contributing? We'd love to hear from you! Reach out to
            discuss collaboration opportunities, partnership possibilities, or
            any questions you might have.
          </p>

          <div class="contact-info">
            <p><strong>Email:</strong> contribute@mits-platform.org</p>
            <p>
              <strong>GitHub:</strong> github.com/marketable-it-skills/platform
            </p>
            <p>
              <strong>Discussions:</strong> Join our GitHub Discussions to
              connect with the community
            </p>
          </div>

          <a href="#" class="btn btn-primary">Contact Us</a>
        </div>
      </section>
    </main>

    <!-- Footer -->
    <footer>
      <div class="container">
        <div class="footer-content">
          <div class="footer-section">
            <h4>MITS Platform</h4>
            <p>Marketable IT Skills for Vocational Education</p>
          </div>

          <div class="footer-section">
            <h4>Contact</h4>
            <p>Email: info@mits-platform.org</p>
            <p>GitHub: github.com/marketable-it-skills</p>
          </div>

          <div class="footer-section">
            <h4>Quick Links</h4>
            <ul>
              <li><a href="about.html">About</a></li>
              <li><a href="guide.html">Guide</a></li>
              <li><a href="contribute.html">Contribute</a></li>
            </ul>
          </div>
        </div>

        <div class="footer-bottom">
          <p>&copy; 2025 MITS Initiative. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </body>
</html>
```

---

## Task 5: Verify CSS File Links

In this module, we're focusing purely on HTML structure. The CSS files are linked in your HTML but will remain empty for now.

### Step 5.1: Verify CSS Files Exist

Make sure you have created all 6 CSS files in the `css/` folder:

- ✅ `base.css`
- ✅ `layout.css`
- ✅ `index.css`
- ✅ `about.css`
- ✅ `guide.css`
- ✅ `contribute.css`

### Step 5.2: Leave CSS Files Empty

**Keep all CSS files empty for now.** We will implement the CSS in Module 2, where we'll learn:

- CSS reset and box model
- CSS custom properties (variables)
- Typography and color schemes
- Flexbox for header and footer layout
- Grid for responsive layouts

> **Note:** Your website will look unstyled at this point - that's completely normal! We're building the HTML foundation first, then we'll add beautiful styling in Module 2.

---

## Task 6: Test Your HTML Structure

### Step 6.1: Open index.html in Your Browser

1. Navigate to your project folder
2. Right-click on `index.html`
3. Choose "Open with" → Your web browser (or use Live Server in VS Code)

> **Note:** Your page will look **unstyled** (plain black text on white background) - that's expected! We're only checking HTML structure in this module.

### Step 6.2: Verify the Home Page Structure

Check that you can see all content elements:

- ✅ Header with logo text and navigation links
- ✅ Hero section with title and subtitle
- ✅ Introduction section text
- ✅ 3 project cards with titles and descriptions
- ✅ Collaboration section
- ✅ Footer with contact information

### Step 6.3: Test Navigation

Click each navigation link:

- ✅ "Home" → `index.html`
- ✅ "About" → `about.html`
- ✅ "Guide" → `guide.html`
- ✅ "Contribute" → `contribute.html`

Verify that:

- All pages load correctly
- All content is readable
- Links work between pages
- Each page has similar structure (header, main content, footer)

---

## Task 7: Validate Your HTML

### Step 7.1: Use the W3C Validator

1. Go to [https://validator.w3.org/#validate_by_upload](https://validator.w3.org/#validate_by_upload)
2. Upload `index.html`
3. Check for errors

### Step 7.2: Fix Any Errors

If you see errors:

- Read the error message carefully
- Find the line number mentioned
- Fix the issue (common: unclosed tags, missing attributes)
- Re-validate

### Step 7.3: Validate All Pages

Repeat validation for:

- ✅ `index.html`
- ✅ `about.html`
- ✅ `guide.html`
- ✅ `contribute.html`

---

## Task 8: Version Control with Git

Now that your website is complete and validated, let's save your work using Git - the industry-standard version control system. This teaches you professional development practices from day one!

### What is Git?

Git is a version control system that:

- Tracks changes to your code over time
- Allows you to work on features in separate branches
- Enables collaboration with other developers
- Backs up your work to remote repositories (like GitHub)

### Step 8.1: Initialize Git Repository

Open your terminal in your project folder and run:

```bash
git init
```

**What this does:** Creates a new Git repository in your project folder. You'll see a message like "Initialized empty Git repository".

> **Note:** If you don't have Git installed, download it from [git-scm.com](https://git-scm.com/)

### Step 8.2: Create Feature Branch

```bash
git checkout -b feat/module-1-workshop
```

**What this does:** Creates and switches to a new branch called `feat/module-1-workshop`. This is a **feature branch** - a best practice for organizing your work.

> **Why branches?** Working on branches keeps your main code clean. You develop features on branches, then merge them when complete.

### Step 8.3: Stage Your Changes

```bash
git add .
```

**What this does:** Stages all your files (the `.` means "everything") to prepare them for commit. Think of this as preparing files to be photographed.

**Verify what's staged:**

```bash
git status
```

You should see all your HTML and CSS files listed in green.

### Step 8.4: Commit Your Work

```bash
git commit -m "Complete Module 1: HTML structure with semantic markup"
```

**What this does:** Creates a commit (snapshot) of your work with a descriptive message.

> **Commit message tips:**
>
> - Start with a verb (Complete, Add, Fix, Update)
> - Be descriptive but concise
> - Explain WHAT you did, not HOW

### Step 8.5: Switch to Main Branch

```bash
git checkout main
```

**What this does:** Switches back to the `main` branch. This is your primary branch - the "production-ready" version of your code.

> **Note:** If you get an error saying main doesn't exist, create it first: `git checkout -b main`

### Step 8.6: Merge Feature Branch

```bash
git merge feat/module-1-workshop
```

**What this does:** Merges your feature branch into main. Your Module 1 work is now part of your main codebase!

You should see a message like "Fast-forward" with files updated.

### Step 8.7: Create GitHub Repository

Now let's back up your work to GitHub (free remote repository hosting):

1. Go to [GitHub.com](https://github.com)
2. Sign in (or create a free account if you don't have one)
3. Click the **"+"** icon in the top-right
4. Click **"New repository"**
5. Repository settings:
   - **Name:** `mits-website` (or your preferred name)
   - **Description:** "MITS Platform Website - Design & Implementation Tutorial"
   - **Visibility:** Public (so you can share it!)
   - **Important:** Do NOT check "Initialize with README" (you already have files)
6. Click **"Create repository"**

GitHub will show you commands - we'll use them in the next step!

### Step 8.8: Connect to GitHub

Copy your repository URL from GitHub (it looks like: `https://github.com/YOUR-USERNAME/mits-website.git`)

Run these commands in your terminal:

```bash
git remote add origin https://github.com/YOUR-USERNAME/mits-website.git
git branch -M main
git push -u origin main
```

**Replace `YOUR-USERNAME`** with your actual GitHub username!

**What these do:**

- `git remote add origin ...` - Connects your local repository to GitHub
- `git branch -M main` - Ensures your branch is named "main"
- `git push -u origin main` - Uploads your code to GitHub

You'll be prompted for your GitHub credentials. After entering them, your code will be pushed!

### Step 8.9: Verify on GitHub

1. Go back to your GitHub repository page
2. Refresh the page
3. You should see all your files:
   - ✅ `index.html`, `about.html`, `guide.html`, `contribute.html`
   - ✅ `css/` folder with all CSS files
   - ✅ Your commit message

**Congratulations!** Your code is now backed up on GitHub and accessible from anywhere!

> **Share your work:** You can share the GitHub repository URL with others to showcase your project!

### Step 8.10: View Your Git History

```bash
git log --oneline
```

**What this does:** Shows your commit history in a compact format. You should see your Module 1 commit!

---

## Congratulations! 🎉

You've completed Module 1! You now have:

- ✅ A complete 4-page website with semantic HTML5 structure
- ✅ Working navigation between all pages
- ✅ Properly organized file structure with HTML and CSS files
- ✅ Valid, accessible HTML code
- ✅ Understanding of semantic HTML elements
- ✅ **Professional Git workflow** - Your code is version controlled and on GitHub!

**Your HTML foundation is solid!** Right now your website looks unstyled - and that's perfect! You've proven that good HTML structure works even without CSS.

## What's Next?

### Module 2: CSS Fundamentals - Base & Layout

In the next module, you'll transform your plain HTML into a beautiful dark-themed website by implementing:

**`base.css`** - Foundation styles:

- CSS reset and box model
- CSS custom properties (variables)
- Color scheme (dark theme)
- Typography (fonts, sizes, spacing)
- Base component styles (buttons, links)

**`layout.css`** - Structural layout:

- Header and navigation with Flexbox
- Footer with CSS Grid
- Container and section spacing
- Sticky header positioning

By the end of Module 2, your site will have a professional dark theme with proper layout!

### Future Modules

- **Module 3**: Page-specific CSS (index.css, about.css, guide.css, contribute.css)
- **Module 4**: Advanced CSS & Responsive Design
- **Module 5**: Interactive Elements & Polish

Keep your files organized and get ready to bring your HTML to life with CSS! 🚀
