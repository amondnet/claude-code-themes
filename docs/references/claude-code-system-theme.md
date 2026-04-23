# Claude Code System Theme Reference

Extracted color-slot definitions and built-in palettes from Claude Code's internal `theme.ts`. Use as a reference when authoring custom theme JSON (`themes/*.json`) — this document lists every key available in `overrides` and dumps the full base palettes that `base: "dark" | "light"` (etc.) provide.

## Theme identifiers

- `THEME_NAMES`: `dark`, `light`, `light-daltonized`, `dark-daltonized`, `light-ansi`, `dark-ansi`
- `THEME_SETTINGS`: `auto` + the six names above. `auto` follows the system light/dark mode and is resolved at runtime.

## Color slot definitions

All slots take a CSS-like string: `rgb(r,g,b)` or `ansi:<name>`. Custom plugin themes may also use `#RRGGBB` hex.

### Core UI
| Slot | Purpose |
| --- | --- |
| `text` | Default foreground text |
| `inverseText` | Inverse foreground (on colored backgrounds) |
| `inactive` | Inactive/disabled elements |
| `inactiveShimmer` | Shimmer (lighter) variant of `inactive` |
| `subtle` | Muted secondary text |
| `background` | Primary accent background (typically a cyan) |
| `suggestion` | Suggestion text color |
| `remember` | Memory/remember indicator |
| `merged` | Merge state (usually matches `autoAccept`) |

### Mode & status
| Slot | Purpose |
| --- | --- |
| `claude` | Claude brand orange |
| `claudeShimmer` | Shimmer of `claude` |
| `claudeBlue_FOR_SYSTEM_SPINNER` | Blue used by the system spinner |
| `claudeBlueShimmer_FOR_SYSTEM_SPINNER` | Shimmer of the above |
| `permission` | Permission request UI |
| `permissionShimmer` | Shimmer of `permission` |
| `planMode` | Plan mode indicator |
| `ide` | IDE integration indicator |
| `autoAccept` | Auto-accept state (electric violet family) |
| `fastMode` | Fast mode indicator |
| `fastModeShimmer` | Shimmer of `fastMode` |

### Borders & backgrounds
| Slot | Purpose |
| --- | --- |
| `promptBorder` | Prompt border |
| `promptBorderShimmer` | Shimmer of prompt border |
| `bashBorder` | Bash block border |
| `userMessageBackground` | User message background |
| `userMessageBackgroundHover` | Hover background for user messages |
| `messageActionsBackground` | Message-actions selection bg (cool gray shifted toward `suggestion`) |
| `selectionBg` | Text selection bg (replaces cell bg, keeps fg) |
| `bashMessageBackgroundColor` | Bash message background |
| `memoryBackgroundColor` | Memory block background |
| `clawd_body` | Clawd (TUI v2) body |
| `clawd_background` | Clawd background |

### Semantic
| Slot | Purpose |
| --- | --- |
| `success` | Success (green family) |
| `error` | Error (red family) |
| `warning` | Warning (amber family) |
| `warningShimmer` | Shimmer of `warning` |

### Diff
| Slot | Purpose |
| --- | --- |
| `diffAdded` | Added-line background |
| `diffRemoved` | Removed-line background |
| `diffAddedDimmed` | Dimmed variant of added |
| `diffRemovedDimmed` | Dimmed variant of removed |
| `diffAddedWord` | Word-level added highlight |
| `diffRemovedWord` | Word-level removed highlight |

### Subagents only (`*_FOR_SUBAGENTS_ONLY`)
`red`, `blue`, `green`, `yellow`, `purple`, `orange`, `pink`, `cyan` — reserved for distinguishing subagents. Do not reuse in general UI.

### Miscellaneous
| Slot | Purpose |
| --- | --- |
| `professionalBlue` | Grove palette |
| `chromeYellow` | Chrome integration |
| `briefLabelYou` | Brief-mode "You" label |
| `briefLabelClaude` | Brief-mode "Claude" label |
| `rate_limit_fill` | Rate-limit progress bar fill |
| `rate_limit_empty` | Rate-limit progress bar empty |

