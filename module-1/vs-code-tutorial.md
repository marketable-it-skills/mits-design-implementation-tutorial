# VS Code Guide for MITS Project

Visual Studio Code is a powerful, free code editor that's perfect for web development. This guide covers the essential extensions, shortcuts, and best practices for building the MITS Platform Website.

## Why VS Code?

- **Free and open-source**
- **Built-in Emmet support** for fast HTML/CSS writing
- **Live Server** for instant preview
- **IntelliSense** for smart code completion
- **Integrated terminal**
- **Git integration**
- **Huge extension marketplace**

---

## Essential Extensions for This Project

### 1. Live Server ⭐ **MUST HAVE**

**What it does:** Launches a local development server with live reload

**Why you need it:** See your HTML/CSS changes instantly in the browser without manually refreshing

**How to install:**

1. Click Extensions icon (or `Ctrl+Shift+X`)
2. Search "Live Server"
3. Click Install on "Live Server" by Ritwick Dey

**How to use:**

- Right-click on any HTML file → "Open with Live Server"
- Or click "Go Live" in the bottom-right status bar
- Your site opens at `http://127.0.0.1:5500`
- Changes auto-reload in browser!

---

### 2. Prettier - Code Formatter ⭐ **HIGHLY RECOMMENDED**

**What it does:** Automatically formats your HTML/CSS to look clean and consistent

**Why you need it:** Keeps your code readable and professionally formatted

**How to install:**

1. Extensions → Search "Prettier"
2. Install "Prettier - Code formatter"

**How to use:**

- Save file: `Ctrl+S` (auto-formats if enabled)
- Manual format: `Shift+Alt+F`

**Setup:**

1. `Ctrl+,` to open Settings
2. Search "format on save"
3. Check ✅ "Editor: Format On Save"
4. Search "default formatter"
5. Select "Prettier - Code formatter"

---

### 3. Auto Rename Tag ⭐ **HIGHLY RECOMMENDED**

**What it does:** Automatically renames paired HTML tags

**Why you need it:** Change `<div>` to `<section>` - both opening and closing tags update automatically!

**How to install:**

1. Extensions → Search "Auto Rename Tag"
2. Install by Jun Han

**Example:**

```html
<!-- Change this: -->
<div class="hero">
  <h1>Title</h1>
</div>

<!-- Type "section" over "div" and watch the closing tag update automatically! -->
<section class="hero">
  <h1>Title</h1>
</section>
```

---

### 4. HTML CSS Support

**What it does:** IntelliSense for CSS class names in HTML

**Why you need it:** Autocomplete class names from your CSS files

**How to install:**

1. Extensions → Search "HTML CSS Support"
2. Install by ecmel

---

### 5. Color Highlight

**What it does:** Highlights color codes with the actual color

**Why you need it:** Visually see colors in your CSS without checking the browser

**How to install:**

1. Extensions → Search "Color Highlight"
2. Install by Sergii N

**Example:** `#0f172a` will show the dark blue background color inline!

---

### 6. Path Intellisense

**What it does:** Autocompletes file paths

**Why you need it:** Quickly link CSS files and navigate between pages

**How to install:**

1. Extensions → Search "Path Intellisense"
2. Install by Christian Kohler

**Example:** Type `href="css/` and it suggests `base.css`, `layout.css`, etc.

---

### 7. Indent Rainbow (Optional but Nice)

**What it does:** Colors indentation levels

**Why you need it:** Makes nested HTML structure easier to read

**How to install:**

1. Extensions → Search "Indent Rainbow"
2. Install by oderwat

---

## Essential Keyboard Shortcuts

> **⚠️ Important Note:** These shortcuts are shown for **US English (QWERTY)** keyboard layout. If you're using a different keyboard layout (e.g., Hungarian, German, French), some shortcuts may be different. You can:
>
> - View your keyboard shortcuts: `File → Preferences → Keyboard Shortcuts` (or `Ctrl+K Ctrl+S`)
> - Search for commands by name if a shortcut doesn't work
> - Customize shortcuts to match your preferences
> - Use `Ctrl+Shift+P` (Command Palette) to access any command by typing its name

### File Management

