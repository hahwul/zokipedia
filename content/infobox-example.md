+++
title = "Infobox Example"
date = 2025-11-05
description = "Example page demonstrating the infobox shortcode feature"
tags = ["example", "shortcode", "documentation"]
+++

{% infobox(title="Example Topic", image="/static/images/example.png", image_caption="Example caption") %}
| Field | Value |
|-------|-------|
| **Type** | Example |
| **Date** | 2025 |
| **Author** | Test |
| **Status** | Active |

Additional information can be added here as markdown content.
{% end %}

# Infobox Example

This page demonstrates the new **infobox** shortcode that can be used to display structured information on the right side of the page, similar to Wikipedia's infoboxes.

## Features

The infobox shortcode supports:
- Title display
- Image with optional caption
- Tabular data
- Markdown content
- Responsive design (full-width on mobile)

## Usage

You can use the infobox shortcode in your content like this:

```markdown
{% raw %}
{% infobox(title="Your Title", image="/path/to/image.png", image_caption="Caption") %}
| Field | Value |
|-------|-------|
| **Name** | Example |
| **Type** | Demo |

Any markdown content here.
{% end %}
{% endraw %}
```

## Parameters

- `title` (optional): The title shown at the top of the infobox
- `image` (optional): Path to the image to display
- `image_alt` (optional): Alt text for the image (defaults to title)
- `image_caption` (optional): Caption text below the image

## Content

The body of the shortcode can contain:
- Tables (ideal for key-value pairs)
- Paragraphs
- Lists
- Links
- Bold and italic text

## Example without Image

{% infobox(title="Simple Infobox") %}
**Purpose**: Demonstrate a simple infobox without an image.

**Features**:
- Clean design
- Structured information
- Responsive layout
{% end %}

This is regular paragraph content that flows around the infobox. The infobox will float on the right side on desktop devices and display full-width on mobile devices for better readability.

## Multiple Infoboxes

{% infobox(title="Second Infobox") %}
| Property | Details |
|----------|---------|
| **Position** | Stacked |
| **Behavior** | Float right |
| **Clear** | Right |
{% end %}

You can use multiple infoboxes on the same page. Each will stack vertically on the right side of the content.

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris.

## Conclusion

The infobox shortcode provides a clean and effective way to present supplementary information alongside your main content, improving the overall structure and readability of your pages.