### Rainbow (ultrathink keyword highlight)
`rainbow_red`, `rainbow_orange`, `rainbow_yellow`, `rainbow_green`, `rainbow_blue`, `rainbow_indigo`, `rainbow_violet` — each with a `_shimmer` counterpart.

---

## Full palette dump

### `dark`

```
autoAccept                              rgb(175,135,255)   electric violet
bashBorder                              rgb(253,93,177)    bright pink
claude                                  rgb(215,119,87)    Claude orange
claudeShimmer                           rgb(235,159,127)
claudeBlue_FOR_SYSTEM_SPINNER           rgb(147,165,255)
claudeBlueShimmer_FOR_SYSTEM_SPINNER    rgb(177,195,255)
permission                              rgb(177,185,249)   light blue-purple
permissionShimmer                       rgb(207,215,255)
planMode                                rgb(72,150,140)    muted sage green
ide                                     rgb(71,130,200)
promptBorder                            rgb(136,136,136)
promptBorderShimmer                     rgb(166,166,166)
text                                    rgb(255,255,255)
inverseText                             rgb(0,0,0)
inactive                                rgb(153,153,153)
inactiveShimmer                         rgb(193,193,193)
subtle                                  rgb(80,80,80)
suggestion                              rgb(177,185,249)
remember                                rgb(177,185,249)
background                              rgb(0,204,204)     bright cyan
success                                 rgb(78,186,101)
error                                   rgb(255,107,128)
warning                                 rgb(255,193,7)
merged                                  rgb(175,135,255)
warningShimmer                          rgb(255,223,57)
diffAdded                               rgb(34,92,43)
diffRemoved                             rgb(122,41,54)
diffAddedDimmed                         rgb(71,88,74)
diffRemovedDimmed                       rgb(105,72,77)
diffAddedWord                           rgb(56,166,96)
diffRemovedWord                         rgb(179,89,107)
red_FOR_SUBAGENTS_ONLY                  rgb(220,38,38)
blue_FOR_SUBAGENTS_ONLY                 rgb(37,99,235)
green_FOR_SUBAGENTS_ONLY                rgb(22,163,74)
yellow_FOR_SUBAGENTS_ONLY               rgb(202,138,4)
purple_FOR_SUBAGENTS_ONLY               rgb(147,51,234)
orange_FOR_SUBAGENTS_ONLY               rgb(234,88,12)
pink_FOR_SUBAGENTS_ONLY                 rgb(219,39,119)
cyan_FOR_SUBAGENTS_ONLY                 rgb(8,145,178)
professionalBlue                        rgb(106,155,204)
chromeYellow                            rgb(251,188,4)
clawd_body                              rgb(215,119,87)
clawd_background                        rgb(0,0,0)
userMessageBackground                   rgb(55,55,55)
userMessageBackgroundHover              rgb(70,70,70)
messageActionsBackground                rgb(44,50,62)
selectionBg                             rgb(38,79,120)     VS Code dark default
bashMessageBackgroundColor              rgb(65,60,65)
memoryBackgroundColor                   rgb(55,65,70)
rate_limit_fill                         rgb(177,185,249)
rate_limit_empty                        rgb(80,83,112)
fastMode                                rgb(255,120,20)
fastModeShimmer                         rgb(255,165,70)
briefLabelYou                           rgb(122,180,232)
briefLabelClaude                        rgb(215,119,87)
rainbow_red                             rgb(235,95,87)
rainbow_orange                          rgb(245,139,87)
rainbow_yellow                          rgb(250,195,95)
rainbow_green                           rgb(145,200,130)
rainbow_blue                            rgb(130,170,220)
rainbow_indigo                          rgb(155,130,200)
rainbow_violet                          rgb(200,130,180)
rainbow_red_shimmer                     rgb(250,155,147)
rainbow_orange_shimmer                  rgb(255,185,137)
rainbow_yellow_shimmer                  rgb(255,225,155)
rainbow_green_shimmer                   rgb(185,230,180)
rainbow_blue_shimmer                    rgb(180,205,240)
rainbow_indigo_shimmer                  rgb(195,180,230)
rainbow_violet_shimmer                  rgb(230,180,210)
```

