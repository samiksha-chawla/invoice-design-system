# Mobile Guidelines — Petpooja Design System

**Source (canonical):** https://www.figma.com/design/BYjfyLF2DEQhdU1jszWt2g/Mobile-Guidelines
**Applies to:** native mobile apps (iOS, Android) and mobile-first surfaces where native patterns dominate.
**Inheritance:** this file **defines no local paint, text, effect styles or variables**. ALL tokens come from `base.md`. The Mobile Guidelines file owns only **components**.

> **Always read alongside `base.md`.** Tokens come from `base.md`; components come from §3 below; non-default variant anatomy is in §7. Anything outside those three is invented — refuse.

---

## 1. Token pointers (what to use from `base.md` for mobile work)

### 1.1 Colour roles → `base.md` tokens

Mobile uses the same colour vocabulary as web. The most common bindings:

| Role                                              | `base.md` token                                     |
| ------------------------------------------------- | --------------------------------------------------- |
| Screen background                                 | `Neutral/Background` `#F8F8F8` (`base.md §1.2`)     |
| Card / surface                                    | `Neutral/White` `#FFFFFF` (`base.md §1.2`)          |
| Subtle surface tint (header rows, sheet handles)  | `Brand/Light/100..200` (`base.md §1.1.2`)           |
| Primary text                                      | `Neutral/Text` `#192839` (`base.md §1.2`)           |
| Secondary text                                    | `Neutral/Content` `#40566D` (`base.md §1.2`)        |
| Tertiary / muted text                             | `Neutral/Sub Content` `#768EA7` (`base.md §1.2`)    |
| Disabled                                          | `Neutral/Disabled` `#D0D8E0` (`base.md §1.2`)       |
| Default border / divider                          | `Neutral/Stroke` `#D2D6DB` (`base.md §1.2`)         |
| Brand primary fill (CTAs, active nav, active chip) | `Brand/Primary` `#2E5391` (`base.md §1.1.1`)       |
| Brand hover / pressed fill                        | `Brand/Dark/600` `#254A88` (`base.md §1.1.3`)       |
| White text on brand surfaces / Top Nav modal text | `Brand/Gray/highContrast/700` `#FFFFFF` (`base.md §1.1.5`) |
| Status — error / warning / success / info wash    | `Error/BG`, `Warning/BG`, `Success/BG`, `Prediction/BG` (`base.md §1.3`) |
| Tooltip background                                | `Neutral/Text` `#192839` (`base.md §1.2`) *(dark fill — not `Neutral/Tooltip BG` here)* |

### 1.2 Typography → `base.md` text styles

Use the **`Mobile/*`** scale (`base.md §2.4`). Common pairings:

| Use                          | Text style                          |
| ---------------------------- | ----------------------------------- |
| Screen H1 / large displays   | `Mobile/Display/Small/Semibold..XLarge/Semibold` |
| Section title                | `Mobile/Heading/Large/Semibold`     |
| Card / list item title       | `Mobile/Heading/Small/Semibold`     |
| Body                         | `Mobile/Body/Medium/Regular`        |
| Body emphasised              | `Mobile/Body/Medium/Semibold`       |
| Form labels                  | `Mobile/Body/Small/Medium`          |
| Button label                 | `Mobile/Body/Small/Medium`          |
| Caption / fine print         | `Mobile/Caption/SmallRegular`       |

> **⚠️ Drift:** the Mobile Guidelines file's **Button** component is mis-bound to `Desktop/*` text styles (verified — `Desktop/Body/Small/Medium`, `Desktop/Body/Medium/Medium`, etc.). When implementing on mobile, **prefer the `Mobile/*` equivalent at the same size step**, and surface the divergence to design. Only the Button family carries this drift — Top Nav, Bottom Nav, Inputs etc. use `Mobile/*` correctly.
>
> **Never use `Desktop/*` text styles in net-new mobile designs.** If the request asks for a desktop look in a mobile design, surface the conflict.

### 1.3 Variables vs paint styles

Same rule as web: prefer the variable when both exist (e.g. `Brand/Primary/Primary`, `Neutral/Text`). Variables in `base.md §1` are canonical.

### 1.4 Mobile-only token usage rules

- **Status Bar / Home Indicator fill:** `Neutral/White` (`Background=True`) or transparent (`Background=False`). The system status icons / time / signal indicator are rendered by the OS, not the design.
- **Page-dim overlay (for bottom sheets / dialogs):** `Neutral/Text @ 50%` (= `#192839 @ 50%`).
- **Top Nav `Modal` variant** uses a **black** fill (`#000000`) — not a `base.md` token. Treat as an explicit override for modal headers only.

---

## 2. Effect styles (shadows)

The Mobile Guidelines file defines **no local effect styles**. The Bottom Navigation surfaces apply an imported library effect `Blur/Tabbar`, and inputs use `Shadow/xs` / `Focused Effect` / `Focused Error Effect` / `Input Box` / `Focused w/Error input Box` (all library tokens — same as web).

