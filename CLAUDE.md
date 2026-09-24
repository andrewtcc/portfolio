# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

A static personal portfolio site for Andrew Tsang. It is plain HTML/CSS with no build step, package manager, linter, or tests. Everything served lives under `html/`, which is the document root.

## Running locally

Serve the `html/` directory with any static server, for example:

```sh
python3 -m http.server 8000 --directory html
```

Then open http://localhost:8000. Opening `html/index.html` directly in a browser also works. The page loads Bootstrap, jQuery and Google Fonts from CDNs, so it needs network access to render correctly.

## Architecture

- **`html/index.html`**: the only page. It uses **Bootstrap 4.5.2** (CSS and JS from the StackPath CDN) and **jQuery 3.5.1 slim** (from code.jquery.com). Bootstrap 4 conventions apply, such as `ml-auto`, `card-deck` and `data-toggle`, so don't use Bootstrap 5 class names or `data-bs-*` attributes unless the whole page is migrated.
- **`html/styles/main.css`**: site-specific overrides loaded after Bootstrap. It includes:
  - A custom animated hamburger `.navbar-toggler` whose three `.line` spans take the place of Bootstrap's default icon. The CSS selects the top and bottom spans by the IDs `#topbar` and `#bottombar`.
  - The `.bx` box-shadow class.
- **Card hover behavior**: an inline `<script>` at the bottom of `index.html` adds `text-white bg-primary` to a card's `.card-header` on hover and adds `.bx` to the card. If you rename card markup or the `.bx` class, update the script and the CSS together.
- The nav links (Projects, Contact) are `href="#"` placeholders; those pages don't exist yet.
- `<meta name="robots" content="noindex,follow">` is set on purpose. Keep it unless asked to change it.