### `light`

```
autoAccept                              rgb(135,0,255)     electric violet
bashBorder                              rgb(255,0,135)     vibrant pink
claude                                  rgb(215,119,87)    Claude orange
claudeShimmer                           rgb(245,149,117)
claudeBlue_FOR_SYSTEM_SPINNER           rgb(87,105,247)
claudeBlueShimmer_FOR_SYSTEM_SPINNER    rgb(117,135,255)
permission                              rgb(87,105,247)    medium blue
permissionShimmer                       rgb(137,155,255)
planMode                                rgb(0,102,102)     muted teal
ide                                     rgb(71,130,200)
promptBorder                            rgb(153,153,153)
promptBorderShimmer                     rgb(183,183,183)
text                                    rgb(0,0,0)
inverseText                             rgb(255,255,255)
inactive                                rgb(102,102,102)
inactiveShimmer                         rgb(142,142,142)
subtle                                  rgb(175,175,175)
suggestion                              rgb(87,105,247)
remember                                rgb(0,0,255)
background                              rgb(0,153,153)     cyan
success                                 rgb(44,122,57)
error                                   rgb(171,43,63)
warning                                 rgb(150,108,30)
merged                                  rgb(135,0,255)
warningShimmer                          rgb(200,158,80)
diffAdded                               rgb(105,219,124)
diffRemoved                             rgb(255,168,180)
diffAddedDimmed                         rgb(199,225,203)
diffRemovedDimmed                       rgb(253,210,216)
diffAddedWord                           rgb(47,157,68)
diffRemovedWord                         rgb(209,69,75)
red_FOR_SUBAGENTS_ONLY                  rgb(220,38,38)
blue_FOR_SUBAGENTS_ONLY                 rgb(37,99,235)
green_FOR_SUBAGENTS_ONLY                rgb(22,163,74)
yellow_FOR_SUBAGENTS_ONLY               rgb(202,138,4)
purple_FOR_SUBAGENTS_ONLY               rgb(147,51,234)
orange_FOR_SUBAGENTS_ONLY               rgb(234,88,12)
pink_FOR_SUBAGENTS_ONLY                 rgb(219,39,119)
cyan_FOR_SUBAGENTS_ONLY                 rgb(8,145,178)
professionalBlue                        rgb(106,155,204)
chromeYellow                            rgb(251,188,4)
clawd_body                              rgb(215,119,87)
clawd_background                        rgb(0,0,0)
userMessageBackground                   rgb(240,240,240)
userMessageBackgroundHover              rgb(252,252,252)
messageActionsBackground                rgb(232,236,244)
selectionBg                             rgb(180,213,255)   macOS / VS Code light
bashMessageBackgroundColor              rgb(250,245,250)
memoryBackgroundColor                   rgb(230,245,250)
rate_limit_fill                         rgb(87,105,247)
rate_limit_empty                        rgb(39,47,111)
fastMode                                rgb(255,106,0)
fastModeShimmer                         rgb(255,150,50)
briefLabelYou                           rgb(37,99,235)
briefLabelClaude                        rgb(215,119,87)
rainbow_red                             rgb(235,95,87)
rainbow_orange                          rgb(245,139,87)
rainbow_yellow                          rgb(250,195,95)
rainbow_green                           rgb(145,200,130)
rainbow_blue                            rgb(130,170,220)
rainbow_indigo                          rgb(155,130,200)
rainbow_violet                          rgb(200,130,180)
rainbow_red_shimmer                     rgb(250,155,147)
rainbow_orange_shimmer                  rgb(255,185,137)
rainbow_yellow_shimmer                  rgb(255,225,155)
rainbow_green_shimmer                   rgb(185,230,180)
rainbow_blue_shimmer                    rgb(180,205,240)
rainbow_indigo_shimmer                  rgb(195,180,230)
rainbow_violet_shimmer                  rgb(230,180,210)
```