| Shortcut       | Action               | When to Use                           |
| -------------- | -------------------- | ------------------------------------- |
| `Ctrl+N`       | New file             | Creating new HTML/CSS files           |
| `Ctrl+S`       | Save file            | After making changes (do this often!) |
| `Ctrl+Shift+S` | Save all files       | Before testing in browser             |
| `Ctrl+W`       | Close current file   | Closing tabs                          |
| `Ctrl+P`       | Quick file open      | Jump to any file quickly              |
| `Ctrl+Tab`     | Switch between files | Navigate open files                   |
| `Ctrl+B`       | Toggle sidebar       | More screen space for code            |
| `Ctrl+`\``     | Toggle terminal      | Open/close integrated terminal        |

---

### Editing

| Shortcut        | Action                  | When to Use                            |
| --------------- | ----------------------- | -------------------------------------- |
| `Ctrl+D`        | Select next occurrence  | Change multiple instances of same word |
| `Ctrl+Shift+L`  | Select all occurrences  | Change all at once                     |
| `Alt+Click`     | Multiple cursors        | Edit multiple lines simultaneously     |
| `Ctrl+/`        | Toggle comment          | Comment out code                       |
| `Shift+Alt+↓/↑` | Duplicate line          | Copy line up/down                      |
| `Alt+↓/↑`       | Move line up/down       | Reorder code                           |
| `Ctrl+Shift+K`  | Delete line             | Remove entire line                     |
| `Ctrl+X`        | Cut line (no selection) | Cut entire line                        |
| `Ctrl+]`        | Indent line             | Add indentation                        |
| `Ctrl+[`        | Outdent line            | Remove indentation                     |

---

### Code Navigation

| Shortcut       | Action            | When to Use                  |
| -------------- | ----------------- | ---------------------------- |
| `Ctrl+G`       | Go to line        | Jump to specific line number |
| `Ctrl+Home`    | Go to beginning   | Top of file                  |
| `Ctrl+End`     | Go to end         | Bottom of file               |
| `Ctrl+F`       | Find              | Search in current file       |
| `Ctrl+H`       | Find and replace  | Change multiple instances    |
| `Ctrl+Shift+F` | Find in all files | Search entire project        |
| `Ctrl+Shift+O` | Go to symbol      | Jump to CSS class/ID         |

---

### Selection

| Shortcut         | Action           | When to Use                   |
| ---------------- | ---------------- | ----------------------------- |
| `Ctrl+A`         | Select all       | Select entire file            |
| `Shift+→/←`      | Extend selection | Select character by character |
| `Ctrl+Shift+→/←` | Select word      | Select whole words            |
| `Shift+Alt+→`    | Expand selection | Select entire HTML tag        |
| `Shift+Alt+←`    | Shrink selection | Deselect outer tag            |

---

### Display

