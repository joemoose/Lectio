# Lectio - A Bear Theme

A legibility-focused, accessibility-conscious CSS theme for the [Bearblog.dev](https://bearblog.dev) blogging platform. 

---

## Design Goals

- **Editorial typography** — Georgia body text paired with DM Sans for headings and UI chrome. Designed for screen legibility, Georgia pairs well with DM Sans to give posts a composed, readable feel without importing multiple web fonts.
- **Contrast compliance** — Both light and dark palettes meet WCAG AA contrast ratios. The light-mode background is a warm off-white (`#fafaf8`) rather than pure white, reducing eye fatigue during long reading sessions.
- **Accessibility** — Keyboard navigation focus indicators (`focus-visible`), a skip navigation link, and motion are scoped behind `prefers-reduced-motion`.
- **Automatic dark mode** — The dark palette activates via `prefers-color-scheme: dark` without JavaScript.
- **Minimal footprint** — One Google Font import (DM Sans, variable weight). Everything else uses system fonts or established web-safe fallbacks.

---

## Preview

Example page: [Lectio Stylesheet Demo](https://joemoose.github.io/lectio/demo.html)

---

## Installation

Open **Lectio.css** and copy the contents into the "Edit theme CSS" text box in the Bearblog Themes page. Click Publish.

That's it. The theme takes effect immediately.

---

## Customization

All theme-level values are defined as CSS custom properties in the `:root` block at the top of the file. The most useful options:

| Variable | Default | Purpose |
|---|---|---|
| `--width` | `720px` | Maximum content column width |
| `--font-main` | DM Sans, system fallbacks | Headings, nav, UI chrome |
| `--font-secondary` | Georgia, serif fallback | Body copy |
| `--font-scale` | `1.08em` | Base font size (~17.3px) |
| `--link-color` | `#2b6cb0` | Link and focus indicator color |
| `--background-color` | `#fafaf8` | Page background (light mode) |

To swap the heading font, change `--font-main` and update the `@import` at the top of the file if using a different Google Font. To use only system fonts and eliminate the Google Fonts import entirely, set:

```css
--font-main: 'Segoe UI', system-ui, -apple-system, sans-serif;
```

and remove the `@import` line.

---

## The `.aside` Class

This theme adds an `.aside` utility class that looks like `blockquote` but is semantically distinct. It's intended for asides or notes rather than quotations from external sources. Using blockquotes for non-quotations can create accessibility issues.

Use it in BearBlog Markdown via inline HTML:

```html
<div class="aside">
  This is an aside, a personal reflection or editorial note, not a quotation.
</div>
```

---

## Skip Navigation Link

The `.skip-link` class is included for WCAG 2.4.1 compliance. It is visually hidden until focused by keyboard (Tab key), then appears as a styled banner in the top-left corner.

BearBlog does not inject this link automatically. Add this to your header:

```html
<a class="skip-link" href="#main-content">Skip to main content</a>
```

---

## Known Platform Limitations

Lectio addresses everything addressable through CSS. Several accessibility gaps in BearBlog's default output are template-level issues that require changes to the platform itself:

- Duplicate `<h1>` tags (site title and post title both use `h1`)
- No `<article>` wrapper around post content
- `<nav>` links wrapped in a `<p>` tag
- The upvote widget uses a DOM property rather than `setAttribute` for its aria label

These have been reported to the BearBlog developer.

---

## License

MIT — use freely, modify as needed, no attribution required (though appreciated).