### `light-daltonized`

Color-blind friendly light theme. Success shifts to blue; warning/claude use deuteranopia-adjusted oranges.

```
autoAccept                              rgb(135,0,255)
bashBorder                              rgb(0,102,204)     blue instead of pink
claude                                  rgb(255,153,51)    deuteranopia-adjusted orange
claudeShimmer                           rgb(255,183,101)
claudeBlue_FOR_SYSTEM_SPINNER           rgb(51,102,255)
claudeBlueShimmer_FOR_SYSTEM_SPINNER    rgb(101,152,255)
permission                              rgb(51,102,255)
permissionShimmer                       rgb(101,152,255)
planMode                                rgb(51,102,102)    muted blue-gray
ide                                     rgb(71,130,200)
promptBorder                            rgb(153,153,153)
promptBorderShimmer                     rgb(183,183,183)
text                                    rgb(0,0,0)
inverseText                             rgb(255,255,255)
inactive                                rgb(102,102,102)
inactiveShimmer                         rgb(142,142,142)
subtle                                  rgb(175,175,175)
suggestion                              rgb(51,102,255)
remember                                rgb(51,102,255)
background                              rgb(0,153,153)
success                                 rgb(0,102,153)     blue instead of green
error                                   rgb(204,0,0)
warning                                 rgb(255,153,0)
merged                                  rgb(135,0,255)
warningShimmer                          rgb(255,183,50)
diffAdded                               rgb(153,204,255)   light blue instead of green
diffRemoved                             rgb(255,204,204)
diffAddedDimmed                         rgb(209,231,253)
diffRemovedDimmed                       rgb(255,233,233)
diffAddedWord                           rgb(51,102,204)
diffRemovedWord                         rgb(153,51,51)
red_FOR_SUBAGENTS_ONLY                  rgb(204,0,0)
blue_FOR_SUBAGENTS_ONLY                 rgb(0,102,204)
green_FOR_SUBAGENTS_ONLY                rgb(0,204,0)
yellow_FOR_SUBAGENTS_ONLY               rgb(255,204,0)
purple_FOR_SUBAGENTS_ONLY               rgb(128,0,128)
orange_FOR_SUBAGENTS_ONLY               rgb(255,128,0)
pink_FOR_SUBAGENTS_ONLY                 rgb(255,102,178)
cyan_FOR_SUBAGENTS_ONLY                 rgb(0,178,178)
professionalBlue                        rgb(106,155,204)
chromeYellow                            rgb(251,188,4)
clawd_body                              rgb(215,119,87)
clawd_background                        rgb(0,0,0)
userMessageBackground                   rgb(220,220,220)
userMessageBackgroundHover              rgb(232,232,232)
messageActionsBackground                rgb(210,216,226)
selectionBg                             rgb(180,213,255)
bashMessageBackgroundColor              rgb(250,245,250)
memoryBackgroundColor                   rgb(230,245,250)
rate_limit_fill                         rgb(51,102,255)
rate_limit_empty                        rgb(23,46,114)
fastMode                                rgb(255,106,0)
fastModeShimmer                         rgb(255,150,50)
briefLabelYou                           rgb(37,99,235)
briefLabelClaude                        rgb(255,153,51)
rainbow_red                             rgb(235,95,87)
rainbow_orange                          rgb(245,139,87)
rainbow_yellow                          rgb(250,195,95)
rainbow_green                           rgb(145,200,130)
rainbow_blue                            rgb(130,170,220)
rainbow_indigo                          rgb(155,130,200)
rainbow_violet                          rgb(200,130,180)
rainbow_red_shimmer                     rgb(250,155,147)
rainbow_orange_shimmer                  rgb(255,185,137)
rainbow_yellow_shimmer                  rgb(255,225,155)
rainbow_green_shimmer                   rgb(185,230,180)
rainbow_blue_shimmer                    rgb(180,205,240)
rainbow_indigo_shimmer                  rgb(195,180,230)
rainbow_violet_shimmer                  rgb(230,180,210)
```