| Shortcut | Action            | When to Use                 |
| -------- | ----------------- | --------------------------- |
| `Ctrl++` | Zoom in           | Make text larger            |
| `Ctrl+-` | Zoom out          | Make text smaller           |
| `Ctrl+0` | Reset zoom        | Back to default size        |
| `F11`    | Toggle fullscreen | Distraction-free coding     |
| `Ctrl+\` | Split editor      | View two files side by side |

---

## Most Useful Shortcuts for This Project

### 1. Quick File Switching: `Ctrl+P`

Type partial filename to jump instantly:

- Type "index" → `index.html`
- Type "base" → `css/base.css`

---

### 2. Multi-Cursor Editing: `Alt+Click`

Edit multiple places at once:

```html
<!-- Click after each opening tag while holding Alt -->
<li><a href="">Home</a></li>
<li><a href="">About</a></li>
<li><a href="">Guide</a></li>
<li><a href="">Contribute</a></li>
<!-- Now type once to edit all at the same time! -->
```

---

### 3. Select All Occurrences: `Ctrl+Shift+L`

Change all instances of a class name:

1. Select `.hero`
2. Press `Ctrl+Shift+L`
3. All instances are selected
4. Type new name: `.hero-section`

---

### 4. Duplicate Line: `Shift+Alt+↓`

Quickly create similar HTML elements:

```html
<li><a href="index.html">Home</a></li>
<!-- Press Shift+Alt+↓ to duplicate -->
<li><a href="index.html">Home</a></li>
<!-- Edit the duplicate -->
```

---

### 5. Toggle Comment: `Ctrl+/`

Quickly comment/uncomment code for testing:

```html
<!-- <section class="hero"> -->
<!--   Testing without hero section -->
<!-- </section> -->
```

---

## Pro Tips for This Project

### 1. Side-by-Side Editing

**Shortcut:** `Ctrl+\` (split editor)

**Use case:** View HTML and CSS files simultaneously

- HTML on left
- CSS on right
- See changes as you code!

---

### 2. Format Document

**Shortcut:** `Shift+Alt+F`

**Use case:** Clean up messy HTML/CSS instantly

- Fixes indentation
- Aligns code properly
- Makes code readable

---

### 3. Rename Symbol

**Shortcut:** `F2`

**Use case:** Rename a class across all files

1. Click on class name in HTML
2. Press `F2`
3. Type new name
4. Updates everywhere!

---

### 4. Peek Definition

**Shortcut:** `Alt+F12`

**Use case:** See CSS for a class without leaving HTML file

1. Click on class name in HTML
2. Press `Alt+F12`
3. CSS definition appears inline!

---

### 5. Quick Open Command Palette

**Shortcut:** `Ctrl+Shift+P`

**Use case:** Access any VS Code command

- "Emmet: Wrap with Abbreviation"
- "Format Document"
- "Change Language Mode"
- Everything!

---

## Essential Settings for This Project

### 1. Enable Format on Save

```
Ctrl+, → Search "format on save" → Check ✅
```

Your code auto-formats every time you save!

---

### 2. Auto Save

```
Ctrl+, → Search "auto save" → Select "afterDelay"
```

Files save automatically after 1 second of inactivity.

---

### 3. Word Wrap

```
Ctrl+, → Search "word wrap" → Select "on"
```

Long lines wrap instead of scrolling horizontally.

---

### 4. Tab Size (2 spaces for HTML/CSS)

```
Ctrl+, → Search "tab size" → Set to 2
```

Standard for HTML/CSS projects.

---

### 5. Emmet Enabled

```
Ctrl+, → Search "emmet" → Ensure enabled for html, css
```

Should be on by default, but verify!

---

## Workspace Organization Tips

### 1. Open Project Folder

**Always** open the entire project folder, not individual files:

```
File → Open Folder → Select "mits-website"
```

Benefits:

- See all files in sidebar
- Quick file switching works
- Path autocomplete works
- Search entire project

---

### 2. File Explorer

**Shortcut:** `Ctrl+Shift+E`

Quick actions:

- Right-click folder → New File
- Right-click folder → New Folder
- Drag files to move them
- Rename with `F2`

---

### 3. Breadcrumbs

Enable breadcrumbs to see file path at top:

```
View → Show Breadcrumbs
```

Shows: `mits-website > css > base.css`

---

## Live Server Tips

### 1. Start Live Server

**Method 1:** Right-click `index.html` → "Open with Live Server"

**Method 2:** Click "Go Live" in bottom status bar

---

### 2. Stop Live Server

Click "Port: 5500" in bottom status bar

---

### 3. Custom Port (if 5500 is taken)

```
Ctrl+, → Search "liveServer.settings.port" → Change to 5501
```

---

### 4. Open in Browser

Default: Opens in your default browser

To change:

```
Ctrl+, → Search "liveServer.settings.CustomBrowser" → Select "chrome" or "firefox"
```

---

## Common VS Code Workflows for This Project

### Workflow 1: Creating a New Page

1. `Ctrl+N` - New file
2. `Ctrl+S` - Save as `guide.html`
3. Type `!` + `Tab` - HTML boilerplate
4. Edit title and meta description
5. Type `link:css` + `Tab` (3 times for 3 CSS files)
6. Build page structure with Emmet
7. `Ctrl+S` - Save
8. Right-click → "Open with Live Server"

---

### Workflow 2: Editing CSS While Viewing

1. `Ctrl+\` - Split editor
2. Open `index.html` (left)
3. Open `css/index.css` (right)
4. Start Live Server
5. Edit CSS on right
6. `Ctrl+S` - Watch changes live in browser!

---

### Workflow 3: Finding and Replacing

1. `Ctrl+H` - Open find and replace
2. Type old class name: `hero`
3. Type new class name: `hero-section`
4. Click "Replace All" or `Ctrl+Alt+Enter`
5. All instances updated!

---

### Workflow 4: Fixing Indentation

Select messy code → `Shift+Alt+F` → Beautiful!

**Before:**

```html
<div class="hero">
  <h1>Title</h1>
  <p>Text</p>
