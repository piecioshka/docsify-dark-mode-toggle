# Contributing to docsify-dark-mode-toggle

How the plugin is built and how to try changes locally. For installation and configuration, see the [README](README.md).

## Getting started

Prerequisites: Node.js version from `.nvmrc` (`lts/krypton`). The package declares `node >= 20`.

The plugin has no dependencies, no build step, no npm scripts and no tests. `index.js` and `index.css` are published as they are.

```bash
git clone https://github.com/piecioshka/docsify-dark-mode-toggle
cd docsify-dark-mode-toggle
```

## Project structure

```
index.js          - the plugin: reads window.$docsify.darkMode, creates or reuses the toggle button, stores the choice in localStorage
index.css         - button styles and CSS custom properties for the light and dark palettes
demo/index.html   - Docsify site that renders this README with the plugin loaded
```

Only `index.js`, `index.css` and `LICENSE` go into the npm package (the `files` field in `package.json`).

## Trying changes in the demo

`demo/index.html` loads Docsify from unpkg and the plugin from `../index.js` and `../index.css`, with `basePath: "../"` so it renders the repo's `README.md`. Docsify fetches Markdown over HTTP, so serve the repository root with any static HTTP server and open `/demo/` (opening the file directly from disk does not work). The demo config adds a German (`de`) label set to exercise the `messages` option.

## Releasing

Bump the version with `npm version <patch|minor|major>`, which creates the version commit (for example `1.0.2`) and the tag.

## Conventions

- Format with Prettier: `npx prettier --write .`.
- Commit messages follow Conventional Commits (`fix:`, `docs:`, `chore:`); release commits are the bare version number.