When implementing in code:
- `Blur/Tabbar` → backdrop-blur 20–30 px with a subtle translucent fill (matches iOS frosted tab bar).
- `Shadow/xs` → small subtle drop shadow (≈ web's `Pretty Shadows/96` lite).
- `Focused Effect` / `Focused Error Effect` → 2-3 px focus ring (blue / red).

> **Drift flag:** these effect tokens are inherited from an **external library** (not defined in `base.md` or in this file). The web file has 10 file-local `Pretty Shadows/*`; **the mobile file has none** — its surfaces rely on library effects. When unclear, ask.

---

## 3. Component catalog

The Mobile Guidelines file is organised one component family per Figma page. Below is the full inventory.

### 3.1 Buttons

**Sets:** 2 — `Button` (272 variants) and `Icon Button` (48 variants).

**Anatomy of `Button` default (`Size=Small, Type=Quaternary, State=Default`):** 90 × 32, layout `HORIZONTAL`, `pad [4, 14, 4, 14]`, `gap 0`, `radius 8`. Text style `Desktop/Body/Small/Medium` ⚠️ *(file bug — should use `Mobile/Body/Small/Medium`)*. Text fill `Brand/Gray/highContrast/700`.

**Anatomy of `Icon Button` default (`Type=Primary, State=Standard, Size=XL`):** 56 × 56, `pad [16, 16, 16, 16]`, `radius 8`, fill `Brand/Primary`.

Full variant matrices in §7.1 (Button) and §7.2 (Icon Button).

### 3.2 Inputs (Text field family)

**Page name:** `New_INPUTS ` *(trailing space in page name — file quirk)*.

**Sets:** 3 — `_Text field` (192 variants), `_pills_Text field` (192 variants), `New_Input Text field` (2 wrapper variants). Plus 1 standalone `Pills`.

**Anatomy of `_Text field` default (`Size=Small, State=Enabled, Text-Config=Placeholder, Alignment=Top, Focused=No`):** outer 270 × 59 (`VERTICAL` wrapper, `gap 6`). Inner `Input` frame: 270 × 38, `pad [10.5, 16, 10.5, 16]` *(wider than web — mobile uses pills-style padding even for plain text fields)*, `gap 8`, `radius 8`, fill `Neutral/White`, stroke `Neutral/Stroke` (1 px).

Full anatomy in §7.3.

### 3.3 Status Bar (iOS + Android)

**Sets:** 2 — `iOS Status Bar` (4 variants: iPhone 13 / iPhone 14 pro × Background True/False), `Android Status Bar` (2: Background True/False).

| Device         | W × H   | Padding `[T, R, B, L]`  | Notes                          |
| -------------- | ------- | ----------------------- | ------------------------------ |
| iPhone 13      | 375 × 48| `[13, 16, 13, 32]`      | Notch-era safe area            |
| iPhone 14 pro  | 375 × 54| `[16, 32, 16, 52]`      | Dynamic Island safe area       |
| Android        | 360 × 52| `[10, 24, 10, 24]`      | Standard Android status height |

`Background=True` → fill `Neutral/White`. `Background=False` → transparent (let app surface show through; required when content scrolls behind the bar).

### 3.4 Home Indicator (iOS + Android)

**Sets:** 2 — `iOS Home Indicator` (2 Type variants), `Android Home Indicator` (2 Type variants).

| Platform | W × H   | Padding `[T, R, B, L]` | Notes                          |
| -------- | ------- | ---------------------- | ------------------------------ |
| iOS      | 375 × 21| `[8, 16, 8, 16]`       | Slim — just the home bar       |
| Android  | 360 × 48| `[0, 0, 0, 0]`         | Gesture navigation bar         |

`Type=Background` → fill `Neutral/White`. `Type=Without Background` → transparent.

> **Hard rule:** every full-screen design MUST include a Status Bar at the top and a Home Indicator at the bottom (or equivalent safe-area inset). Never render content over those zones unintentionally.

### 3.5 Top Nav

**Set:** 1 — `Top Navigation` (3 Type variants).

| Type    | W × H    | Fill         | Use                                                            |
| ------- | -------- | ------------ | -------------------------------------------------------------- |
| Title   | 375 × 56 | `Neutral/White` | Standard nav bar with title + leading/trailing icons        |
| Search  | 375 × 96 | `Neutral/White` | Title row + integrated search field below                   |
| Modal   | 375 × 68 | `#000000`    | Black header for modal screens (`Brand/Gray/highContrast/700` text on black) |

Booleans control: Left/Right Title (text), Left/Right Icon (icon visibility), Avatar (profile thumbnail).

### 3.6 Bottom App Menu (Bottom Navigation)

**Sets:** 2 — `Bottom Navigation Tab` (16 variants: Label × Selected × Badge size), `Bottom Navigation` (9 variants: System iOS/Android × Tab Count 2/3/4/5/Float).

**`Bottom Navigation Tab`** — single tab cell, always 70 wide. Height = 64 (with label) or 40 (icon-only). `radius 100` (full-pill highlight when selected).

**`Bottom Navigation`** — full bottom bar:

| System  | W × H     | Notes                                                            |
| ------- | --------- | ---------------------------------------------------------------- |
| iOS     | 375 × 85  | 5 variants: Tab Count = 2 / 3 / 4 / 5 / Float                    |
| Android | 360 × 112 | 4 variants: Tab Count = 2 / 3 / 4 / 5                            |

Common chrome: fill `Neutral/White`, top stroke `#E2E8F0` (`slate/200` from base.md — note the raw hex here is the same), effect `Blur/Tabbar` (library — frosted backdrop blur).

iOS `Float` variant has no fill / no stroke (transparent floating tab bar — content shows through the blur).

### 3.7 Tabs and Chips

**Sets:** 2 — `Tabs` (2 underline-style variants) and `Chips` (3 selection-style variants).

**Tabs** (underline indicator below content row):
- Selected: 42 × 33, no bottom padding (sits flush with underline)
- Default: 41 × 33, `pad [0, 0, 8, 0]` (extra space allows the underline to sit below the label)

**Chips** (pill-style filter selection):

| Property 1 | W × H    | Fill              | Stroke           | Radius |
| ---------- | -------- | ----------------- | ---------------- | ------ |
| Default    | 53 × 31  | `Neutral/White`   | `Neutral/Stroke` | 86 (pill) |
| Current    | 53 × 31  | `Brand/Light/100` | `Brand/Primary`  | 86 (pill) |
| Selected   | 79 × 31  | `Brand/Light/200` | —                | 86 (pill) |

All chips: `pad [8, 14, 8, 14]`, `gap 3`. The Selected variant is wider — typically used when chip carries a count badge.

### 3.8 Toggle

**Set:** 1 — `Toggle-mw` (60 variants: Size × State × Status × Icon × With Text × Support Text).

Same matrix and anatomy as web's Toggle. Track 36 × 20. Focused state adds `Focused Effect`. See §7.6 for the full grid.

### 3.9 Tooltip

**Set:** 1 — `Tooltip` (3 Position variants: Center / Left / Right).

| Position | W × H    | Body `pad`         | Body fill       |
| -------- | -------- | ------------------ | --------------- |
| Center   | 301 × 63 | `[6, 6, 6, 6]`     | `Neutral/Text`  |
| Left     | 301 × 63 | `[6, 6, 6, 6]`     | `Neutral/Text`  |
| Right    | 301 × 63 | `[6, 6, 6, 6]`     | `Neutral/Text`  |

All variants share `gap -6` (caret overlaps body). **Mobile tooltip is slightly larger than the web equivalent (301 × 63 vs web 282 × 59) — touch-target ergonomics.**

> Web has 6 positions (incl. Bottom + Position Left/Right). Mobile has only 3 — Center/Left/Right. If you need Bottom on mobile, surface as a gap to design.

### 3.10 Bottom Sheet

**Standalone components** — 2: `Bottom Sheet` (the sheet container) and `Content` (default content stub).

**Anatomy — `Bottom Sheet`:**
- 375 × 566, layout `VERTICAL`, `pad [16, 0, 0, 0]`, `gap 16`, fill `Neutral/White`.
- Includes a 24 × 4 drag handle pill at the top (rendered as a small rounded rectangle).
- Stacks on top of a 50% dim overlay (`Neutral/Text @ 50%`).

**Anatomy — `Content`:** 343 × 400, the default body slot (no fill/treatment by itself — meant to be overridden per use-site).

### 3.11 Dialog Box / Popup

**Standalone components** — 2: `Popup` (the dialog card) and `Content` (default content stub).

**Anatomy — `Popup`:**
- 343 × 180, `radius 8`, fill `Neutral/White`.
- Centred over a 50% dim overlay (`Neutral/Text @ 50%`).

**Anatomy — `Content`:** 309 × 34 default slot.

### 3.12 Icons

The Mobile Guidelines file ships **886 icon components** in the `Icons` page (`8:816`). The set is **Lucide Icons** (verified — naming matches Lucide exactly) plus a handful of Petpooja-specific glyphs and a few file-bugs at the end.

#### 3.12.1 Naming & usage rules

1. **Reference icons by `icon/{name}` only.** Do not draw new icons; do not import from other sets.
2. **Default icon size in mobile components:**
   - Status Bar: 17 px
   - Top Nav: 24 px
   - Bottom Navigation Tab: 24 px
   - Input leading / trailing: 16 px
   - Button leading / trailing (Small / Medium): 16 px; (Large / XL): 20 px
   - Icon Button content: scales to fit the host (Small 16, Medium 20, Large 24, XL 32 — approximate)
3. **Icon vectors are stroked (not filled)** — stroke colour is inherited from the parent text/icon role (`Neutral/Text`, `Neutral/White`, `Brand/Primary`, etc.).
4. **Stroke weight on icon vectors: `1.5 px`** (matches web).
5. There is a near-empty second `Icons` page (`242:68`, 1 child) — **ignore it**; use `8:816` exclusively.
6. **If a needed icon is not in the catalog below, stop and ask — do not improvise.**

#### 3.12.2 Known file anomalies in the icon catalog

These 10 names break the `icon/{kebab-case}` convention. Reproduced verbatim (do not rename in code), but flag if your tooling chokes:

| Name                    | Issue                                                                |
| ----------------------- | -------------------------------------------------------------------- |
| `icon/Google`           | Capital G — brand icon, casing differs from rest                     |
| `icon/Placeholder`      | Capital P — placeholder stub, likely meant to be removed             |
| `tool-02`               | Missing `icon/` prefix; appears between `icon/settings-2` and `icon/settings` |
| `Payment Out`           | No `icon/` prefix, has space; Petpooja-specific                      |
| `Payment In`            | No `icon/` prefix, has space; Petpooja-specific                      |
| `receipt-text 1`        | No `icon/` prefix, trailing ` 1` suffix                              |
| `monitor-smartphone 1`  | No `icon/` prefix, trailing ` 1` suffix; duplicate of `icon/monitor-smartphone` |
| `barcode 2`             | No `icon/` prefix, trailing ` 2`; barcode icon                       |
| `keyboard 1`            | No `icon/` prefix, trailing ` 1`; duplicate of `icon/keyboard`       |

**Rule:** when referencing these in code, use the exact name as it appears in Figma. Surface the inconsistency to design and request renames.

#### 3.12.3 Full alphabetical catalog (886 icons)

All standard `icon/*` names below. Use `Ctrl+F` / `Cmd+F` to search. Non-standard names are listed separately in §3.12.4.

**A**
`accessibility`, `activity`, `air-vent`, `airplay`, `alarm-check`, `alarm-clock`, `alarm-clock-off`, `alarm-minus`, `alarm-plus`, `album`, `alert-circle`, `alert-octagon`, `alert-triangle`, `align-center`, `align-center-horizontal`, `align-center-vertical`, `align-end-horizontal`, `align-end-vertical`, `align-horizontal-distribute-center`, `align-horizontal-distribute-end`, `align-horizontal-distribute-start`, `align-horizontal-justify-center`, `align-horizontal-justify-end`, `align-horizontal-justify-start`, `align-horizontal-space-around`, `align-horizontal-space-between`, `align-justify`, `align-left`, `align-right`, `align-start-horizontal`, `align-start-vertical`, `align-vertical-distribute-center`, `align-vertical-distribute-end`, `align-vertical-distribute-start`, `align-vertical-justify-center`, `align-vertical-justify-end`, `align-vertical-justify-start`, `align-vertical-space-around`, `align-vertical-space-between`, `anchor`, `angry`, `annoyed`, `aperture`, `apple`, `archive`, `archive-restore`, `armchair`, `arrow-big-down`, `arrow-big-left`, `arrow-big-right`, `arrow-big-up`, `arrow-down`, `arrow-down-circle`, `arrow-down-left`, `arrow-down-right`, `arrow-left`, `arrow-left-circle`, `arrow-left-right`, `arrow-right`, `arrow-right-circle`, `arrow-up`, `arrow-up-circle`, `arrow-up-down`, `arrow-up-left`, `arrow-up-right`, `asterisk`, `at-sign`, `award`, `axe`, `axis-3d`

**B**
`baby`, `backpack`, `baggage-claim`, `banana`, `banknote`, `bar-chart`, `bar-chart-2`, `bar-chart-3`, `bar-chart-4`, `bar-chart-horizontal`, `baseline`, `bath`, `battery`, `battery-charging`, `battery-full`, `battery-low`, `battery-medium`, `battery-warning`, `beaker`, `bean`, `bean-off`, `bed`, `bed-double`, `bed-single`, `beef`, `beer`, `bell`, `bell-minus`, `bell-off`, `bell-plus`, `bell-ring`, `bike`, `binary`, `bitcoin`, `bluetooth`, `bluetooth-connected`, `bluetooth-off`, `bluetooth-searching`, `bold`, `bomb`, `bone`, `book`, `book-open`, `book-open-check`, `bookmark`, `bookmark-minus`, `bookmark-plus`, `bot`, `box`, `box-select`, `boxes`, `briefcase`, `brush`, `bug`, `building`, `building-2`, `bus`

**C**
`cake`, `calculator`, `calendar`, `calendar-check`, `calendar-check-2`, `calendar-clock`, `calendar-days`, `calendar-heart`, `calendar-minus`, `calendar-off`, `calendar-plus`, `calendar-range`, `calendar-search`, `calendar-x`, `calendar-x-2`, `camera`, `camera-off`, `candy`, `candy-off`, `car`, `carrot`, `cast`, `cat`, `check`, `check-check`, `check-circle`, `check-circle-2`, `check-square`, `chef-hat`, `cherry`, `chevron-down`, `chevron-first`, `chevron-last`, `chevron-left`, `chevron-right`, `chevron-up`, `chevrons-down`, `chevrons-down-up`, `chevrons-left`, `chevrons-left-right`, `chevrons-right`, `chevrons-right-left`, `chevrons-up`, `chevrons-up-down`, `chrome`, `cigarette`, `cigarette-off`, `circle`, `circle-dot`, `circle-ellipsis`, `circle-slashed`, `citrus`, `clapperboard`, `clipboard`, `clipboard-check`, `clipboard-copy`, `clipboard-edit`, `clipboard-list`, `clipboard-signature`, `clipboard-type`, `clipboard-x`, `clock`, `clock-1`, `clock-2`, `clock-3`, `clock-4`, `clock-5`, `clock-6`, `clock-7`, `clock-8`, `clock-9`, `clock-10`, `clock-11`, `clock-12`, `cloud`, `cloud-cog`, `cloud-drizzle`, `cloud-fog`, `cloud-hail`, `cloud-lightning`, `cloud-moon`, `cloud-moon-rain`, `cloud-off`, `cloud-rain`, `cloud-rain-wind`, `cloud-snow`, `cloud-sun`, `cloud-sun-rain`, `cloudy`, `clover`, `code`, `code-2`, `codepen`, `codesandbox`, `coffee`, `cog`, `coins`, `columns`, `command`, `compass`, `component`, `concierge-bell`, `contact`, `contrast`, `cookie`, `copy`, `copyleft`, `copyright`, `corner-down-left`, `corner-down-right`, `corner-left-down`, `corner-left-up`, `corner-right-down`, `corner-right-up`, `corner-up-left`, `corner-up-right`, `cpu`, `credit-card`, `croissant`, `crop`, `cross`, `crosshair`, `crown`, `cup-soda`, `curly-braces`, `currency`

**D**
`database`, `database-backup`, `delete`, `diamond`, `dice-1`, `dice-2`, `dice-3`, `dice-4`, `dice-5`, `dice-6`, `dices`, `diff`, `disc`, `divide`, `divide-circle`, `divide-square`, `dna`, `dna-off`, `dog`, `dollar-sign`, `download`, `download-cloud`, `dribbble`, `droplet`, `droplets`, `drumstick`, `dumbbell`

**E**
`ear`, `ear-off`, `edit`, `edit-2`, `edit-3`, `egg`, `egg-fried`, `egg-off`, `equal`, `equal-not`, `eraser`, `euro`, `expand`, `external-link`, `eye`, `eye-off`

**F**
`facebook`, `factory`, `fan`, `fast-forward`, `feather`, `figma`, `file`, `file-archive`, `file-audio`, `file-audio-2`, `file-axis-3d`, `file-badge`, `file-badge-2`, `file-bar-chart`, `file-bar-chart-2`, `file-box`, `file-check`, `file-check-2`, `file-clock`, `file-code`, `file-cog`, `file-cog-2`, `file-diff`, `file-digit`, `file-down`, `file-edit`, `file-heart`, `file-image`, `file-input`, `file-json`, `file-json-2`, `file-key`, `file-key-2`, `file-line-chart`, `file-lock`, `file-lock-2`, `file-minus`, `file-minus-2`, `file-output`, `file-pie-chart`, `file-plus`, `file-plus-2`, `file-question`, `file-scan`, `file-search`, `file-search-2`, `file-signature`, `file-spreadsheet`, `file-symlink`, `file-terminal`, `file-text`, `file-type`, `file-type-2`, `file-up`, `file-video`, `file-video-2`, `file-volume`, `file-volume-2`, `file-warning`, `file-x`, `file-x-2`, `files`, `film`, `filter`, `fingerprint`, `fish`, `flag`, `flag-off`, `flag-triangle-left`, `flag-triangle-right`, `flame`, `flashlight`, `flashlight-off`, `flask-conical`, `flask-conical-off`, `flask-round`, `flip-horizontal`, `flip-horizontal-2`, `flip-vertical`, `flip-vertical-2`, `flower`, `flower-2`, `focus`, `folder`, `folder-archive`, `folder-check`, `folder-clock`, `folder-closed`, `folder-cog`, `folder-cog-2`, `folder-down`, `folder-edit`, `folder-heart`, `folder-input`, `folder-key`, `folder-lock`, `folder-minus`, `folder-open`, `folder-output`, `folder-plus`, `folder-search`, `folder-search-2`, `folder-symlink`, `folder-tree`, `folder-up`, `folder-x`, `folders`, `form-input`, `forward`, `frame`, `framer`, `frown`, `fuel`, `function-square`

**G**
`gamepad`, `gamepad-2`, `gauge`, `gavel`, `gem`, `ghost`, `gift`, `git-branch`, `git-branch-plus`, `git-commit`, `git-compare`, `git-fork`, `git-merge`, `git-pull-request`, `git-pull-request-closed`, `git-pull-request-draft`, `github`, `gitlab`, `glass-water`, `glasses`, `globe`, `globe-2`, `grab`, `graduation-cap`, `grape`, `grid`, `grip-horizontal`, `grip-vertical`

**H**
`hammer`, `hand`, `hand-metal`, `hard-drive`, `hard-hat`, `hash`, `haze`, `heading`, `heading-1`, `heading-2`, `heading-3`, `heading-4`, `heading-5`, `heading-6`, `headphones`, `heart`, `heart-crack`, `heart-handshake`, `heart-off`, `heart-pulse`, `help-circle`, `hexagon`, `highlighter`, `history`, `home`, `hop`, `hop-off`, `hourglass`

**I**
`ice-cream`, `ice-cream-2`, `image`, `image-minus`, `image-off`, `image-plus`, `import`, `inbox`, `indent`, `indian-rupee`, `infinity`, `info`, `inspect`, `instagram`, `italic`

**J**
`japanese-yen`, `joystick`

**K**
`key`, `keyboard`

**L**
`lamp`, `lamp-ceiling`, `lamp-desk`, `lamp-floor`, `lamp-wall-down`, `lamp-wall-up`, `landmark`, `languages`, `laptop`, `laptop-2`, `lasso`, `lasso-select`, `laugh`, `layers`, `layout`, `layout-dashboard`, `layout-grid`, `layout-list`, `layout-template`, `leaf`, `library`, `life-buoy`, `lightbulb`, `lightbulb-off`, `line-chart`, `link`, `link-2`, `link-2-off`, `linkedin`, `list`, `list-checks`, `list-end`, `list-minus`, `list-music`, `list-ordered`, `list-plus`, `list-start`, `list-video`, `list-x`, `loader`, `loader-2`, `locate`, `locate-fixed`, `locate-off`, `lock`, `log-in`, `log-out`, `luggage`

**M**
`magnet`, `mail`, `mail-check`, `mail-minus`, `mail-open`, `mail-plus`, `mail-question`, `mail-search`, `mail-warning`, `mail-x`, `mails`, `map`, `map-pin`, `map-pin-off`, `martini`, `maximize`, `maximize-2`, `medal`, `megaphone`, `megaphone-off`, `meh`, `menu`, `message-circle`, `message-square`, `mic`, `mic-2`, `mic-off`, `microscope`, `microwave`, `milestone`, `milk`, `milk-off`, `minimize`, `minimize-2`, `minus`, `minus-circle`, `minus-square`, `monitor`, `monitor-off`, `monitor-smartphone`, `monitor-speaker`, `moon`, `more-horizontal`, `more-vertical`, `mountain`, `mountain-snow`, `mouse`, `mouse-pointer`, `mouse-pointer-2`, `mouse-pointer-click`, `move`, `move-3d`, `move-diagonal`, `move-diagonal-2`, `move-horizontal`, `move-vertical`, `music`, `music-2`, `music-3`, `music-4`

**N**
`navigation`, `navigation-2`, `navigation-2-off`, `navigation-off`, `network`, `newspaper`, `nut`, `nut-off`

**O**
`octagon`, `option`, `outdent`

**P**
`package`, `package-2`, `package-check`, `package-minus`, `package-open`, `package-plus`, `package-search`, `package-x`, `paint-bucket`, `paintbrush`, `paintbrush-2`, `palette`, `palmtree`, `paperclip`, `party-popper`, `pause`, `pause-circle`, `pause-octagon`, `pen-tool`, `pencil`, `percent`, `person-standing`, `phone`, `phone-call`, `phone-forwarded`, `phone-incoming`, `phone-missed`, `phone-off`, `phone-outgoing`, `pie-chart`, `piggy-bank`, `pilcrow`, `pin`, `pin-off`, `pipette`, `pizza`, `plane`, `play`, `play-circle`, `plug`, `plug-2`, `plug-zap`, `plus`, `plus-circle`, `plus-square`, `pocket`, `podcast`, `pointer`, `pound-sterling`, `power`, `power-off`, `printer`, `puzzle`

**Q**
`qr-code`, `quote`

**R**
`radio`, `radio-receiver`, `rectangle-horizontal`, `rectangle-vertical`, `recycle`, `redo`, `redo-2`, `refresh-ccw`, `refresh-cw`, `refrigerator`, `regex`, `repeat`, `repeat-1`, `reply`, `reply-all`, `rewind`, `rocket`, `rocking-chair`, `rotate-3d`, `rotate-ccw`, `rotate-cw`, `rss`, `ruler`, `russian-ruble`

**S**
`sailboat`, `salad`, `sandwich`, `save`, `scale`, `scale-3d`, `scaling`, `scan`, `scan-face`, `scan-line`, `scissors`, `screen-share`, `screen-share-off`, `scroll`, `search`, `send`, `separator-horizontal`, `separator-vertical`, `server`, `server-cog`, `server-crash`, `server-off`, `settings`, `settings-2`, `share`, `share-2`, `sheet`, `shield`, `shield-alert`, `shield-check`, `shield-close`, `shield-off`, `shirt`, `shopping-bag`, `shopping-cart`, `shovel`, `shower-head`, `shrink`, `shrub`, `shuffle`, `sidebar`, `sidebar-close`, `sidebar-open`, `sigma`, `signal`, `signal-high`, `signal-low`, `signal-medium`, `signal-zero`, `siren`, `skip-back`, `skip-forward`, `skull`, `slack`, `slash`, `slice`, `sliders`, `sliders-horizontal`, `smartphone`, `smartphone-charging`, `smile`, `smile-plus`, `snowflake`, `sofa`, `sort-asc`, `sort-desc`, `soup`, `speaker`, `spline`, `sprout`, `square`, `star`, `star-half`, `star-off`, `stethoscope`, `sticker`, `sticky-note`, `stop-circle`, `stretch-horizontal`, `stretch-vertical`, `strikethrough`, `subscript`, `subtitles`, `sun`, `sun-dim`, `sun-medium`, `sun-moon`, `sun-snow`, `sunrise`, `sunset`, `superscript`, `swiss-franc`, `switch-camera`, `sword`, `swords`, `syringe`

**T**
`table`, `table-2`, `tablet`, `tag`, `tags`, `target`, `tent`, `terminal`, `terminal-square`, `text-cursor`, `text-cursor-input`, `thermometer`, `thermometer-snowflake`, `thermometer-sun`, `thumbs-down`, `thumbs-up`, `ticket`, `timer`, `timer-off`, `timer-reset`, `toggle-left`, `toggle-right`, `tornado`, `toy-brick`, `train`, `trash`, `trash-2`, `tree-deciduous`, `tree-pine`, `trees`, `trello`, `trending-down`, `trending-up`, `triangle`, `trophy`, `truck`, `tv`, `tv-2`, `twitch`, `twitter`, `type`

**U**
`umbrella`, `underline`, `undo`, `undo-2`, `unlink`, `unlink-2`, `unlock`, `upload`, `upload-cloud`, `usb`, `user`, `user-check`, `user-cog`, `user-minus`, `user-plus`, `user-x`, `users`, `utensils`, `utensils-crossed`

**V**
`vegan`, `venetian-mask`, `verified`, `vibrate`, `vibrate-off`, `video`, `video-off`, `view`, `voicemail`, `volume`, `volume-1`, `volume-2`, `volume-x`

**W**
`wallet`, `wand`, `wand-2`, `watch`, `waves`, `webcam`, `webhook`, `wheat`, `wheat-off`, `wifi`, `wifi-off`, `wind`, `wine`, `wine-off`, `wrap-text`, `wrench`

**X**
`x`, `x-circle`, `x-octagon`, `x-square`

**Y**
`youtube`

**Z**
`zap`, `zap-off`, `zoom-in`, `zoom-out`

**Brand / capitalised:**
`Google`, `Placeholder`

#### 3.12.4 Non-standard names (file bugs — use verbatim until renamed)

The Mobile Guidelines file contains **6 icons that do NOT follow the `icon/{kebab-case}` convention**. Use these names exactly as written in any reference; do not normalise them:

| Verbatim name              | Probable intent              | Status                                         |
| -------------------------- | ----------------------------- | ---------------------------------------------- |
| `Payment Out`              | Petpooja-specific outgoing-payment glyph | Keep — used in POS contexts        |
| `Payment In`               | Petpooja-specific incoming-payment glyph | Keep — used in POS contexts        |
| `receipt-text 1`           | Receipt with text lines       | Rename to `icon/receipt-text` (file fix)       |
| `monitor-smartphone 1`     | Duplicate of `icon/monitor-smartphone` | Remove duplicate (file fix)           |
| `barcode 2`                | Barcode glyph                 | Rename to `icon/barcode` (file fix)            |
| `keyboard 1`               | Duplicate of `icon/keyboard`  | Remove duplicate (file fix)                    |
| `tool-02`                  | Likely a Settings/tools glyph; sits between `icon/settings-2` and `icon/settings` | Rename to `icon/tool-2` or remove (file fix) |

> When implementing in code, reference the icon by its **exact Figma name** (e.g. `"Payment In"` with the space and capitalisation). File renames are the responsibility of the design team — surface these as drift.

#### 3.12.5 Total count

886 icons total:
- **879** standard `icon/{name}` glyphs (incl. `icon/Google` and `icon/Placeholder` with non-kebab casing)
- **7** non-standard names (Payment In, Payment Out, receipt-text 1, monitor-smartphone 1, barcode 2, keyboard 1, tool-02)

> **Compared to the Web Guidelines file**, which ships 2,422 icons (almost 3 × more). Mobile carries the most-used ~880 Lucide glyphs plus the 6 Petpooja-specific extras. If a glyph is needed on mobile but only exists in web's icon set, surface the gap — do not silently substitute.

---

## 4. Deprecated / empty pages (do not use)

| Figma page name | Notes                                                                  |
| --------------- | ---------------------------------------------------------------------- |
| `Icons` (`242:68`) | 1-child placeholder — use `Icons` (`8:816`) instead                 |
| `CheckBoc`         | Empty page — typo of "Checkbox". **Mobile checkboxes / radio buttons are not yet defined in this file.** Use `base.md`-token-only renderings or escalate. |
| `Page 5`           | Empty placeholder — skip                                            |

> **Hard rule:** if a mobile design requires a checkbox or radio button, surface the gap. The Mobile Guidelines file does NOT yet ship those components — the empty `CheckBoc` page is a known stub.

---

## 5. What this file does NOT contain (and where to find it)

The following are absent on mobile and have **no fallback in `base.md`**. Either:
1. Reuse the web component (with mobile-appropriate tokens), surfacing this to design, or
2. Stop and ask.

Missing on mobile:
- Checkbox / Radio Button (page is stubbed — see §4)
- Dropdowns / Select / Menu
- Date / Time picker / Calendar
- Table (mobile typically uses list rows instead)
- Pagination (mobile typically uses infinite scroll / load-more)
- Stepper / Progress bar
- Slider / Range
- Filters popover (mobile typically pushes to its own screen)
- Badges (mobile uses inline status badges within rows — flag if needed)
- Toaster / Snackbar
- Side Drawer (mobile uses Bottom Sheet — see §3.10)

> If any of these is required, raise it before designing.

---

## 6. Known file-level drift & file bugs

1. **Button uses `Desktop/*` text styles** — every Button variant binds to `Desktop/Body/{Size}/Medium` instead of `Mobile/Body/{Size}/Medium`. Visually similar at most sizes, but semantically wrong on mobile. Implement against `Mobile/*` and raise as a Figma fix.
2. **One Button variant uses `Text/Md/Medium`** (a library text style, not in `base.md`) for `Size=Large, Type=Quaternary, State=Disable`. Other Disable variants at the same size use `Desktop/Body/Large/Medium`. Treat as `Mobile/Body/Large/Medium` in code.
3. **Inputs use the wider pills-style padding** (`[10.5, 16, 10.5, 16]` for Small) in the plain `_Text field` set — web's `_Text field` uses `[0, 0, 0, 12]`. Confirmed intentional (mobile touch targets), but flag if it shows up in code review as a "bug".
4. **Inputs Error stroke is inconsistent within a set:** Small/Extra Small variants use `Error/Content`; Large/Extra Large variants use `Primary/Red Stroke` (library token). Pick one in code; surface to design.
5. **Trailing space in page name `New_INPUTS `** — file quirk.
6. **Empty `CheckBoc` page (typo)** — no Checkbox component shipped.
7. **Top Nav Modal variant uses `#000000`** — not a `base.md` token. Treat as an intentional override (modal headers are black on mobile per platform conventions).
8. **`#E2E8F0` raw hex** on Bottom Navigation top stroke — equals `slate/200` from `base.md §1` (which appears in the variables I extracted earlier). Code may bind to either; prefer the token.
9. **Icon Button references several raw hex values** in Hover / Pressed / Disabled states (`#FFFDF8`, `#FFFBEC`, `#EBD583`, `#153CC6`, `#F1F5F9`) and library tokens (`Brand/Primary Light/200 - Hover`, `Brand/Primary Light/300`) that are NOT in `base.md`. Surface to design — these likely need to be canonicalised.
10. **`Pretty Shadows/*` from web don't exist here** — mobile inherits shadows from imported library effects (`Blur/Tabbar`, `Shadow/xs`, `Focused Effect`, etc.). If a design needs a card shadow on mobile, surface the gap and request a token.

---

## 7. Variant anatomy appendix

Same structure as `web.md §7`. Each component below shows non-default variant anatomy compressed into axis-rule tables.

> **How to read:** find the row matching the target (e.g. `Primary / Hover / Medium`). Attributes not listed in a row inherit from the component's default in §3.

### 7.1 Button — full variant anatomy (272 variants)

The mobile Button has the **same axis matrix as web Button** (`Size × Type × State × Icon Left × Icon Right × Only Icon`), but the State→fill rules differ slightly from web. **Read carefully.**

**Constants:** `radius 8`, `gap 0` (text-only) or `gap 4` (with icons) or `gap 10` (only-icon), layout `HORIZONTAL`, `align CENTER/CENTER`.

#### 7.1.1 Size axis (governs height + padding + text style)

| Size           | Height | Padding `[T, R, B, L]` | Text style ⚠️ *(file binds Desktop/* — should be Mobile/*)*  | Only-Icon size | Only-Icon padding |
| -------------- | ------ | ----------------------- | -------------------------------------- | -------------- | ----------------- |
| Small          | 32     | `[4, 14, 4, 14]` (Quat/Pri) / `[8, 16, 8, 16]` (Sec/Ter) | `Desktop/Body/Small/Medium` → use `Mobile/Body/Small/Medium`   | 32 × 32        | `[6, 6, 6, 6]`    |
| Medium         | 38     | `[10, 16, 10, 16]`      | `Desktop/Body/Medium/Medium` → use `Mobile/Body/Medium/Medium` | 38 × 38        | `[7, 7, 7, 7]`    |
| Large          | 44     | `[10, 16, 10, 16]`      | `Desktop/Body/Large/Medium` → use `Mobile/Body/Large/Medium`   | 44 × 44        | `[7, 7, 7, 7]`    |
| Extra Large    | 50     | `[10, 16, 10, 16]`      | `Desktop/Body/Large/Medium` → use `Mobile/Body/Large/Medium`   | 50 × 50        | `[7, 7, 7, 7]`    |

#### 7.1.2 Type × State axis (governs fill / stroke / effect / text fill)

| Type        | State          | Fill                                             | Stroke               | Effect                  | Text fill                       |
| ----------- | -------------- | ------------------------------------------------ | -------------------- | ----------------------- | ------------------------------- |
| Primary     | Default        | `Brand/Primary`                                  | —                    | —                       | `Neutral/White`                 |
| Primary     | Hover          | `Brand/Dark/600`                                 | —                    | —                       | `Neutral/White`                 |
| Primary     | While Pressed  | `Brand/Dark/600`                                 | —                    | `Button Shadow Hovered` | `Neutral/White`                 |
| Primary     | **Disable**    | **`Brand/Light/200`** ⚠️ *(differs from web's `Neutral/Grey 1`)* | —     | —                       | **`Brand/Light/400`** ⚠️ *(differs from web)* |
| Secondary   | Default        | `Neutral/White` (Small uses `Brand/Gray/highContrast/700`) | `Neutral/Stroke` (1px) | `Button Shadow`       | `Neutral/Text`                  |
| Secondary   | Hover          | `Brand/Light/100`                                | `Neutral/Stroke` (1px) | —                     | `Neutral/Text`                  |
| Secondary   | While Pressed  | `Brand/Light/100`                                | `Neutral/Stroke` (1px) | `Button Shadow Hovered` | `Neutral/Text`                |
| Secondary   | **Disable**    | **`Surface/Disabled`** ⚠️ *(differs from web's `Neutral/Grey 1`)*   | `Neutral/Stroke` (1px) | `Button Shadow`     | **`Neutral/Disabled`** ⚠️ *(differs from web's `Neutral/Sub Content`)* |
| Tertiary    | Default        | `Neutral/White`                                  | `Brand/Primary` (1px) | `Button Shadow`        | `Brand/Primary`                 |
| Tertiary    | Hover          | `#F5F8FF` *(off-token; ≈ `Brand/Light/100`)*     | `Brand/Primary` (1px) | —                      | `Brand/Primary`                 |
| Tertiary    | While Pressed  | `Brand/Light/100`                                | `Brand/Primary` (1px) | `Button Shadow Hovered` | `Brand/Primary`                |
| Tertiary    | **Disable**    | **`Neutral/White` + stroke `Brand/Light/300`** ⚠️ *(differs from web — web collapses Disable to `Neutral/Grey 1`)* | `Brand/Light/300` (1px) | `Button Shadow` | **`Brand/Light/300`** ⚠️ *(differs from web)* |
| Quaternary  | Default        | — (transparent)                                  | —                    | —                       | `Brand/Gray/highContrast/700`   |
| Quaternary  | Hover / While Pressed | — (transparent) ⚠️ *(no hover affordance — same gap as web)* | —     | (none / `Button Shadow Hovered`) | `Brand/Gray/highContrast/700`        |
| Quaternary  | Disable        | — (transparent)                                  | —                    | —                       | `Brand/Gray/highContrast/700`   |
| Action Button | Default      | `Neutral/White`                                  | `Neutral/Stroke` (1px) | —                     | (icon-only, no text)            |
| Action Button | Hover        | `Brand/Light/100`                                | `Neutral/Stroke` (1px) | —                     | —                               |
| Action Button | While Pressed | `Brand/Light/100`                               | `Neutral/Stroke` (1px) | `Button Shadow Hovered` | —                             |
| Action Button | Disable      | `Neutral/Grey 1`                                 | —                    | —                       | —                               |

> **Three big diffs vs. web Button:**
> 1. **Primary/Disable on mobile** stays in the brand-light family (`Brand/Light/200` + `Brand/Light/400` text), giving a softer disabled look.
> 2. **Secondary/Disable on mobile** uses `Surface/Disabled` + `Neutral/Disabled` text (vs. web's `Neutral/Grey 1` + `Neutral/Sub Content`).
> 3. **Tertiary/Disable on mobile** keeps the outline (`Brand/Light/300`) — visually still looks like a Tertiary button, just muted. Web collapses Tertiary/Disable to a filled grey button.

#### 7.1.3 Icon axis

Width grows when icons are added (same pattern as web): default text-only ≈ 90 → +13 with one icon → +15 with both. `gap` goes 0 → 4 → 10 (only-icon).

### 7.2 Icon Button — full variant anatomy (48 variants)

Mobile-only component — NOT in `web.md`. 3 Types × 4 States × 4 Sizes = 48 variants.

**Constants:** `radius 8`, layout `HORIZONTAL`, `gap 0`.

#### 7.2.1 Size axis

| Size   | W × H   | Padding              |
| ------ | ------- | -------------------- |
| Small  | 32 × 32 | `[4, 4, 4, 4]`       |
| Medium | 40 × 40 | `[8, 8, 8, 8]`       |
| Large  | 48 × 48 | `[12, 12, 12, 12]`   |
| XL     | 56 × 56 | `[16, 16, 16, 16]`   |

#### 7.2.2 Type × State axis (fill / stroke)

| Type      | State    | Fill                                       | Stroke             |
| --------- | -------- | ------------------------------------------ | ------------------ |
| Primary   | Standard | `Brand/Primary`                            | —                  |
| Primary   | Hover    | `Brand/Dark/600`                           | —                  |
| Primary   | Pressed  | `#153CC6` *(raw hex; no `base.md` mirror)* | —                  |
| Primary   | Disabled | `#F1F5F9` *(raw hex; ≈ `Neutral/Grey 2` `#F8F8F8` but lighter blue)* | — |
| Secondary | Standard | `Brand/Primary Light/200 - Hover` *(library; no `base.md` mirror)* | `Brand/Primary` (1px) |
| Secondary | Hover    | `Brand/Primary Light/300` *(library)*      | `Brand/Primary` (1px) |
| Secondary | Pressed  | `#EBD583` *(raw hex; mustard-ish; no `base.md` mirror)* | — |
| Secondary | Disabled | `#F1F5F9` *(raw hex)*                      | —                  |
| Tertiary  | Standard | `Neutral/White`                            | `Brand/Primary` (1px) |
| Tertiary  | Hover    | `#FFFDF8` *(raw hex; very pale yellow)*    | `Brand/Primary` (1px) |
| Tertiary  | Pressed  | `#FFFBEC` *(raw hex; pale yellow)*         | `Brand/Dark/600` (1px) |
| Tertiary  | Disabled | `Neutral/White`                            | —                  |

> **Drift cluster:** Icon Button references **6 raw-hex values** (`#153CC6`, `#F1F5F9`, `#EBD583`, `#FFFDF8`, `#FFFBEC`) and **3 library tokens** (`Brand/Primary Light/200 - Hover`, `Brand/Primary Light/300`) that are **not in `base.md`**. Implement against the closest base tokens (e.g. `Brand/Primary` family) and surface these gaps to design.

### 7.3 Inputs (`_Text field` family) — full variant anatomy (192 + 192 + 2 = 386)

**Constants for `_Text field` and `_pills_Text field`:** outer wrapper layout `VERTICAL`, `gap 6` (label → input → supporting text). Inner `Input` frame: `radius 8`, layout `HORIZONTAL`, `gap 8`, stroke weight `1`.

#### 7.3.1 Size axis — `_Text field` (mobile uses pills-style padding even for plain text fields)

| Size         | Outer h | Input h | Input pad `[T, R, B, L]`     |
| ------------ | ------- | ------- | ----------------------------- |
| Extra Small  | 53      | 32      | `[7, 16, 7, 16]`              |
| Small        | 59      | 38      | `[10.5, 16, 10.5, 16]`        |
| Large        | 65      | 44      | `[13.5, 16, 13.5, 16]`        |
| Extra Large  | 71      | 50      | `[15.5, 16, 15.5, 16]`        |

#### 7.3.2 Size axis — `_pills_Text field` (taller, pills inside)

| Size         | Outer h | Input h | Input pad `[T, R, B, L]`     |
| ------------ | ------- | ------- | ----------------------------- |
| Extra Small  | 88      | 67      | `[7, 16, 7, 16]`              |
| Small        | 95      | 74      | `[10.5, 16, 10.5, 16]`        |
| Large        | 101     | 80      | `[13.5, 16, 13.5, 16]`        |
| Extra Large  | 105     | 84      | `[15.5, 16, 15.5, 16]`        |

#### 7.3.3 State axis (fill / stroke of the inner `Input` frame)

| State    | Fill            | Stroke                                                     | Effect (Text-Config=Placeholder) | Effect (Text-Config=Input) |
| -------- | --------------- | ---------------------------------------------------------- | -------------------------------- | -------------------------- |
| Enabled  | `Neutral/White` | `Neutral/Stroke`                                           | —                                | `Shadow/xs` *(library)*    |
| Disabled | `Neutral/White` | `Neutral/Stroke`                                           | —                                | —                          |
| Error    | `Neutral/White` | **`Error/Content`** (Small / XSmall sizes) **OR `Primary/Red Stroke`** (Large / XL sizes) ⚠️ *(inconsistent within set)* | `Input Box` | `Focused w/Error input Box` |

> **Drift note:** Disabled state on mobile uses fill `Neutral/White` (web uses `Neutral/Grey 2` to look obviously disabled). Mobile's signal is purely the inactive opacity of label / placeholder text — be deliberate when implementing.

#### 7.3.4 Focused? axis (overrides effect)

| Focused? | Effect (Enabled)        | Effect (Error)            |
| -------- | ------------------------ | ------------------------- |
| No       | per Text-Config above    | per Text-Config above     |
| Yes      | `Focused Effect`         | `Focused Error Effect`    |

#### 7.3.5 Alignment / Password? / Booleans

Same as web (`web.md §7.2.5`–§7.2.6). `Alignment=Top` is vertical label-above-input; `Alignment=Left` is horizontal label-left-of-input. `Password?=True` swaps `Visible Text` for `Hidden Text` (bullets); typically pair with `Show Trailing?` for the eye-toggle.

#### 7.3.6 `New_Input Text field` (2 wrapper variants)

| Property 1 | W × H | Notes                                                        |
| ---------- | ----- | ------------------------------------------------------------ |
| Default    | (inherits) | Wraps `_Text field` default                            |
| Variant2   | (inherits) | Alternate composition (pills-equivalent)               |

### 7.4 Status Bar — full variant anatomy (6 variants across 2 sets)

#### 7.4.1 `iOS Status Bar` (4 variants)

| 📱 Device       | 👁️ Background | W × H    | Padding             | Fill            |
| -------------- | ------------- | -------- | ------------------- | --------------- |
| iPhone 13      | True          | 375 × 48 | `[13, 16, 13, 32]`  | `Neutral/White` |
| iPhone 13      | False         | 375 × 48 | `[13, 16, 13, 32]`  | transparent     |
| iPhone 14 pro  | True          | 375 × 54 | `[16, 32, 16, 52]`  | `Neutral/White` |
| iPhone 14 pro  | False         | 375 × 54 | `[16, 32, 16, 52]`  | transparent     |

All `gap 237` (pushes left status group to one end, right battery/signal group to the other).

#### 7.4.2 `Android Status Bar` (2 variants)

| 👁️ Background | W × H    | Padding             | Fill            |
| ------------- | -------- | ------------------- | --------------- |
| True          | 360 × 52 | `[10, 24, 10, 24]`  | `Neutral/White` |
| False         | 360 × 52 | `[10, 24, 10, 24]`  | transparent     |

`gap 286` (split layout).

### 7.5 Home Indicator — full variant anatomy (4 variants across 2 sets)

#### 7.5.1 `iOS Home Indicator` (2 variants)

| 🎲 Type           | W × H   | Padding            | Fill            |
| ----------------- | ------- | ------------------ | --------------- |
| Background        | 375 × 21| `[8, 16, 8, 16]`   | `Neutral/White` |
| Without Background| 375 × 21| `[8, 16, 8, 16]`   | transparent     |

#### 7.5.2 `Android Home Indicator` (2 variants)

| 🎲 Type           | W × H   | Padding            | Fill            |
| ----------------- | ------- | ------------------ | --------------- |
| Background        | 360 × 48| `[0, 0, 0, 0]`     | `Neutral/White` |
| Without Background| 360 × 48| `[0, 0, 0, 0]`     | transparent     |

### 7.6 Bottom Navigation — full variant anatomy (25 variants across 2 sets)

#### 7.6.1 `Bottom Navigation Tab` (16 variants — single tab cell)

Axes: `Label × Selected × Badge`. Width fixed at 70.

| Label | Badge       | Height | Gap |
| ----- | ----------- | ------ | --- |
| True  | None / Small / Medium / Large | 64 | 8   |
| False | None / Small / Medium / Large | 40 | 0   |

`Selected=True/False` doesn't change dimensions — it changes inner colour (Selected → icon + label render with brand primary; Default → muted). All variants share `pad [8, 8, 8, 8]`, `radius 100`.

#### 7.6.2 `Bottom Navigation` (9 variants — full bar)

All fill `Neutral/White`, stroke `#E2E8F0`, effect `Blur/Tabbar` (library).

| ⚙️ System | 🔢 Tab Count | W × H     |
| -------- | ------------ | --------- |
| iOS      | 2            | 375 × 85  |
| iOS      | 3            | 375 × 85  |
| iOS      | 4            | 375 × 85  |
| iOS      | 5            | 375 × 85  |
| iOS      | Float        | 375 × 85 *(no fill, no stroke — floating)* |
| Android  | 2            | 360 × 112 |
| Android  | 3            | 360 × 112 |
| Android  | 4            | 360 × 112 |
| Android  | 5            | 360 × 112 |

> Android bottom bar is taller (112 px) than iOS (85 px) to account for system gesture nav at the bottom.

### 7.7 Top Nav — full variant anatomy (3 Type variants in `Top Navigation`)

| 🪄 Type | W × H    | Padding         | Gap | Fill            | Notes                                    |
| ------- | -------- | --------------- | --- | --------------- | ---------------------------------------- |
| Title   | 375 × 56 | `[0, 0, 0, 0]`  | 16  | `Neutral/White` | Standard nav bar                         |
| Search  | 375 × 96 | `[0, 16, 0, 16]`| 0   | `Neutral/White` | Adds an integrated search field below    |
| Modal   | 375 × 68 | `[0, 0, 0, 0]`  | 0   | `#000000`       | Black modal header                       |

Booleans on every variant: `Left Title` / `Right Title` (text), `Left Icon` / `Right Icon` (icon visibility), `Avatar` (profile thumbnail toggle).

### 7.8 Tabs and Chips — full variant anatomy

#### 7.8.1 `Tabs` (2 variants — underline-style)

| Property 1 | W × H    | Padding         | Gap |
| ---------- | -------- | --------------- | --- |
| Selected   | 42 × 33  | `[0, 0, 0, 0]`  | 8   |
| Default    | 41 × 33  | `[0, 0, 8, 0]`  | 8   |

The difference: `Default` has `padding-bottom: 8` to leave room for the underline indicator below the row.

#### 7.8.2 `Chips` (3 variants — filter pills)

All 31 tall, `pad [8, 14, 8, 14]`, `gap 3`, `radius 86` (pill).

| Property 1 | W   | Fill              | Stroke            |
| ---------- | --- | ----------------- | ----------------- |
| Default    | 53  | `Neutral/White`   | `Neutral/Stroke` (1px) |
| Current    | 53  | `Brand/Light/100` | `Brand/Primary` (1px)  |
| Selected   | 79  | `Brand/Light/200` | —                 |

`Show icon` boolean adds a 16 × 16 leading icon (no width change for Default / Current; Selected grows wider when icon is present).

### 7.9 Toggle — full variant anatomy (60 variants in `Toggle-mw`)

Identical matrix and anatomy to web's `Toggle` (`web.md §7.10.1`). Track 36 × 20 across all variants. `State=Focused` adds effect `Focused Effect`. Track fill by `State × Status`:
- `Status=On, State=Default` → `Brand/Primary`
- `Status=On, State=Disable` → `Neutral/Disabled`
- `Status=Off, State=Default` → `Neutral/Stroke`
- `Status=Off, State=Disable` → `Neutral/Disabled`
- `State=Focused` → adds `Focused Effect` ring on top of the above

Handle (knob) is `Neutral/White`. `Icon=Yes` adds a glyph inside the knob. `With Text=Yes Left/Yes Right` adds a label sibling beside the switch.

### 7.10 Tooltip — full variant anatomy (3 Position variants)

| Position | W × H    | Caret position                  |
| -------- | -------- | ------------------------------- |
| Center   | 301 × 63 | Top edge, centred               |
| Left     | 301 × 63 | Top edge, left-aligned          |
| Right    | 301 × 63 | Top edge, right-aligned         |

All variants: `gap -6` (caret overlaps body), body `pad [6, 6, 6, 6]`, body `radius 5`, body fill `Neutral/Text` (`#192839`). Text style `Mobile/Body/Small/Regular`, fill `Neutral/White`.

> Mobile tooltip is **larger than web** (301 × 63 vs 282 × 59) and offers **fewer positions** (3 vs 6). Web's `Bottom`, `Position Left`, `Position Right` are NOT available on mobile.

### 7.11 Bottom Sheet — anatomy

Single component (no variants).

- 375 × 566, layout `VERTICAL`, `pad [16, 0, 0, 0]`, `gap 16`, fill `Neutral/White`.
- Sits over a 50% dim (`#192839 @ 50%` = `Neutral/Text @ 50%`).
- Top edge typically has a 24 × 4 rounded drag handle (visual affordance for swipe-to-dismiss).
- `Content` child (343 × 400) is the body slot — override per use-site.

### 7.12 Dialog Box / Popup — anatomy

Single component (no variants).

- 343 × 180, `radius 8`, fill `Neutral/White`.
- Centred over a 50% dim (`Neutral/Text @ 50%`).
- `Content` child (309 × 34) is the inner body slot.

---

## 8. Summary — what got extracted

- **All ~700 variants** across the 11 active component families compressed into axis-rule tables in §7.
- Mobile-specific surfaces (Status Bar, Home Indicator, Bottom Nav, Top Nav, Bottom Sheet, Dialog) fully spec'd in §3 + §7.
- Every variant's fill / stroke / effect / size / padding captured.
- Drift between Figma values and `base.md` tokens flagged inline at every spot (look for ⚠️).
- **3 major mobile-vs-web differences** explicitly called out in §7.1.2 (Button Disable handling for Primary / Secondary / Tertiary).
- Icons (886 glyphs) summarised under naming rules (§3.12) — query Figma when a specific glyph is needed.
- Empty / stubbed components flagged in §4 (no Checkbox / Radio yet) and §5 (missing components vs web).

When you need a spec for a specific (component, variant) that isn't covered above, request a targeted re-extraction by component + variant key.
