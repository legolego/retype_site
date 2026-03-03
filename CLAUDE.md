# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with this repository.

---

## Commands

### Development Commands

- **Start the Retype development server** (live preview):
  ```bash
  retype start
  ```

- **Build the site** (generates static files in output directory):
  ```bash
  retype build
  ```

- **View the built site locally**: The `retype build` command outputs to `C:/gitProjects/legolego.github.io`. You can serve it with:
  ```bash
  python -m http.server 4000 --directory C:/gitProjects/legolego.github.io
  ```

### Working with Content

- Don't use em-dashes in any new text, and remove em-dashes if you see them
- Instead of doing an "in-file" replacement, just write a new copy of the file from scratch, keeping the full content except for the segment you need to replace, and write that in accordingly.
- Edit the main Markdown files in `retype_src/` directly.
- Use Front Matter at the top of each `.md` file to set `label`, `layout`, and `order` for navigation.
- Images should be placed in `retype_src/static/` and referenced with relative paths.

---

## Code Architecture

### High-Level Structure

This is a **Retype** static site generator project that transforms Markdown files into a static website.

```
retype_src/
├── index.md              # Main landing page (order: 105)
├── Personal.md           # Personal projects (order: 104)
├── University.md         # University projects (order: 100)
├── global.json           # Retype SDK configuration
├── retype.yml            # Main config (input/output paths, branding, footer)
└── static/
    ├── lego.png          # Site logo
    ├── custom.css        # Custom CSS styling
    └── *.png             # Images used across the site
```

### Retype Front Matter Syntax

Each Markdown file uses YAML front matter for page configuration:
```yaml
---
label: "Page Title with Emoji"
layout: default
order: 100    # Determines navigation order (lower numbers appear first)
---
```

### Content Features

- **Inline images**: Use `![](path/to/image.png)` for static images
- **External links in Markdown**: Use `[text](url){target="_blank"}` for new tab links
- **Code highlighting**: Retype automatically detects code blocks with syntax highlighting
- **Automatic navigation**: Built-in side navigation based on file order and labels

### GitHub Pages Deployment

1. Make changes to `retype_src/` Markdown files
2. Run `retype build` to generate static site
3. Push contents of output folder (`C:/gitProjects/legolego.github.io`) to GitHub
4. Site auto-deploys via GitHub Pages (uses `.nojekyll` marker)

---

## Configuration Files

### retype.yml
```yaml
input: ./retype_src                    # Source directory
output: C:/gitProjects/legolego.github.io  # Build output path
url: https://legolego.github.io/
branding:
  logo: static/lego.png
  title: Oleg N
  label: Projects
footer:
  copyright: "&copy; Copyright {{ year }}. All rights reserved."
googleTagManager:
  id: "G-LKNMP7RRVM"
```

---

## Key Patterns

- **Navigation ordering**: Lower `order` values appear first in the navigation menu
- **Page labels**: Use descriptive labels with emojis for better visual hierarchy
- **Asset paths**: All images and assets use relative paths from `static/`
- **404 handling**: `.retype/404.html` provides custom error pages

---

## Notes

- The `.retype` directory is auto-generated and excluded from git via `.gitignore`
- Retype v7 SDK is configured in `global.json`
- Custom CSS in `static/custom.css` allows site-wide styling modifications
- No tests or lint commands needed - validate by running `retype build`
