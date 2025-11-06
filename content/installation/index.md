+++
title = "Installation and Configuration"
date = 2025-11-05
updated = 2025-11-05
description = ""
tags = []
+++

Zokipedia is a theme for Zola. To use this documentation, you need to install Zola first. You can install it on various operating systems with a simple command like the one below.

```bash
# macOS Example
brew install zola
```

For more details, please refer to the [official installation guide](https://www.getzola.org/documentation/getting-started/installation/) on the Zola website.

Once you have Zola installed, create a new Zola site as follows:

```bash
zola init your-docs
cd docs
```

You can then run the local development server with the `zola serve` command and view your site at `http://localhost:1111`.

## Install the zokipedia Theme

The easiest way to install a theme in Zola is to clone it or add it as a submodule into the `themes` subdirectory of your Zola project.

Clone example

```bash
git clone https://github.com/hahwul/zokipedia themes/zokipedia
```

Submodule example

```bash
git submodule add https://github.com/hahwul/zokipedia themes/zokipedia
```

## Update the zokipedia Theme

If you want to update the zokipedia theme to the latest version, you can do so easily:

- If you cloned the theme:
  ```bash
  cd themes/zokipedia
  git pull
  ```

- If you added the theme as a submodule:
  ```bash
  git submodule sync
  git submodule update --remote
  ```

This will ensure you always have the latest features and fixes from the zokipedia theme.

## Set the theme in config.toml

This is the final step. Set the theme in your `config.toml` file to use zokipedia. Below is a sample configuration with additional options you can customize:

```toml
base_url = "https://your-site.com"
title = "Your App"
description = "Your app description"
theme = "zokipedia"

# Whether to automatically compile all Sass files in the sass directory
compile_sass = true

# Whether to build a search index to be used later on by a JavaScript library
build_search_index = true

[markdown]
# Whether to do syntax highlighting
highlight_code = true

[search]
index_format = "fuse_javascript"

[extra]
# Navigation links - will appear in the header on the right side
nav_links = [
    { name = "Home", url = "/" },
    { name = "Docs", url = "/docs" },
]

# Navigation configuration
nav_height = 80  # Height of the top navigation in pixels (default: 64px)

# Footer configuration
[extra.footer]
links = [
    { text = "Contact", url = "/contact" }
]
copyright = "© Your Name. All rights reserved."
```

Now, when you run Zola, it will use the zokipedia theme.

```bash
zola serve
```

However, since you don't have any content yet, you will only see a blank page with a brilliant color. In the next document, we'll create our first page.
