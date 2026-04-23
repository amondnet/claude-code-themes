# claude-code-themes

Curated collection of popular editor-inspired color themes for [Claude Code](https://docs.claude.com/en/docs/claude-code) `2.1.118+`.

## Included themes

### Dark

| Slug | Name | Base |
| --- | --- | --- |
| `dracula` | Dracula | dark |
| `tokyo-night` | Tokyo Night | dark |
| `nord` | Nord | dark |
| `catppuccin-mocha` | Catppuccin Mocha | dark |
| `gruvbox-dark` | Gruvbox Dark | dark |
| `one-dark-pro` | One Dark Pro | dark |
| `rose-pine` | Rosé Pine | dark |

### Light

| Slug | Name | Base |
| --- | --- | --- |
| `solarized-light` | Solarized Light | light |
| `catppuccin-latte` | Catppuccin Latte | light |
| `github-light` | GitHub Light | light |

## Install

### Option 1 — as a Claude Code plugin (via marketplace)

This repo is a self-hosted plugin marketplace. Add it, then install the plugin:

```text
/plugin marketplace add amondnet/claude-code-themes
/plugin install claude-code-themes@claude-code-themes
```

Once installed, pick a theme with `/theme` and select e.g. `Dracula`.

### Option 2 — copy individual themes

If you only want one theme, copy its file into your personal themes directory:

```bash
cp themes/dracula.json ~/.claude/themes/
```

Then run `/theme` and choose it.

## Theme JSON schema

Each theme is a JSON file with this shape:

```json
{
  "name": "Theme Name",
  "base": "dark",
  "overrides": {
    "text": "#f8f8f2",
    "background": "#bd93f9"
  }
}
```

- `base` — one of `dark`, `light`, `dark-ansi`, `light-ansi`, `dark-daltonized`, `light-daltonized`. The `overrides` merge on top of this palette.
- `overrides` — map of color token to color value. Unknown keys are ignored.

### Color formats

Any of these are accepted per value:

- `#rrggbb` or `#rgb`
- `rgb(r, g, b)` (0–255 per channel)
- `ansi256(N)` (0–255)
- `ansi:<name>` where `<name>` is a standard ANSI color name

### Overridable color tokens

Grouped by role:

- **Core** — `text`, `inverseText`, `inactive`, `inactiveShimmer`, `subtle`, `background`
- **Brand** — `claude`, `claudeShimmer`, `claudeBlue_FOR_SYSTEM_SPINNER`, `claudeBlueShimmer_FOR_SYSTEM_SPINNER`, `clawd_body`, `clawd_background`
- **UI modes** — `permission`, `permissionShimmer`, `planMode`, `ide`, `autoAccept`, `suggestion`, `remember`, `merged`, `fastMode`, `fastModeShimmer`
- **Borders / surfaces** — `promptBorder`, `promptBorderShimmer`, `bashBorder`, `userMessageBackground`, `userMessageBackgroundHover`, `messageActionsBackground`, `bashMessageBackgroundColor`, `memoryBackgroundColor`, `selectionBg`
- **Status** — `success`, `error`, `warning`, `warningShimmer`
- **Diff** — `diffAdded`, `diffRemoved`, `diffAddedDimmed`, `diffRemovedDimmed`, `diffAddedWord`, `diffRemovedWord`
- **Subagents** — `red_FOR_SUBAGENTS_ONLY`, `blue_FOR_SUBAGENTS_ONLY`, `green_FOR_SUBAGENTS_ONLY`, `yellow_FOR_SUBAGENTS_ONLY`, `purple_FOR_SUBAGENTS_ONLY`, `orange_FOR_SUBAGENTS_ONLY`, `pink_FOR_SUBAGENTS_ONLY`, `cyan_FOR_SUBAGENTS_ONLY`
- **Rainbow** — `rainbow_red`, `rainbow_orange`, `rainbow_yellow`, `rainbow_green`, `rainbow_blue`, `rainbow_indigo`, `rainbow_violet` (and `*_shimmer` variants)
- **Rate limit** — `rate_limit_fill`, `rate_limit_empty`
- **Misc** — `professionalBlue`, `chromeYellow`, `briefLabelYou`, `briefLabelClaude`

## Adding a new theme

1. Create `themes/<slug>.json` with the shape above.
2. Open Claude Code, run `/theme`, and select your new theme to preview.
3. Open a PR.

## Credits

Palettes are inspired by / ported from their respective upstream projects:

- [Dracula](https://draculatheme.com/)
- [Tokyo Night](https://github.com/enkia/tokyo-night-vscode-theme)
- [Nord](https://www.nordtheme.com/)
- [Catppuccin](https://github.com/catppuccin/catppuccin)
- [Gruvbox](https://github.com/morhetz/gruvbox)
- [One Dark Pro](https://github.com/Binaryify/OneDark-Pro)
- [Rosé Pine](https://rosepinetheme.com/)
- [Solarized](https://ethanschoonover.com/solarized/)
- [GitHub Primer](https://primer.style/)

## License

MIT — see [LICENSE](LICENSE).