### `dark-daltonized`

Color-blind friendly dark theme. Same shifts as light-daltonized, tuned for dark backgrounds.

```
autoAccept                              rgb(175,135,255)
bashBorder                              rgb(51,153,255)    bright blue
claude                                  rgb(255,153,51)
claudeShimmer                           rgb(255,183,101)
claudeBlue_FOR_SYSTEM_SPINNER           rgb(153,204,255)
claudeBlueShimmer_FOR_SYSTEM_SPINNER    rgb(183,224,255)
permission                              rgb(153,204,255)
permissionShimmer                       rgb(183,224,255)
planMode                                rgb(102,153,153)
ide                                     rgb(71,130,200)
promptBorder                            rgb(136,136,136)
promptBorderShimmer                     rgb(166,166,166)
text                                    rgb(255,255,255)
inverseText                             rgb(0,0,0)
inactive                                rgb(153,153,153)
inactiveShimmer                         rgb(193,193,193)
subtle                                  rgb(80,80,80)
suggestion                              rgb(153,204,255)
remember                                rgb(153,204,255)
background                              rgb(0,204,204)
success                                 rgb(51,153,255)    blue instead of green
error                                   rgb(255,102,102)
warning                                 rgb(255,204,0)
merged                                  rgb(175,135,255)
warningShimmer                          rgb(255,234,50)
diffAdded                               rgb(0,68,102)
diffRemoved                             rgb(102,0,0)
diffAddedDimmed                         rgb(62,81,91)
diffRemovedDimmed                       rgb(62,44,44)
diffAddedWord                           rgb(0,119,179)
diffRemovedWord                         rgb(179,0,0)
red_FOR_SUBAGENTS_ONLY                  rgb(255,102,102)
blue_FOR_SUBAGENTS_ONLY                 rgb(102,178,255)
green_FOR_SUBAGENTS_ONLY                rgb(102,255,102)
yellow_FOR_SUBAGENTS_ONLY               rgb(255,255,102)
purple_FOR_SUBAGENTS_ONLY               rgb(178,102,255)
orange_FOR_SUBAGENTS_ONLY               rgb(255,178,102)
pink_FOR_SUBAGENTS_ONLY                 rgb(255,153,204)
cyan_FOR_SUBAGENTS_ONLY                 rgb(102,204,204)
professionalBlue                        rgb(106,155,204)
chromeYellow                            rgb(251,188,4)
clawd_body                              rgb(215,119,87)
clawd_background                        rgb(0,0,0)
userMessageBackground                   rgb(55,55,55)
userMessageBackgroundHover              rgb(70,70,70)
messageActionsBackground                rgb(44,50,62)
selectionBg                             rgb(38,79,120)
bashMessageBackgroundColor              rgb(65,60,65)
memoryBackgroundColor                   rgb(55,65,70)
rate_limit_fill                         rgb(153,204,255)
rate_limit_empty                        rgb(69,92,115)
fastMode                                rgb(255,120,20)
fastModeShimmer                         rgb(255,165,70)
briefLabelYou                           rgb(122,180,232)
briefLabelClaude                        rgb(255,153,51)
rainbow_red                             rgb(235,95,87)
rainbow_orange                          rgb(245,139,87)
rainbow_yellow                          rgb(250,195,95)
rainbow_green                           rgb(145,200,130)
rainbow_blue                            rgb(130,170,220)
rainbow_indigo                          rgb(155,130,200)
rainbow_violet                          rgb(200,130,180)
rainbow_red_shimmer                     rgb(250,155,147)
rainbow_orange_shimmer                  rgb(255,185,137)
rainbow_yellow_shimmer                  rgb(255,225,155)
rainbow_green_shimmer                   rgb(185,230,180)
rainbow_blue_shimmer                    rgb(180,205,240)
rainbow_indigo_shimmer                  rgb(195,180,230)
rainbow_violet_shimmer                  rgb(230,180,210)
```

