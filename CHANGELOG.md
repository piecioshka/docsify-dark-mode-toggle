# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.1](https://github.com/piecioshka/docsify-dark-mode-toggle/compare/v1.0.0...v1.0.1) (2026-05-30)


### Fixed

* make sun icon hollow ([f224184](https://github.com/piecioshka/docsify-dark-mode-toggle/commit/f224184388091a533ae38c449dbd8877e6350785))

## [1.0.0] - 2026-05-28

### Added

- Initial public release.
- Floating dark mode toggle button with sun/moon SVG icons.
- Respects `prefers-color-scheme: dark` for first-visit default.
- Persists user choice in `localStorage` (key configurable via `$docsify.darkMode.storageKey`).
- Built-in English and Polish labels; merge or override via `$docsify.darkMode.messages`.
- Customizable icons via `$docsify.darkMode.sunIcon` / `moonIcon` (SVG string or `SVGElement`).
- CSS custom properties on `:root` and `html.dark-mode` for easy palette overrides.
