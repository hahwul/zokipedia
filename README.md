# Zokipedia

A comprehensive knowledge base built with Zola, featuring a dark theme inspired by Grokipedia.

## Features

- 🔍 **Powerful Search** - Full-text search powered by Fuse.js
- 🌙 **Dark Theme** - Eye-friendly black background design
- 📱 **Responsive Design** - Works perfectly on all devices
- 📚 **Table of Contents** - Auto-generated TOC with active section highlighting
- ⚡ **Fast Performance** - Built with Zola static site generator
- ⌨️ **Keyboard Shortcuts** - Press `Cmd/Ctrl + K` to open search

## Design Inspiration

This theme is inspired by [Grokipedia](https://grokipedia.com) with the following features:

### Main Page
- **Dark background** - `rgb(20, 20, 20)` for optimal reading
- Clean, minimal search interface
- Recent articles grid layout
- Prominent search functionality

### Article Pages
- Left sidebar with Table of Contents
- **Enhanced TOC highlighting** - Light gray text with white highlighting for current section
- Clean typography optimized for reading
- Navigation header with search

## Quick Start

1. Install [Zola](https://www.getzola.org/documentation/getting-started/installation/)
2. Clone this repository
3. Run the development server:
   ```bash
   zola serve
   ```
4. Open http://127.0.0.1:1111 in your browser

## Project Structure

```
zokipedia/
├── config.toml          # Site configuration
├── content/             # Markdown content files
│   ├── _index.md        # Homepage content
│   └── *.md             # Article pages
├── templates/           # HTML templates
│   ├── base.html        # Base template with header/footer
│   ├── index.html       # Homepage template
│   └── page.html        # Article page template
├── sass/                # SCSS source files
│   └── style.scss       # Main stylesheet (compiles to style.css)
├── static/              # Static assets
│   ├── favicon.ico      # Site favicon
│   ├── css/             # Additional CSS files (optional)
│   ├── images/          # Image assets
│   └── js/              # JavaScript files
```

## Creating Content

Create a new article by adding a Markdown file to the `content/` directory:

```markdown
+++
title = "Your Article Title"
date = 2024-01-15
description = "Article description for SEO"
tags = ["tag1", "tag2"]
+++

# Your Article Title

Your content here...
```

## Shortcodes

### Math Shortcode

The math shortcode allows you to include mathematical expressions using LaTeX syntax:

**Display Math:**
```markdown
{% math() %}
E = mc^2
{% end %}
```

**Inline Math:**
Use dollar signs for inline math: `$E = mc^2$`

**Examples:**
```markdown
Sum formula:
{% math() %}
\sum_{i=1}^{n} i = \frac{n(n+1)}{2}
{% end %}

Quadratic formula: $x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$

Matrix:
{% math() %}
\begin{bmatrix}
a & b \\
c & d
\end{bmatrix}
{% end %}
```

The math rendering is powered by [KaTeX](https://katex.org/), supporting a wide range of LaTeX mathematical notation.

### Mermaid Shortcode

Include diagrams using Mermaid syntax:

```markdown
{% mermaid() %}
graph TD
    A[Start] --> B[Process]
    B --> C[End]
{% end %}
```

## Search Functionality

The search functionality uses:
- **Fuse.js** for fuzzy search
- **Zola's built-in search index** for content
- **Modal-based search interface** with keyboard navigation
- **Keyboard shortcuts** for quick access

### Search Features:
- Full-text search across all content
- Fuzzy matching for typos
- Keyboard navigation (↑/↓ arrows, Enter to select)
- `Cmd/Ctrl + K` to open search modal
- `Escape` to close search

## Table of Contents

The Table of Contents is automatically generated from article headings:
- Smooth scrolling to sections
- Active section highlighting
- Mobile-responsive with collapsible sidebar
- Nested heading support (h1-h6)

## Customization

### Colors and Styling

The theme uses SASS with custom color variables:

```scss
$bg-primary: rgb(20, 20, 20);     // Main background
$bg-secondary: rgb(28, 28, 28);   // Cards and surfaces  
$bg-tertiary: rgb(36, 36, 36);    // Input fields and deeper surfaces
$text-primary: #f3f4f6;           // Main text color
$text-muted: #9ca3af;             // Light gray for TOC
$accent-blue: #60a5fa;            // Blue accent color
```

### Table of Contents Styling

The TOC uses a sophisticated highlighting system:
- **Default state**: Light gray (`#6b7280`) text
- **Active section**: Near-white (`#f9fafb`) text with blue accent border
- **Hover state**: Subtle background highlight with smooth transitions

### Typography

The theme uses system fonts for optimal performance:
```css
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', ...
```

## Deployment

### GitHub Pages

1. Build the site: `zola build`
2. Deploy the `public/` directory to GitHub Pages

### Netlify

1. Connect your repository to Netlify
2. Set build command: `zola build`
3. Set publish directory: `public`

### Custom Server

1. Build the site: `zola build`
2. Upload the `public/` directory to your server

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test locally with `zola serve`
5. Submit a pull request

## License

MIT License - feel free to use this theme for your own projects!

## Credits

- **Zola** - Static site generator
- **Tailwind CSS** - CSS framework
- **Fuse.js** - Fuzzy search library
- **Grokipedia** - Design inspiration