### `light-ansi`

Uses only the 16 standard ANSI named colors. For terminals without true-color support.

```
autoAccept                              ansi:magenta
bashBorder                              ansi:magenta
claude                                  ansi:redBright
claudeShimmer                           ansi:yellowBright
claudeBlue_FOR_SYSTEM_SPINNER           ansi:blue
claudeBlueShimmer_FOR_SYSTEM_SPINNER    ansi:blueBright
permission                              ansi:blue
permissionShimmer                       ansi:blueBright
planMode                                ansi:cyan
ide                                     ansi:blueBright
promptBorder                            ansi:white
promptBorderShimmer                     ansi:whiteBright
text                                    ansi:black
inverseText                             ansi:white
inactive                                ansi:blackBright
inactiveShimmer                         ansi:white
subtle                                  ansi:blackBright
suggestion                              ansi:blue
remember                                ansi:blue
background                              ansi:cyan
success                                 ansi:green
error                                   ansi:red
warning                                 ansi:yellow
merged                                  ansi:magenta
warningShimmer                          ansi:yellowBright
diffAdded                               ansi:green
diffRemoved                             ansi:red
diffAddedDimmed                         ansi:green
diffRemovedDimmed                       ansi:red
diffAddedWord                           ansi:greenBright
diffRemovedWord                         ansi:redBright
red_FOR_SUBAGENTS_ONLY                  ansi:red
blue_FOR_SUBAGENTS_ONLY                 ansi:blue
green_FOR_SUBAGENTS_ONLY                ansi:green
yellow_FOR_SUBAGENTS_ONLY               ansi:yellow
purple_FOR_SUBAGENTS_ONLY               ansi:magenta
orange_FOR_SUBAGENTS_ONLY               ansi:redBright
pink_FOR_SUBAGENTS_ONLY                 ansi:magentaBright
cyan_FOR_SUBAGENTS_ONLY                 ansi:cyan
professionalBlue                        ansi:blueBright
chromeYellow                            ansi:yellow
clawd_body                              ansi:redBright
clawd_background                        ansi:black
userMessageBackground                   ansi:white
userMessageBackgroundHover              ansi:whiteBright
messageActionsBackground                ansi:white
selectionBg                             ansi:cyan
bashMessageBackgroundColor              ansi:whiteBright
memoryBackgroundColor                   ansi:white
rate_limit_fill                         ansi:yellow
rate_limit_empty                        ansi:black
fastMode                                ansi:red
fastModeShimmer                         ansi:redBright
briefLabelYou                           ansi:blue
briefLabelClaude                        ansi:redBright
rainbow_red                             ansi:red
rainbow_orange                          ansi:redBright
rainbow_yellow                          ansi:yellow
rainbow_green                           ansi:green
rainbow_blue                            ansi:cyan
rainbow_indigo                          ansi:blue
rainbow_violet                          ansi:magenta
rainbow_red_shimmer                     ansi:redBright
rainbow_orange_shimmer                  ansi:yellow
rainbow_yellow_shimmer                  ansi:yellowBright
rainbow_green_shimmer                   ansi:greenBright
rainbow_blue_shimmer                    ansi:cyanBright
rainbow_indigo_shimmer                  ansi:blueBright
rainbow_violet_shimmer                  ansi:magentaBright
```

### `dark-ansi`

