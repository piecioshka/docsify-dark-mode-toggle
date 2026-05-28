# docsify-dark-mode-toggle

[![node version](https://img.shields.io/node/v/docsify-dark-mode-toggle.svg)](https://www.npmjs.com/package/docsify-dark-mode-toggle)
[![npm version](https://badge.fury.io/js/docsify-dark-mode-toggle.svg)](https://badge.fury.io/js/docsify-dark-mode-toggle)
[![downloads count](https://img.shields.io/npm/dt/docsify-dark-mode-toggle.svg)](https://www.npmjs.com/package/docsify-dark-mode-toggle)
[![size](https://packagephobia.com/badge?p=docsify-dark-mode-toggle)](https://packagephobia.com/result?p=docsify-dark-mode-toggle)
[![license](https://img.shields.io/npm/l/docsify-dark-mode-toggle.svg)](https://piecioshka.mit-license.org)

🔨 A small, zero-dependency dark mode toggle for [Docsify](https://docsify.js.org/).
Adds a floating button that switches the site between light and dark palettes,
respects `prefers-color-scheme`, and persists the user's choice in `localStorage`.

Works just as well in any plain HTML page — Docsify is not required.

## Installation

### Via CDN (recommended for Docsify sites)

Add **after** `docsify.min.js` in your `index.html`:

```html
<link
  rel="stylesheet"
  href="https://unpkg.com/docsify-dark-mode-toggle/index.css"
/>
<!-- ...your docsify config and script... -->
<script src="https://unpkg.com/docsify-dark-mode-toggle/index.js"></script>
```

Pin a version for reproducible builds:

```html
<link
  rel="stylesheet"
  href="https://unpkg.com/docsify-dark-mode-toggle@1.0.0/index.css"
/>
<script src="https://unpkg.com/docsify-dark-mode-toggle@1.0.0/index.js"></script>
```

[jsDelivr](https://www.jsdelivr.com/) works too:
`https://cdn.jsdelivr.net/npm/docsify-dark-mode-toggle@1.0.0/index.js`

### Via npm

```bash
npm install docsify-dark-mode-toggle
```

Then import the CSS and reference the JS however your bundler / setup expects.

## Usage

No configuration is required — drop the two tags in and a toggle button appears
in the top-left corner of the page.

The script adds the class `dark-mode` to `<html>` when dark mode is active, so
your custom CSS can target either `html.dark-mode` or any of the variables
defined in `index.css`.

## Configuration

All options are optional and read from `window.$docsify.darkMode`:

```html
<script>
  window.$docsify = {
    // ...your other docsify options...
    darkMode: {
      storageKey: "color-scheme", // localStorage key (default: "color-scheme")
      messages: {
        // merged with built-in en/pl
        de: {
          enable: "Dunkles Design aktivieren",
          disable: "Dunkles Design deaktivieren",
        },
      },
      sunIcon: "<svg ...>...</svg>", // optional SVG string (or SVGElement)
      moonIcon: "<svg ...>...</svg>",
    },
  };
</script>
```

| Option       | Type                                  | Default          | Description                                                                                                  |
| ------------ | ------------------------------------- | ---------------- | ------------------------------------------------------------------------------------------------------------ |
| `storageKey` | `string`                              | `"color-scheme"` | `localStorage` key under which the user's choice is stored (`"dark"` / `"light"`).                           |
| `messages`   | `Record<string, { enable, disable }>` | English + Polish | Per-locale labels for the button. Locale is taken from `<html lang>` (falling back to `navigator.language`). |
| `sunIcon`    | `string \| SVGElement`                | built-in sun     | Icon shown when dark mode is **active** (click switches to light).                                           |
| `moonIcon`   | `string \| SVGElement`                | built-in moon    | Icon shown when dark mode is **inactive** (click switches to dark).                                          |

## Styling

`index.css` ships with CSS custom properties on `:root` for layout and on
`html.dark-mode` for the dark palette. Override either after loading the
stylesheet:

```css
:root {
  --dm-toggle-top: 12px;
  --dm-toggle-left: auto;
  --dm-toggle-right: 16px;
}

html.dark-mode {
  --dm-bg: #001f3f;
  --dm-code-bg: #002b5c;
}
```

You can also place your own `<button class="dark-mode-toggle">` in the markup
— if one already exists, the script reuses it instead of creating a new one.

## How it works

- On first visit, the initial mode is taken from `prefers-color-scheme: dark`.
- The user's explicit choice is saved as `"dark"` or `"light"` under
  `storageKey` and wins over the system preference.
- The script reacts to `prefers-color-scheme` changes only while the user has
  not made an explicit choice.

## License

[The MIT License](https://piecioshka.mit-license.org) @ 2026