</div>
```

**After:**

```html
<div class="hero">
  <h1>Title</h1>
  <p>Text</p>
</div>
```

---

## Troubleshooting Common Issues

### Issue: Live Server Not Working

**Solution:**

1. Make sure Live Server extension is installed
2. Right-click HTML file (not CSS file!)
3. Check firewall isn't blocking port 5500
4. Try different port in settings

---

### Issue: Emmet Not Expanding

**Solution:**

1. Make sure you're in an HTML file (not .txt)
2. Check file language mode (bottom right) - should say "HTML"
3. Press `Tab` (not Enter) after typing abbreviation
4. Verify Emmet is enabled: `Ctrl+,` → Search "emmet"

---

### Issue: Prettier Not Formatting

**Solution:**

1. Check Prettier is installed
2. Verify "Format On Save" is enabled
3. Check Prettier is default formatter
4. Try manual format: `Shift+Alt+F`

---

### Issue: Can't Find Files

**Solution:**

1. Open folder (not individual files): File → Open Folder
2. Use `Ctrl+P` to quick open
3. Check file is saved in correct location

---

### Issue: Keyboard Shortcut Not Working

**Solution:**

1. Check if you're using a non-US keyboard layout (Hungarian, German, etc.)
2. Open keyboard shortcuts: `File → Preferences → Keyboard Shortcuts` (or `Ctrl+K Ctrl+S`)
3. Search for the command name (e.g., "Toggle Comment")
4. See the actual shortcut for your keyboard layout
5. Optional: Customize the shortcut by clicking the pencil icon

**Tip:** Use `Ctrl+Shift+P` (Command Palette) to run any command by name if shortcuts don't work!

---

## Keyboard Shortcuts Cheat Sheet

**Print this section and keep it handy!**

### Top 10 Most Used Shortcuts

1. `Ctrl+S` - **Save** (use constantly!)
2. `Ctrl+P` - **Quick file open**
3. `Ctrl+D` - **Select next occurrence**
4. `Ctrl+/` - **Toggle comment**
5. `Shift+Alt+F` - **Format document**
6. `Ctrl+Space` - **Trigger IntelliSense**
7. `Alt+↓/↑` - **Move line**
8. `Shift+Alt+↓` - **Duplicate line**
9. `Ctrl+\` - **Split editor**
10. `Ctrl+B` - **Toggle sidebar**

---

## Additional Resources

- **VS Code Shortcuts PDF**: `Help` → `Keyboard Shortcuts Reference`
- **Interactive Tutorial**: `Help` → `Welcome` → "Interactive playground"
- **VS Code Tips**: [https://code.visualstudio.com/docs/getstarted/tips-and-tricks](https://code.visualstudio.com/docs/getstarted/tips-and-tricks)
- **Keyboard Shortcuts**: [https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)

---

## Practice Exercise

Try this workflow to practice shortcuts:

1. `Ctrl+N` - Create new file
2. `Ctrl+S` - Save as `practice.html`
3. Type `!` + `Tab` - Create HTML structure
4. `Ctrl+D` (multiple times) - Select all "Document" text
5. Type "Practice Page" - Replace all at once
6. `Ctrl+End` - Go to end of file
7. Type `section.hero>.container>h1+p` + `Tab` - Emmet!
8. `Shift+Alt+F` - Format document
9. Right-click → "Open with Live Server"
10. `Ctrl+W` - Close file

---

## Summary: Essential Setup Checklist

Before starting Module 1 workshop, ensure you have:

- ✅ VS Code installed
- ✅ Live Server extension installed
- ✅ Prettier extension installed
- ✅ Auto Rename Tag extension installed
- ✅ Format on Save enabled
- ✅ Tab size set to 2
- ✅ Project folder opened (not individual files)
- ✅ Know how to use `Ctrl+P`, `Ctrl+S`, `Shift+Alt+F`

---

**You're ready to code!** These tools and shortcuts will make you **5-10x faster** when building the MITS Platform Website. 🚀

Happy coding! ✨
