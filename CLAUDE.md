# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A content-only Claude Code plugin that ships a collection of color themes. There is no build system, no package manager, and no test runner — the artifacts are JSON files under `themes/`, plus two manifest files under `.claude-plugin/` that register them as a self-hosted plugin marketplace.

Requires Claude Code `2.1.118+` (the version that added theme-plugin support).

## Architecture

Three layers wire a theme file into Claude Code:

1. `.claude-plugin/marketplace.json` — declares this repo as a marketplace named `claude-code-themes` and lists the plugin(s) it exposes. Consumed by `/plugin marketplace add`.
2. `.claude-plugin/plugin.json` — the plugin manifest. Its `"themes": "./themes/"` field tells Claude Code where to scan for theme JSON when the plugin is installed.
3. `themes/<slug>.json` — individual theme definitions. Each is independent; there is no central registry or index file to update when adding a theme (the `themes` directory is scanned).

Themes compose over a built-in base palette rather than defining every color from scratch:

```
base palette  ──merge──▶  overrides  ═══▶  resolved theme
(dark/light/…)            (per-theme)
```

- `base` picks one of Claude Code's built-in palettes: `dark`, `light`, `dark-ansi`, `light-ansi`, `dark-daltonized`, `light-daltonized`.
- `overrides` is a flat map of color-token → value. Only keys you want to change need to appear; unknown keys are ignored silently.
- Color values accept `#rrggbb`/`#rgb`, `rgb(r,g,b)` (0–255), `ansi256(N)`, or `ansi:<name>`.

The full list of overridable tokens and the complete dump of each base palette live in `docs/references/claude-code-system-theme.md`. **Read this file before authoring or debugging a theme** — it is the source of truth for which keys exist and what they default to.

## Adding or editing a theme

1. Create or edit `themes/<slug>.json`. Use an existing theme (e.g. `themes/dracula.json`) as a template for which keys are typically overridden.
2. Preview in Claude Code: run `/theme` and select the theme. If the plugin is already installed via the marketplace, reinstall or restart Claude Code to pick up changes; during local development you can also copy the file into `~/.claude/themes/` to iterate without reinstalling.
3. Exercise the UI surfaces that actually use the overrides you changed — e.g. trigger a bash block to check `bashBorder`, open plan mode to check `planMode`, produce a diff to check the `diff*` family. Token-group semantics are documented in `docs/references/claude-code-system-theme.md`.
4. If the theme is new, add a row to the appropriate table in `README.md`. The marketplace/plugin manifests do **not** need a new entry per theme (the `themes/` directory is scanned).

## Conventions observed by existing themes

- Palette sourcing is upstream-faithful. Themes port colors from their named upstream project (Dracula, Nord, Catppuccin, etc.) — prefer the canonical hex values from the source palette rather than ad-hoc adjustments.
- `diffAdded`/`diffRemoved` use darkened/desaturated backgrounds, while `diffAddedWord`/`diffRemovedWord` use the vivid success/error hues. Keep this contrast pattern when porting new palettes.
- `*_FOR_SUBAGENTS_ONLY` keys exist to distinguish subagents — don't reuse those hues for general UI slots in the same theme.
- Dark themes set `base: "dark"`, light themes `base: "light"`. Don't override `background`/`text` toward the opposite end of the spectrum of the chosen base.

## Notes on tooling

There is no `npm install`, lint, or test command. JSON is the only source format, and validation happens when Claude Code loads the theme (invalid color strings are logged; unknown keys are ignored). When in doubt, validate a theme by loading it with `/theme`.