```
autoAccept                              ansi:magentaBright
bashBorder                              ansi:magentaBright
claude                                  ansi:redBright
claudeShimmer                           ansi:yellowBright
claudeBlue_FOR_SYSTEM_SPINNER           ansi:blueBright
claudeBlueShimmer_FOR_SYSTEM_SPINNER    ansi:blueBright
permission                              ansi:blueBright
permissionShimmer                       ansi:blueBright
planMode                                ansi:cyanBright
ide                                     ansi:blue
promptBorder                            ansi:white
promptBorderShimmer                     ansi:whiteBright
text                                    ansi:whiteBright
inverseText                             ansi:black
inactive                                ansi:white
inactiveShimmer                         ansi:whiteBright
subtle                                  ansi:white
suggestion                              ansi:blueBright
remember                                ansi:blueBright
background                              ansi:cyanBright
success                                 ansi:greenBright
error                                   ansi:redBright
warning                                 ansi:yellowBright
merged                                  ansi:magentaBright
warningShimmer                          ansi:yellowBright
diffAdded                               ansi:green
diffRemoved                             ansi:red
diffAddedDimmed                         ansi:green
diffRemovedDimmed                       ansi:red
diffAddedWord                           ansi:greenBright
diffRemovedWord                         ansi:redBright
red_FOR_SUBAGENTS_ONLY                  ansi:redBright
blue_FOR_SUBAGENTS_ONLY                 ansi:blueBright
green_FOR_SUBAGENTS_ONLY                ansi:greenBright
yellow_FOR_SUBAGENTS_ONLY               ansi:yellowBright
purple_FOR_SUBAGENTS_ONLY               ansi:magentaBright
orange_FOR_SUBAGENTS_ONLY               ansi:redBright
pink_FOR_SUBAGENTS_ONLY                 ansi:magentaBright
cyan_FOR_SUBAGENTS_ONLY                 ansi:cyanBright
professionalBlue                        rgb(106,155,204)   (literal — not an ANSI name)
chromeYellow                            ansi:yellowBright
clawd_body                              ansi:redBright
clawd_background                        ansi:black
userMessageBackground                   ansi:blackBright
userMessageBackgroundHover              ansi:white
messageActionsBackground                ansi:blackBright
selectionBg                             ansi:blue
bashMessageBackgroundColor              ansi:black
memoryBackgroundColor                   ansi:blackBright
rate_limit_fill                         ansi:yellow
rate_limit_empty                        ansi:white
fastMode                                ansi:redBright
fastModeShimmer                         ansi:redBright
briefLabelYou                           ansi:blueBright
briefLabelClaude                        ansi:redBright
rainbow_red                             ansi:red
rainbow_orange                          ansi:redBright
rainbow_yellow                          ansi:yellow
rainbow_green                           ansi:green
rainbow_blue                            ansi:cyan
rainbow_indigo                          ansi:blue
rainbow_violet                          ansi:magenta
rainbow_red_shimmer                     ansi:redBright
rainbow_orange_shimmer                  ansi:yellow
rainbow_yellow_shimmer                  ansi:yellowBright
rainbow_green_shimmer                   ansi:greenBright
rainbow_blue_shimmer                    ansi:cyanBright
rainbow_indigo_shimmer                  ansi:blueBright
rainbow_violet_shimmer                  ansi:magentaBright
```

---

## Design notes

- **Shimmer variants** are lighter tints of the base hue, alternated with the base during loading/spinner animations.
- **`selectionBg`** replaces the cell background while preserving foreground colors (not SGR-7 inverse). Ensure sufficient contrast against expected fg colors — light palettes use soft blue, dark palettes use deep blue.
- **`userMessageBackgroundHover`** in the light theme is set to `≥250` so it quantizes to a distinct value from the base at 256-color depth.
- **`messageActionsBackground`** is a cool gray slightly shifted toward `suggestion` blue — visually distinct from both the default background and `userMessageBackground`.
- **Apple Terminal** handles 24-bit color escape sequences poorly, so the runtime downgrades to 256-color (`chalk` level 2) when `TERM_PROGRAM === "Apple_Terminal"`.
- **ANSI themes** are rarely used by custom plugin themes (which typically only declare `base: "dark"` or `base: "light"`), but are still the fallback for low-capability terminals.
- **Daltonized themes** replace greens with blues and shift oranges to deuteranopia-friendly tones — notably `success` becomes blue.

## Source

Extracted from Claude Code's internal `theme.ts` (v2.1.x). Original module also exports `Theme` type, `getTheme(themeName)`, and `themeColorToAnsi()` — omitted here since plugin theme authors only need the slot names and base palettes to author `overrides`.
