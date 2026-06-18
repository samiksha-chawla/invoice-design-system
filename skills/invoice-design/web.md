# Web Guidelines — Petpooja Design System

**Source (canonical):** https://www.figma.com/design/yJFajRsXtj45oDRWYvauhI/Web-Guidelines
**Applies to:** web (POS, dashboards, internal tools — anything rendered in a browser at a desktop/tablet layout).
**Inheritance:** Web Guidelines file defines **no local paint/text styles or variables** — all colour and type tokens are inherited from `base.md`. The only file-local styles are **10 effect styles (shadows)**. Everything else this file owns is a **component library**.

> **Always read alongside `base.md`.** Tokens come from `base.md`; shadows come from §2 below; components come from §3 below. Anything outside those three sources is invented — refuse.

---

## 1. Token pointers (what to use from `base.md` for web work)

Quick lookup. Authoritative spec for every token is in `base.md`.

### 1.1 Colour roles → `base.md` tokens

| Role on web                                      | `base.md` token                                    |
| ------------------------------------------------ | --------------------------------------------------- |
| Page background                                  | `Neutral/Background` `#F8F8F8` (`base.md §1.2`)     |
| Card / surface background                        | `Neutral/White` `#FFFFFF` (`base.md §1.2`)          |
| Subtle surface step (header rows, hovers)        | `Brand/Light/100` `#F2F5F8` (`base.md §1.1.2`)      |
| Primary text                                     | `Neutral/Text` `#192839` (`base.md §1.2`)           |
| Secondary text                                   | `Neutral/Content` `#40566D` (`base.md §1.2`)        |
| Tertiary / muted text                            | `Neutral/Sub Content` `#768EA7` (`base.md §1.2`)    |
| Disabled text / fg                               | `Neutral/Disabled` `#D0D8E0` (`base.md §1.2`)       |
| Default border                                   | `Neutral/Stroke` `#D2D6DB` (`base.md §1.2`)         |
| Brand primary fill (CTAs, active nav)            | `Brand/Primary` `#2E5391` (`base.md §1.1.1`)        |
| Brand active hover / nested nav background       | `Brand/Dark/600` `#254A88` (`base.md §1.1.3`)       |
| Brand light tint (cards, header rows)            | `Brand/Light/100..400`, `700` (`base.md §1.1.2`)    |
| Status — error (text/border)                     | `Error/Header` `#C52031`, `Error/Content` `#D92D20` (`base.md §1.3`) |
| Status — error wash                              | `Error/BG` `#FFF5F6` (`base.md §1.3`)               |
| Status — warning                                 | `Warning/*` (`base.md §1.3`)                        |
| Status — success                                 | `Success/*` (`base.md §1.3`)                        |
| Status — info / prediction                       | `Prediction/*` (`base.md §1.3`)                     |
| Tooltip background                               | `Neutral/Tooltip BG` `#373737` (`base.md §1.2`)     |
| White text on brand / dark surfaces              | `Brand/Gray/highContrast/700` `#FFFFFF` (`base.md §1.1.5`) |

### 1.2 Typography → `base.md` text styles

Use the **`Desktop/*`** scale (`base.md §2.3`). Common pairings:

| Use                          | Text style                          |
| ---------------------------- | ----------------------------------- |
| Page H1                      | `Desktop/Heading/2XLarge/Semibold`  |
| Section heading              | `Desktop/Heading/Large/Semibold`    |
| Card / panel title           | `Desktop/Heading/Small/Medium`      |
| Body                         | `Desktop/Body/Medium/Regular`       |
| Body emphasised              | `Desktop/Body/Medium/Semibold`      |
| Table cell content / labels  | `Desktop/Body/Small/Regular`        |
| Form labels                  | `Desktop/Body/Small/Medium`         |
| Button label                 | `Desktop/Body/Small/Medium`         |
| Caption / fine print         | `Desktop/Caption/SmallRegular`      |

> **Never use `Mobile/*` text styles on web.** If a request asks for a mobile-looking treatment in a web design, surface the conflict.

### 1.3 Variables vs paint styles on web

Always prefer the **variable** when both exist (`Brand/Primary/Primary`, `Neutral/Text`, etc.) — variables are how the Figma file actually rebinds tokens. Fall back to the named paint style only where the variable is missing or broken (see `base.md §1.6` drift list).

---

## 2. Effect styles (shadows) — file-local

10 effect styles defined locally in the Web Guidelines file. Use these — do not reinvent.

| Style                    | Composition (in render order)                                                                                  |
| ------------------------ | -------------------------------------------------------------------------------------------------------------- |
| `Pretty Shadows/42`      | Drop `(0, 0)` blur 1 @ 10% black · Drop `(0, 0)` blur 5 @ 10% black                                            |
| `Pretty Shadows/42 Dark` | Drop `(0, 0)` blur 1 @ 10% black · Drop `(0, 0)` blur 18 @ 15% black                                           |
| `Pretty Shadows/96`      | Drop `(0, 1)` blur 2 @ 6% black · Drop `(0, 1)` blur 3 @ 10% black                                             |
| `Pretty Shadows/97`      | Drop `(0, 2)` blur 4 spread −1 @ 6% black · Drop `(0, 4)` blur 6 spread −1 @ 10% black                         |
| `Pretty Shadows/98`      | Drop `(0, 4)` blur 6 spread −2 @ 5% black · Drop `(0, 10)` blur 15 spread −3 @ 10% black                       |
| `Pretty Shadows/99`      | Drop `(0, 10)` blur 10 spread −5 @ 4% black · Drop `(0, 20)` blur 25 spread −5 @ 10% black                     |
| `Pretty Shadows/100`     | Drop `(0, 25)` blur 50 spread −12 @ 25% black                                                                  |
| `Pretty Shadows/101`     | Drop `(0, 0)` blur 0 spread 3 @ 60% `rgb(66,153,225)` *(focus-ring blue)*                                      |
| `Pretty Shadows/104`     | Drop `(0, 1)` blur 2 @ 5% black · *(plus 2 transparent layers — effectively `Pretty Shadows/96` lite)*         |
| `Filter Shadow`          | Drop `(0, 4)` blur 6 spread −2 @ 3% `rgba(16,24,40)` · Drop `(0, 12)` blur 16 spread −4 @ 8% `rgba(16,24,40)`  |

### 2.1 Recommended bindings

| Surface                            | Shadow                |
| ---------------------------------- | --------------------- |
| Card / panel rest                  | `Pretty Shadows/96`   |
| Card / panel hover                 | `Pretty Shadows/97`   |
| Calendar popover                   | `Pretty Shadows/42`   |
| Dropdown menu                      | `Pretty Shadows/99`   |
| Toast notification                 | `Pretty Shadows/98`   |
| Focus ring                         | `Pretty Shadows/101`  |
| Filter popovers (right-side)       | `Filter Shadow`       |

`Pretty Shadows/97` is the same composition as the `Pretty Shadows/97` variable referenced from `base.md` — either source is canonical.

---

## 3. Component catalog

**Iron rule (restated):** the components below are the only ones available for web designs. Do not invent new components; do not import from elsewhere. For each component, the **matrix** lists the variant properties you can set; the **anatomy** describes the canonical default variant. Where deeper specs are needed (specific states, alternative variants), request a targeted re-extraction.

> **Notation in anatomy tables:** `pad` = `[top, right, bottom, left]` in px. `gap` = item-spacing in auto-layout. `radius` = corner radius in px (single number = all corners). Tokens shown like `Token/Name` resolve to `base.md` colours; tokens shown like `Pretty Shadows/97` resolve to §2.

### 3.1 Buttons

**Matrix** — 1 component set, 272 variants:

| Property      | Type           | Options                                                    |
| ------------- | -------------- | ---------------------------------------------------------- |
| Size          | Variant        | Small, Medium, Large, Extra Large                          |
| Type          | Variant        | Primary, Secondary, Tertiary, Quaternary, Action Button    |
| State         | Variant        | Default, Hover, Disable, While Pressed                     |
| Icon Left     | Variant        | True, False, NA                                            |
| Icon Right    | Variant        | True, False, NA                                            |
| Only Icon     | Variant        | True, False, N                                             |
| Text          | Text           | (default: "Button")                                        |
| Leading Icon  | Instance swap  | any `icon/*`                                               |
| Trailing Icon | Instance swap  | any `icon/*`                                               |
| Choose Icon   | Instance swap  | any `icon/*` (only-icon variant)                           |

**Anatomy — default (`Size=Small, Type=Quaternary, State=Default`):**

- Frame: 90 × 32, layout `HORIZONTAL`, `pad [4, 14, 4, 14]`, `gap 0`, `align CENTER/CENTER`, `radius 8`.
- Text child: text style `Desktop/Body/Small/Medium`, fill `Brand/Gray/highContrast/700` (= `#FFFFFF`).

**Sizing rule of thumb:** all sizes share `radius 8`; vertical padding scales 4 → ~10, horizontal padding scales 14 → ~24 with size. *(For full per-size anatomy, request a targeted re-extraction.)*

### 3.2 Input Fields (Text field family)

**Sets on the Input Fields page** — 7 component sets + 4 standalone components.

| Set                  | Variants | Key variant props                                                                                      |
| -------------------- | -------- | ------------------------------------------------------------------------------------------------------ |
| `_Text field`        | 192      | State `Enabled/Disabled/Error`, Text-Config `Placeholder/Input`, Size `Small/Large/Extra Small/Extra Large`, Alignment `Top/Left`, Password? `True/False`, Focused? `No/Yes` |
| `_pills_Text field`  | 192      | Same axes as above; pills/badge presence baked in                                                      |
| `_+x, pills_Text field` | 192   | Same axes; with `+x more` overflow indicator                                                           |
| `Input Text field`   | 5        | Property 1 `Default/pills/X More Pills/Disabled/x_pills (Disabled)`                                    |
| `_swticher_icon`     | 2        | `indian-rupee / percent`                                                                                |
| `_Trailing-Type`     | 2        | Type `Trailing Icon / Switcher`                                                                         |
| `Scroll bar`         | 1        | Default                                                                                                 |
| **Standalones:** `Pills`, `Pills- Disabled`, `x_Pills`, `x_Pills - Disabled` |

Common booleans across the text-field sets: `Badge?`, `info Tooltip?`, `Label?` (default true), `Compulsory?`, `Show Leading Icon`, `Show Supporting Text`, `Show Trailing?`, `Prefix`.

**Anatomy — `_Text field` default (`Size=Small, State=Enabled, Placeholder, Alignment=Top, Focused=No`):**

- Outer frame: 270 × 59, layout `VERTICAL`, `gap 6`.
- Label row (top, `Frame 11808585`): 32 × 15 — text style `Desktop/Body/Small/Medium`, fill `Neutral/Content` for label, fill `Primary/Brand` (= brand red) for the `*` (compulsory marker).
- Input frame: 270 × 38, layout `HORIZONTAL`, `pad [0, 0, 0, 12]`, `gap 8`, `align SPACE_BETWEEN/CENTER`, `radius 8`, fill `Neutral/White`, stroke `Neutral/Stroke` (1px).
- Supporting text row: 270 × 18.

**Anatomy — `_pills_Text field` default:** larger 270 × 95 outer frame (vertical layout), input frame `pad [10.5, 16, 10.5, 16]`, same `radius 8` / fill `Neutral/White` / stroke `Neutral/Stroke`.

**POS Input** (separate page) — see §3.3.

### 3.3 Input field for POS

**Matrix** — 1 set, 3 variants:

| Property   | Options                       |
| ---------- | ----------------------------- |
| Property 1 | Default, Variant2, Variant3   |
| Place Holder (Text) | default: "Place Holder" |

**Anatomy — `Default`:**

- Outer: 370 × 73, layout `VERTICAL`, `gap 4`.
- Label: text style **`Mobile/Body/Medium/Semibold`** ⚠️ — POS Input uses **Mobile** text styles even on a web surface. Fill `Neutral/Content`.
- Container: 370 × 52, layout `HORIZONTAL`, `pad [16, 16, 16, 16]`, `align SPACE_BETWEEN/CENTER`, `radius 8`, fill `Brand/Light/100`.
- Placeholder: text style `Mobile/Body/Medium/Regular`, fill `Neutral/Sub Content`.
- Trailing: `icon/chevron-down` 20 × 20.

> **Drift flag (file bug):** POS Input is on a Desktop/web file but binds to `Mobile/*` text styles. Use as-is in POS billing contexts; raise if encountered elsewhere.

### 3.4 Modal / Popups

**Sets** — 6 sets + 1 standalone `_Modal action-3`.

| Set                | Variants | Variant props                                                                                  |
| ------------------ | -------- | ---------------------------------------------------------------------------------------------- |
| `Modal/Popup`      | 9        | Type `Pop Alert/With Form/Custom Content/Confirmation`, With Photo? `True/False`, With Carousel? `True/False` |
| `_Modal header`    | 3        | Don't Change- Type `Left aligned/Center aligned/Horizontal left aligned`                       |
| `_Featured icon`   | 24       | Type `Success/Warning/Save/Delete/Info/Custom icon`, Size `lg/md/sm/xs`                        |
| `_Modal action-1`  | 2        | Destructive `True/False`                                                                       |
| `_Modal action-2`  | 1        | Type `Horizontal fill container`                                                               |
| `_Modal actions`   | 12       | Type `Vertical / Horizontal fill / Horizontal right (checkbox)`, Destructive, Breakpoint `Desktop/Mobile` |

**Anatomy — `Modal/Popup` default (`With Form/Custom Content`):**

- Page frame: 1440 × 1024, fill `#192839 @ 50%` (page-dim overlay; equivalent to `Neutral/Text` at 50%).
- Modal frame: **640 × variable**, layout `VERTICAL`, `radius 12`, fill `Base / White` (library), effect `Shadow / xl` (library).
- Children: `_Modal header` → `Frame 1` (form area, `pad [24, 0, 0, 0]`, `gap 8`) → `_Modal action-1` footer.

**Anatomy — `_Modal header` (`Left aligned`):**

- 400 × 175, layout `VERTICAL`, fill `Base / White` (library).
- Content area: `pad [24, 24, 0, 24]`, `gap 16`.
- Close button: 44 × 44, `radius 8`, contains `x-close` icon 24 × 24.
- Divider: 1 px, fill `Gray/200` (library).

**Anatomy — `_Featured icon` default (`Success, xs`):**

- 24 × 24, `radius 4`, fill `Base/White`, stroke `Gray/200` (library, 1px), effect `Shadow/xs` (library).
- Inner icon: 12 × 12 `check-circle`, stroke `Success / 600` (library).

**Anatomy — `_Modal actions` default (`Vertical fill container, Destructive=False, Desktop`):**

- 560 × 181, layout `VERTICAL`, `pad [32, 0, 0, 0]`.
- Divider: 1 px, fill `Gray/200` (library).
- Content area: `pad [0, 24, 24, 24]`, `gap 12`, layout `VERTICAL`.
- Primary button row: 512 × 44, `pad [10, 18, 10, 18]`, `radius 8`, fill `Primary / 600` (library), stroke `Primary / 600`, effect `Shadow / xs`.
- Secondary button: same size, fill `Base / White`, stroke `Gray / 300` (library), effect `Shadow / xs`.

> **Drift flag:** Modal uses tokens from an **imported library** (`Base / White`, `Gray / 200`, `Primary / 600`, `Shadow / xs`, `Shadow / xl`) that are NOT in `base.md`. When implementing modals, treat the imported names as equivalent to `Neutral/White`, `Neutral/Stroke`, `Brand/Primary` / `Brand/Dark/600`, and a small/large drop-shadow respectively — and surface the mismatch to design.

### 3.5 Table

**Sets** — 19 component sets + 5 standalone (Status, _Before, _After, Text-and-Icon based, Input/Icon Based).

| Set                                | Variants | Variant props                                                                  |
| ---------------------------------- | -------- | ------------------------------------------------------------------------------ |
| `Table Cell - Text Based`          | 5        | Type `Text/Date/Date & Time/Double Line Text/Numbers`                          |
| `Table Cell - Icon Based`          | 2        | Line `Single/Double`                                                           |
| `Table Cell - Checkbox`            | 1        | Single line                                                                    |
| `Table Cell - Star`                | 4        | Type `Empty/Type2/Type3/Type4`                                                 |
| `Table Cell - Toggle`              | 1        | Single line                                                                    |
| `Table Cell - Tick Untick`         | 2        | Line `Single/Line2`                                                            |
| `Table Cell - Image Based`         | 2        | Type `With Out Description/With Description`                                   |
| `Table Cell - Upload`              | 3        | Type `Uploaded/Change/Upload`                                                  |
| `Table Cell - Badge`               | 13       | Type `Sucess (sic) with MD / Sucess / Reviewed / Reviewed Draft / Duplicate / Rejected / Failed / Processing 1 / Uploaded / Type11 / Uploading / Failed + Icon / Discount` |
| `Table Cell - Action Buttons`      | 1        | Property 1 `Icon Based`                                                        |
| `Table Cell - Special Input Field` | 10       | Type `Normal/With Chev Hover/With Chev/Normal Hover/Normal_Num_hover/Normal_Num/Type7/Active Normal/Active Hover/Type10` |
| `Head Cell - Sort`                 | 4        | State `Inactive/Active`, Asc/Dsc `DSC/ASC`                                     |
| `Head Cell Numbers - Sort`         | 4        | Same                                                                            |
| `Head Cell - Edit`                 | 2        | State `Head Cell - Filter`, Active? `Opened/Closed`                            |
| `Head Cell - Checkbox`             | 1        | Filter State `Closed`, Active? `Yes`                                           |
| `Head Cell - Sort Updated`         | 2        | State `Inactive/Active`                                                        |
| `Head Cell - Filter`               | 3        | State `Inactive/Active/Opened`                                                 |
| `Favourites`                       | 3        | State `Hover/Default/Added`                                                    |
| `State`                            | 5        | State `False Positive/Pending Review/Confirmed Fraud/Under investigation/Default` (used as cell status dot) |

**Common cell anatomy** (data cells — Text, Icon, Checkbox, Star, Toggle, Tick Untick, Image, Upload):

- Outer: variable width × 56, layout `VERTICAL`.
- `Cell Content` row: `pad [13, 10, 13, 10]` (some cells use `[7, 10, 7, 10]` or `[16, 10, 16, 10]`), `gap 8`, `align MIN/CENTER`, fill `Neutral/White` (or `#FFFFFF`).
- Bottom border: 1px rectangle, fill `Neutral/Stroke`.

**Common head-cell anatomy** (Sort, Numbers Sort, Edit, Checkbox, Sort Updated, Filter):

- Outer: variable width × 56, layout `VERTICAL`.
- `Cell Content` row: `pad [13, 10, 13, 10]`, `gap 8`, fill **`Brand/Light/100`** (`#F2F5F8`).
- Bottom border: 1px rectangle, fill `Neutral/Stroke`.

**Text style for data:** `Desktop/Body/Small/Regular`, fill `Neutral/Text`.

**State (status dot):** 8 × 8 ellipse, fill `Success/Content` for default; bind to `Success/Content`, `Error/Content`, `Warning/Content`, or `Prediction/Content` per state.

**Action buttons** (Before/After cells): 32 × 32 buttons, `radius 8`, fill `Brand/Gray/highContrast/700`, stroke `Neutral/Stroke` (1px), `pad [6, 6, 6, 6]`.

### 3.6 Navigation

#### 3.6.1 Side Nav

**Sets** — 5 sets.

| Set                | Variants | Variant props                                                                      |
| ------------------ | -------- | ---------------------------------------------------------------------------------- |
| `_Nav Text Item`   | 12       | Type `Open/Collapsed`, State `Inactive/Active/Hover/Expanded/Active Expanded/Active Solo Hover/Active Expanded Hover` |
| `_Nav_menu_item`   | 5        | State `Collapsed/Open`, Type `Inactive/Active/Hover`                               |
| `Nav Bar`          | 10       | Property 1 `Open/Inventory/Banking/Marketing/Purchase/Accountant/Settings/Variant9/Default/Sales` |
| `_Menu Item`       | 2        | Type `Default/Hover`, Icon bool                                                    |
| `_Menu Listing`    | 2        | Property 1 `With Title/Without Title`                                              |

**Anatomy — `Nav Bar` default (`Property 1=Variant9`):**

- 64 × 1024 (full-height left rail), layout `VERTICAL`, fill **`Brand/Primary`** (`#2E5391`).
- Contains 8 × `_Nav Text Item` instances, each 64 × 56 with `pad [4, 8, 4, 8]`, fill `Brand/Primary`.

**Anatomy — `_Nav Text Item` (`Collapsed, Active Solo Hover`):**

- 64 × 56, layout `VERTICAL`, `pad [4, 8, 4, 8]`, fill `Brand/Primary`.
- Content inner: 48 × 48, `pad [12, 12, 12, 12]`, `gap 16`, `radius 4`, fill `Neutral/White` (highlight bubble for active state).

**Anatomy — `_Nav_menu_item` (`Open, Inactive`):**

- 207 × 48, layout `HORIZONTAL`, `pad [12, 12, 12, 12]`, `gap 16`, `radius 4`, fill **`Brand/Dark/600`** (`#254A88`).
- Icon: 24 × 24.
- Label: text style `Desktop/Body/Large/Medium`, fill `Neutral/White`.
- Badge (optional): 20 × 20, `pad [2, 6, 2, 6]`, `radius 2000` (pill), fill `Banner red` (library token).

**Anatomy — `_Menu Item` (`Default`):**

- 176 × 40, layout `HORIZONTAL`, `pad [11, 8, 11, 8]`, `gap 105`, `radius 6`, fill `Brand/Dark/600`.
- Label: text style `Desktop/Body/Medium/Regular`, fill `Neutral/White`.
- Trailing icon: 16 × 16 `icon/plus`.

#### 3.6.2 Top Nav

**Standalone component** — `Top NavBar` (no variants).

**Anatomy:**

- 1440 × 64, layout `HORIZONTAL`, `pad [0, 20, 0, 88]`, `gap 1026` (effectively pushes left logo group and right action group to ends), fill `#FFFFFF`.
- Logo group (`Layer_1`): 112 × 37.
- Right group (`Frame 427319324`): 573 × 64, `gap 12`.

#### 3.6.3 Sub-Sidemenu

**Sets** — 1 set + 2 standalone (`Sub Side Menu`, `_Local`).

| Set         | Variants | Variant props |
| ----------- | -------- | ------------- |
| `_List_item`| 2        | State `Active/Inactive` |

**Anatomy — `_List_item` (`Inactive`):**

- 226 × 44, layout `VERTICAL`, `pad [0, 24, 0, 24]`.
- Content inner: 178 × 44, layout `HORIZONTAL`, `pad [12, 0, 12, 0]`, `gap 16`, `radius 4`.

**Anatomy — `Sub Side Menu`:** 270 × 997, layout `VERTICAL`, `gap 12`, fill `#FFFFFF`, stroke `Neutral/Stroke`, effect `Drawer` (library shadow).

#### 3.6.4 Tabs

**Sets** — 3 sets.

| Set            | Variants | Variant props                                                                          |
| -------------- | -------- | -------------------------------------------------------------------------------------- |
| `Tabs`         | 2        | Current `No/Yes`, Badge `Yes`, Badge? boolean, Error? boolean                          |
| `Filled Tab`   | 6        | Active `True/False`, State `Placeholder/Focus`, Type `Default/Badg/Icon only`, Style `Fill` |
| `Fill tab bar` | 2        | Style `Border`, Icon only `True/False`                                                 |

**Anatomy — `Tabs` (`Current=No, Badge=Yes`):**

- 100 × 35, layout `VERTICAL`.
- Content row: 98 × 33, layout `HORIZONTAL`, `pad [0, 16, 16, 16]`, `gap 4`.
- Bottom border: 100 × 2 rectangle.

**Anatomy — `Filled Tab` (`Active=False, State=Placeholder, Default, Fill`):**

- 85 × 40, layout `HORIZONTAL`, `pad [11.5, 24, 11.5, 24]`, `gap 4`.
- Label: text style `Desktop/Body/Medium/Medium`, fill `Neutral/Content`.

**Anatomy — `Fill tab bar` (`Border, Icon only=False`):**

- 466 × 52, layout `HORIZONTAL`, `pad [6, 6, 6, 6]`, `radius 8`, fill `Brand/Gray/lowContrast/a50` (= `#6C849D @ 12%`).

#### 3.6.5 Breadcrumbs (moved to active per user override)

> **Note on canonical status:** in the Figma file this lives on a page named `Breadcrumbs - Don't Use`. The user has overridden this and treats Breadcrumbs as an **active component**. When designs are exported back to Figma, this divergence should be resolved by renaming the page in Figma — until then, treat Breadcrumbs as active here.

**Sets** — 1 set + 1 standalone (`Breadcrumbs`).

| Set                       | Variants | Variant props                |
| ------------------------- | -------- | ---------------------------- |
| `_Breadcrumb button base` | 4        | Type `Icon/Text`, State `Active/Default` |

**Anatomy — `_Breadcrumb button base` (`Icon, Default`):**

- 20 × 20, layout `HORIZONTAL`.
- Contains a single 20 × 20 icon (default: `home`).

**Anatomy — `Breadcrumbs` (standalone bar):**

- 693 × 44, layout `VERTICAL`, `pad [12, 0, 12, 0]`, `gap 8`, stroke `Neutral/Stroke`.
- Inner `Tabs` frame: 693 × 20, layout `HORIZONTAL`, `pad [0, 0, 0, 8]`, `gap 12`.

### 3.7 Pagination

**Sets** — 3 sets + 1 standalone (`Pagination Strip`).

| Set                   | Variants | Variant props                                                                          |
| --------------------- | -------- | -------------------------------------------------------------------------------------- |
| `_Pagination_BUttons` | 5        | Property 1 `Frame 1410090391 / 92 / 93 / 94 / Variant5` *(naming is generic, treat as layout slots)* |
| `_Forward-Button`     | 2        | Property 1 `Default/Forward`                                                           |
| `_Backward-Button`    | 2        | Property 1 `Default/Backward`                                                          |

**Anatomy — `_Pagination_BUttons` default:**

- 368 × 32, layout `HORIZONTAL`, `gap 10`.
- Each button: 32 × 32, `pad [4, 14, 4, 14]` (inactive) or `[6, 6, 6, 6]` (icon-only chevrons), `radius 8`.
- Active page button: fill `Brand/Primary`.
- Trailing forward button: 32 × 32.

**Anatomy — `Pagination Strip` (standalone, full bar):**

- 1326 × 60, layout `HORIZONTAL`, `pad [12, 8, 12, 8]`, `gap 800` (pushes left summary text to one side, page buttons to the other), fill `#FFFFFF`.

### 3.8 Calendar

**Sets** — 3 sets + 1 standalone (`_calendarHeaderCell`).

| Set                  | Variants | Variant props                                                                                   |
| -------------------- | -------- | ----------------------------------------------------------------------------------------------- |
| `Date Range picker`  | 2        | Property 1 `clicked/Default`                                                                    |
| `_calenderCell`      | 18       | Type `Inactive/Active/Today`, Position `Leading/Trailing / Middle / Middle-Leading / Middle-Trailing`, State `Default/Disabled/Hover` |
| `Calendar`           | 2        | Variant `Default/Range`                                                                         |

**Anatomy — `Calendar` (`Default`):**

- 248 × 344, layout `VERTICAL`, `pad [12, 12, 12, 12]`, `gap 12`, `radius 6`, fill `Neutral/White`, stroke `Brand/Light/100` (1px), effect **`Pretty Shadows/42`**.
- Header row: 224 × 36, layout `HORIZONTAL`.
- Days grid: 224 × 272, layout `VERTICAL`, `gap 8`.

**Anatomy — `_calenderCell` (`Inactive, Leading/Trailing, Default`):**

- 32 × 32, layout `VERTICAL`, `pad [5, 11, 5, 11]`, `gap 10`, `radius 6`, fill `Neutral/White`.
- Number: text style `Desktop/Body/Medium/Regular`, fill `Neutral/Text`.

**Anatomy — `_calendarHeaderCell` (day-of-week labels):**

- 32 × 32, same layout, label text style `Desktop/Body/Small/Regular`, fill `Neutral/Sub Content`.

**Anatomy — `Date Range picker` (`clicked`):**

- 302 × 38 input field on top.
- Popover: 724 × 508, `radius 8`, stroke `Brand/Light/100`, effect `Pretty Shadows/42`.

### 3.9 Checkboxes (covers Checkboxes + Radio Buttons)

**Sets** — 2 sets, 42 variants each.

| Set            | Variants | Variant props                                                                  |
| -------------- | -------- | ------------------------------------------------------------------------------ |
| `Checkboxes`   | 42       | Size `Small/Medium`, State `Default/Hover/Focused/Disabled`, Checked `No/Yes`, With Text `Yes/No`, Support Text `No/Yes` |
| `Radio Buttons`| 42       | Same axes as above, but `Selected` instead of `Checked`                        |

**Anatomy — `Checkboxes` default (`Small, Default, No, No, No`):**

- 16 × 16 outer, layout `HORIZONTAL`.
- `_Checkbox base`: 16 × 16, **`radius 4`**, fill `Neutral/White`, stroke `Neutral/Stroke` (1px).

**Anatomy — `Radio Buttons` default (`Small, Default, No, No, No`):**

- 16 × 16 outer, layout `HORIZONTAL`.
- `_Checkbox base`: 16 × 16, **`radius 8`** (full circle), fill `Neutral/White`, stroke `Neutral/Stroke` (1px).

> **Only difference between Checkbox and Radio at the base level is the corner radius** (4 vs 8).

### 3.10 Badges

**Sets** — 2 sets.

| Set         | Variants | Variant props                                              |
| ----------- | -------- | ---------------------------------------------------------- |
| `Badges`    | 7        | Type `Red/Blue/Green/Purple/Yellow/Teal/Default`; Leading Icon / Trailing Icon booleans |
| `Icon Badge`| 2        | State `Up/Down`                                            |

**Anatomy — `Badges` default (`Red`):**

- 170 × 24, layout `HORIZONTAL`, `pad [4, 12, 4, 12]`, `gap 4`, `radius 72` (effectively pill — width-dependent), fill `Error/BG` (for Red).

Per-type fill mapping (inferred from naming):
- Red → `Error/BG` + `Error/Header` text
- Green → `Success/BG` + `Success/Header` text
- Blue → `Prediction/BG` + `Prediction/Header` text
- Yellow → `Warning/BG` + `Warning/Header` text
- Purple / Teal / Default → flagged for re-extraction (no explicit base.md token mapping)

**Anatomy — `Icon Badge` (`Up`):**

- 20 × 20, layout `HORIZONTAL`, `pad [4, 4, 4, 4]`, `gap 4`, `radius 16` (full circle).
- Fill `Success/BG`.
- Inner: 12 × 12 `icon/arrow-up`.

### 3.11 Toggle

**Sets** — 3 sets.

| Set              | Variants | Variant props                                                                                   |
| ---------------- | -------- | ----------------------------------------------------------------------------------------------- |
| `Toggle`         | 60       | Size `Small`, State `Default/Focused/Disable`, Status `Off/On`, Icon `Yes/No`, With Text `Yes Left/No/Yes Right`, Support Text `No/Yes` |
| `Option`         | 3        | State `Default/hover/active`; Show icon boolean                                                 |
| `OptionSwitcher` | 1+       | Default                                                                                          |

**Anatomy — `Toggle` (`Small, Default, On, No, No, No`):**

- 36 × 20, the inner `Toggle_selected_icon` frame is 36 × 20 (VERTICAL layout).

**Anatomy — `OptionSwitcher` (`Default`):** segmented control bar.

- 260 × 34, layout `HORIZONTAL`, `pad [4, 4, 4, 4]`, `gap 4`, `radius 8`, fill `Neutral/White`, stroke `Neutral/Stroke` (1px).
- Each `Option` segment: ~80 × 26, layout `HORIZONTAL`, `pad [8, 16, 8, 16]`, `gap 10`, `radius 8`.

### 3.12 Dropdowns (menu + dropdown list)

**Sets** — 6 sets + 3+ standalone (CRM-1, _Org-Section-1/2/3, Badges, etc.)

| Set                         | Variants | Variant props                                                                       |
| --------------------------- | -------- | ----------------------------------------------------------------------------------- |
| `dropdown menu`             | 4        | Type `Org Switcher/Normal/Checkboxes/Customer profile`; Search bar?, Add New? booleans |
| `menu item`                 | 17       | Type `Menu Item/Sub Menu Item/header`, State `default/hover/disabled/Selected`, Size `Large/Small`; left/right icon, right text, Star?, Outled ID Badge? booleans |
| `menu item - with badge`    | 17       | Same axes as above                                                                  |
| `Menu List items`           | 2        | Type `Normal/Checkbox`; Scrollbar?, Add New? booleans                               |
| `Menu List items - with badge` | 1     | Type `Normal`                                                                       |
| `Star`                      | 3        | Type `Type2/Type3/Type4`                                                            |

**Anatomy — `dropdown menu` (`Org Switcher`):**

- 344 × 708, layout `VERTICAL`, `radius 6`, effect **`Pretty Shadows/99`**.
- Section: 344 × 708, fill `#FFFFFF`.

**Anatomy — `menu item` (`Menu Item, default, Small`):**

- 236 × 32, layout `HORIZONTAL`, `pad [6, 8, 6, 8]`, `gap 8`, fill `#FFFFFF`.
- Right-text label `⌘⇧B` etc.: text style `detail` (library), fill `slate/500` (library).

> **Drift flag:** dropdowns reference `detail` text style and `slate/500` colour from an imported library, not `base.md`. Map to `Desktop/Caption/SmallRegular` + `Neutral/Sub Content` when implementing in code; surface the divergence.

**Anatomy — `Menu List items - with badge` (`Normal`):**

- 236 × 288, layout `VERTICAL`, `pad [8, 8, 8, 8]`, `gap 8`, fill `#FFFFFF`.
- Selected item highlight: `radius 6`, fill **`Brand/Light/100`**.

### 3.13 Tooltip

**Set** — 1 set, 6 variants.

| Property | Options                                                  |
| -------- | -------------------------------------------------------- |
| Position | Center, Left, Right, Position Left, Position Right, Bottom |

**Anatomy — `Tooltip` (`Center`):**

- 282 × 59, layout `VERTICAL`, `gap −6` (caret overlaps the body intentionally).
- Caret frame: 43 × 13.
- Body: 282 × 52, layout `HORIZONTAL`, `pad [6, 6, 6, 6]`, `gap 10`, `radius 5`, fill **`Neutral/Text`** (`#192839`).

### 3.14 Toaster (Toast Notification)

**Set** — 1 set, 5 variants.

| Property      | Options                                  |
| ------------- | ---------------------------------------- |
| Type          | Sucess (sic), Info, Error, Warning, Neutral |
| Sub Text      | boolean (default true)                   |
| Manual Close? | boolean                                  |
| Action?       | boolean                                  |

**Anatomy — `Toast Notification` (`Sucess`):**

- 411 × 66, layout `HORIZONTAL`, `pad [16, 40, 16, 16]`, `gap 9`, `radius 8`, fill `#EFFDF3` *(close to `Success/BG` `#ECFDF3` — flag drift)*, effect **`Pretty Shadows/98`**.
- Icon: 24 × 24 `circle-check`.
- Text stack: 322 × 34, layout `VERTICAL`, `gap 2`.
- Close button: 18 × 18, `pad [2.25, 2.25, 2.25, 2.25]`, `radius 27` (full circle), fill `#FFFFFF`, stroke `Neutral/Stroke` (0.5625 px).
- Action button: 68 × 24, `radius 4`, fill `Neutral/Text`.

Per-type colour mapping (inferred):
- Sucess → `Success/BG`-adjacent
- Info → `Prediction/BG`
- Error → `Error/BG`
- Warning → `Warning/BG`
- Neutral → `Neutral/Grey 2`

### 3.15 Side Drawers

**Set** — 1 set + 3 standalone (`_SPL Drawer Content`, `_Drawer Content`, `Add Party`).

| Set          | Variants | Variant props                                                            |
| ------------ | -------- | ------------------------------------------------------------------------ |
| `Side Drawer`| 4        | Type `Normal/Special`, Supporting Text `True/False`; Back Button?, Single Button, Show Cancel Button, Show Price booleans |

**Anatomy — `Side Drawer` (`Normal, Supporting Text=False`):**

- 518 × 1024, layout `VERTICAL`, fill `Neutral/White`.
- Header frame: 518 × 76, layout `HORIZONTAL`, `pad [26, 32, 26, 32]`, fill `Brand/Light/200`.
- Body: 518 × 876, `pad [24, 32, 24, 32]`, `gap 10`.
- Footer frame (two variants — single or split): 518 × 72, `pad [17, 32, 17, 32]`, fill `Brand/Light/200`.

### 3.16 Loaders

**Set** — 1 set, 4 variants.

| Property   | Options       |
| ---------- | ------------- |
| Property 1 | 1, 2, 3, 4    |

**Anatomy — `Spinner-Round/Spinner-Round-05`:**

- 22 × 22, contains two overlapping 17 × 17 ellipses (one track + one indicator).

### 3.17 Stepper / Horizontal Progress Bar

**Sets** — 2 sets + 1 standalone (`Horizontal Progress bar`).

| Set                              | Variants | Variant props                                                  |
| -------------------------------- | -------- | -------------------------------------------------------------- |
| `Progress bar Local component`   | 3        | Property 1 `Active/Disabled/Success`; Hide Subtext / Text / Divider booleans |
| `States` (step indicator dot)    | 9        | Type `Icon/Number/Tick`, State `Success/Disabled/Active`       |

**Anatomy — `States` (`Number, Success`):**

- 25 × 25, layout `VERTICAL`, `pad [10, 10, 10, 10]`, `gap 10`, `radius 99` (full circle), fill `Success/Content`.
- Number text: style `Desktop/Body/Small/Semibold`, fill `Neutral/White`.

**Anatomy — `Progress bar Local component` (`Active`):**

- 159 × 60, layout `HORIZONTAL`, `gap 8`.
- Step indicator wrapper: 101 × 60, `pad [12, 0, 12, 0]`, `gap 12`.
- Connecting line: 50 × 0 (LINE node), stroke `Neutral/Disabled`, weight 2.

**Anatomy — `Horizontal Progress bar` (standalone, full row):**

- 954 × 60, layout `HORIZONTAL`, contains 6 `Progress bar Local component` instances.

### 3.18 Slider / Range

**Standalone components** — 2: `Slider / Range` and `Slider / Value`.

**Anatomy — `Slider / Range`:**

- 256 × 8, `radius 4`, fill `Brand/Light/300`.
- Selected range frame: 135 × 8 inside.

**Anatomy — `Slider / Value`:**

- 256 × 8, `radius 4`, fill `Brand/Light/300`.
- Inner value frame: 83 × 8, `radius 4`, fill **`Brand/Primary`**.

### 3.19 Filters

**Standalone components** — 2: `Filter`, `Date & Time`.

**Anatomy — `Filter`:**

- 252 × 330, layout `VERTICAL`, `gap 21`, `radius 8`, fill `#FFFFFF`, effect **`Filter Shadow`**.

**Anatomy — `Date & Time`:**

- 406 × 386, layout `VERTICAL`, `radius 12`, fill `Neutral/White`, stroke `Neutral/Stroke` (1px), effect **`Filter Shadow`**.
- Header row: 406 × 56.
- Body: 406 × 268, stroke `Neutral/Stroke` (separator).
- Footer: 406 × 62, `pad [12, 12, 12, 12]`.

### 3.20 POS Billing Screen

POS-specific composite components.

**Sets** — 3 sets.

| Set            | Variants | Variant props                                                                              |
| -------------- | -------- | ------------------------------------------------------------------------------------------ |
| `Cart Items`   | 3        | State `Default/Expanded/with variant`; Product Name text                                   |
| `Cart Section` | 6        | State `Empty State/Items added Closed/Charges Open/Empty with item/empty with charges open/combo`; Show Price list boolean |
| `Item Listing` | 3        | Property 1 `Default/combo/variant`                                                         |

**Anatomy — `Cart Items` (`Default`):**

- 642 × 56, layout `VERTICAL`, `gap 12`, fill `#FFFFFF`.
- Row: 642 × 56, `radius 8`, fill `Neutral/White`.

**Anatomy — `Cart Section` (`Items added Closed`):**

- 666 × 953, fill `Neutral/White`.
- Top strip: 666 × 40, fill `Neutral/Background`.
- Item row container: 666 × 62, `pad [12, 12, 12, 12]`, fill `Neutral/White`, stroke `Brand/Light/200`.
- Footer separator: 666 × 50, stroke `Neutral/Stroke`.

**Anatomy — `Item Listing` (`Default`):**

- 130 × 88, layout `VERTICAL`, `pad [8, 8, 8, 8]`, `gap 8`, `radius 8`, fill `Neutral/White`, stroke `Brand/Light/100` (1px).
- Product name: text style applied, fill `Neutral/Text`.
- Accent bar: 56 × 2, fill `Prediction/Content`.

### 3.21 POS Header

**Set** — 1 set, 3 variants.

| Property | Options                |
| -------- | ---------------------- |
| State    | Login, Day End, Default |

**Anatomy — `POS Header` (`Login`):**

- 1440 × 75, layout `HORIZONTAL`, `pad [16, 32, 16, 32]`, `gap 1029` (spreads logo group left and action group right), fill `Neutral/White`, stroke `Neutral/Stroke`.
- Inner content frame: 1376 × 43.

### 3.22 Illustrations

Page exists with 2 raster illustrations (not COMPONENTs in Figma's component-system sense — they are static frames containing images). When a design calls for an illustration, **use exactly the assets on this page** by reference (e.g. "the welcome illustration from Web Guidelines / Illustrations"). Do not generate or substitute.

### 3.23 Icons

The Web Guidelines file ships **2,422 icon components** on the `Icons` page (`4:29`). **This file contains TWO distinct icon sets coexisting on the same page** — see §3.23.1.

#### 3.23.1 Two icon sets — read this first

| Set | Count | Naming | Era | Status |
|-----|------:|--------|-----|--------|
| **Legacy** | ~837 | `icon/{kebab-case}` (e.g. `icon/arrow-up`) | Older Lucide release | Still present; many duplicates of the modern set |
| **Modern** | ~1,565 | `{kebab-case}` (no prefix, e.g. `arrow-up`) | Newer Lucide release with ~700+ additional glyphs | **Preferred for new work** |
| **Petpooja-specific** | ~20 | Mixed (some `icon/`-prefixed, some not, some with spaces) | n/a | Use as-is; can't substitute |

> **Rule of thumb:** for any new design, **use the modern (prefix-less) set** — it has more glyphs and matches the latest Lucide naming. Only use the legacy `icon/*` set when modifying an existing screen that already references it.
>
> Both sets share ~824 names — when you find a glyph in both forms (e.g. `arrow-up` and `icon/arrow-up`), prefer the prefix-less one and migrate references as you touch them.

#### 3.23.2 Naming & usage rules

1. **Reference icons by their exact Figma name.** Modern: `arrow-up`. Legacy: `icon/arrow-up`. Petpooja-specific: literal name as it appears (e.g. `Cash Drawer 1`, `Payment In`, `icon/GST`).
2. **Default icon size by host component:**
   - Status Bar (n/a — mobile only)
   - Side Nav: 24 px
   - Top Nav action buttons: 24 px
   - Buttons (Small / Medium): 16 px; (Large / XL): 20 px
   - Inputs leading / trailing: 16 px
   - Modal close (`x-close`): 24 px
   - Modal Featured icon: 12 px (xs) / 16 (sm) / 20 (md) / 24 (lg)
   - Toaster: 24 px
   - Table action buttons: 16 px
3. **Icons are stroked, not filled.** The outer `icon/*` or `name` component fill defaults to `#FFFFFF` (transparent in render); the inner vectors use `stroke` bound to the parent's text/icon role colour (`Neutral/Text`, `Neutral/White`, `Brand/Primary`, etc.).
4. **Stroke weight on icon vectors: `1.5 px`** (verified across multiple icons).
5. **If a needed icon is not in either catalog below, stop and ask.** Do not draw, do not import.

#### 3.23.3 Petpooja-specific icons (canonical — use exact names)

Glyphs unique to the Petpooja system, with the exact name as it appears in Figma:

| Name (verbatim)      | Probable use                                      |
| -------------------- | ------------------------------------------------- |
| `icon/GST`           | GST tax indicator                                 |
| `icon/Tax-k`         | Tax-related glyph                                 |
| `icon/Link`          | Link / chain (custom Petpooja variant)            |
| `icon/Support`       | Customer support                                  |
| `icon/E-way Bill`    | E-way Bill (with space; logistics)                |
| `icon/E Bill`        | E-Bill (with space)                               |
| `icon/drawer`        | Cash drawer                                       |
| `icon/Loyalty`       | Loyalty programme                                 |
| `icon/Gift`          | Gift / promotion                                  |
| `icon/user-star`     | Favourite / starred user                          |
| `icon/notebook 1`    | Notebook (file-bug suffix " 1")                   |
| `Cash Drawer 1`      | Cash drawer (alternate; file-bug suffix " 1")     |
| `Expense`            | Expense entry                                     |
| `Withdrawal`         | Cash withdrawal                                   |
| `Cash_Topup`         | Cash top-up                                       |
| `anniversary`        | Anniversary marker                                |
| `Birthday`           | Birthday marker                                   |
| `column configure`   | Table column configuration (with space)           |
| `Update details`     | Generic "update details" CTA glyph (with space)   |
| `Text`               | Text format glyph                                 |
| `duplicate`          | Duplicate / clone                                 |
| `What's New`         | "What's New" banner glyph                         |
| `What's new`         | Duplicate of above with different casing — file bug |
| `Marketing (1) `     | Marketing (with trailing space and `(1)` — file bug) |
| `Store-outlet`       | Store / outlet marker                             |
| `Placeholder image`  | Placeholder for missing image                     |
| `blocks-integration` | Integration / API connector glyph                 |
| `whatsapp`           | WhatsApp brand (appears twice on the page — file dup) |
| `star-07`            | Decorative star variant 7                         |
| `star-08`            | Decorative star variant 8                         |
| `tool-02`            | Tools / wrench (file-bug — missing `icon/` prefix) |
| `day-end`            | POS day-end marker                                |

> Several of these have file bugs (trailing spaces, version-number suffixes, casing inconsistencies). Reproduce the **exact name** when referencing — do not normalise.

#### 3.23.4 Modern set (prefix-less) — full alphabetical catalog (~1,565 icons)

This is the **preferred set for new work**. Names match Lucide v0.300+ naming. Search with `Cmd+F` / `Ctrl+F`.

**A**
`a-arrow-down`, `a-arrow-up`, `a-large-small`, `accessibility`, `activity`, `air-vent`, `airplay`, `alarm-clock`, `alarm-clock-check`, `alarm-clock-minus`, `alarm-clock-off`, `alarm-clock-plus`, `alarm-smoke`, `album`, `align-center`, `align-center-horizontal`, `align-center-vertical`, `align-end-horizontal`, `align-end-vertical`, `align-horizontal-distribute-center`, `align-horizontal-distribute-end`, `align-horizontal-distribute-start`, `align-horizontal-justify-center`, `align-horizontal-justify-end`, `align-horizontal-justify-start`, `align-horizontal-space-around`, `align-horizontal-space-between`, `align-justify`, `align-left`, `align-right`, `align-start-horizontal`, `align-start-vertical`, `align-vertical-distribute-center`, `align-vertical-distribute-end`, `align-vertical-distribute-start`, `align-vertical-justify-center`, `align-vertical-justify-end`, `align-vertical-justify-start`, `align-vertical-space-around`, `align-vertical-space-between`, `ambulance`, `ampersand`, `ampersands`, `anchor`, `angry`, `annoyed`, `antenna`, `anvil`, `aperture`, `app-window`, `app-window-mac`, `apple`, `archive`, `archive-restore`, `archive-x`, `armchair`, `arrow-big-down`, `arrow-big-down-dash`, `arrow-big-left`, `arrow-big-left-dash`, `arrow-big-right`, `arrow-big-right-dash`, `arrow-big-up`, `arrow-big-up-dash`, `arrow-down`, `arrow-down-0-1`, `arrow-down-1-0`, `arrow-down-a-z`, `arrow-down-from-line`, `arrow-down-left`, `arrow-down-narrow-wide`, `arrow-down-right`, `arrow-down-to-dot`, `arrow-down-to-line`, `arrow-down-up`, `arrow-down-wide-narrow`, `arrow-down-z-a`, `arrow-left`, `arrow-left-from-line`, `arrow-left-right`, `arrow-left-to-line`, `arrow-right`, `arrow-right-from-line`, `arrow-right-left`, `arrow-right-to-line`, `arrow-up`, `arrow-up-0-1`, `arrow-up-1-0`, `arrow-up-a-z`, `arrow-up-down`, `arrow-up-from-dot`, `arrow-up-from-line`, `arrow-up-left`, `arrow-up-narrow-wide`, `arrow-up-right`, `arrow-up-to-line`, `arrow-up-wide-narrow`, `arrow-up-z-a`, `arrows-up-from-line`, `asterisk`, `at-sign`, `atom`, `audio-lines`, `audio-waveform`, `award`, `axe`, `axis-3d`

**B**
`baby`, `backpack`, `badge`, `badge-alert`, `badge-cent`, `badge-check`, `badge-dollar-sign`, `badge-euro`, `badge-help`, `badge-indian-rupee`, `badge-info`, `badge-japanese-yen`, `badge-minus`, `badge-percent`, `badge-plus`, `badge-pound-sterling`, `badge-russian-ruble`, `badge-swiss-franc`, `badge-x`, `baggage-claim`, `ban`, `banana`, `banknote`, `barcode`, `baseline`, `bath`, `battery`, `battery-charging`, `battery-full`, `battery-low`, `battery-medium`, `battery-warning`, `beaker`, `bean`, `bean-off`, `bed`, `bed-double`, `bed-single`, `beef`, `beer`, `beer-off`, `bell`, `bell-dot`, `bell-electric`, `bell-minus`, `bell-off`, `bell-plus`, `bell-ring`, `between-horizontal-end`, `between-horizontal-start`, `between-vertical-end`, `between-vertical-start`, `biceps-flexed`, `bike`, `binary`, `biohazard`, `bird`, `bitcoin`, `blend`, `blinds`, `blocks`, `bluetooth`, `bluetooth-connected`, `bluetooth-off`, `bluetooth-searching`, `bold`, `bolt`, `bomb`, `bone`, `book`, `book-a`, `book-audio`, `book-check`, `book-copy`, `book-dashed`, `book-down`, `book-headphones`, `book-heart`, `book-image`, `book-key`, `book-lock`, `book-marked`, `book-minus`, `book-open`, `book-open-check`, `book-open-text`, `book-plus`, `book-text`, `book-type`, `book-up`, `book-up-2`, `book-user`, `book-x`, `bookmark`, `bookmark-check`, `bookmark-minus`, `bookmark-plus`, `bookmark-x`, `boom-box`, `bot`, `bot-message-square`, `bot-off`, `box`, `box-select`, `boxes`, `braces`, `brackets`, `brain`, `brain-circuit`, `brain-cog`, `brick-wall`, `briefcase`, `briefcase-business`, `briefcase-medical`, `bring-to-front`, `brush`, `bug`, `bug-off`, `bug-play`, `building`, `building-2`, `bus`, `bus-front`

**C**
`cable`, `cable-car`, `cake`, `cake-slice`, `calculator`, `calendar`, `calendar-arrow-down`, `calendar-arrow-up`, `calendar-check`, `calendar-check-2`, `calendar-clock`, `calendar-cog`, `calendar-days`, `calendar-fold`, `calendar-heart`, `calendar-minus`, `calendar-minus-2`, `calendar-off`, `calendar-plus`, `calendar-plus-2`, `calendar-range`, `calendar-search`, `calendar-x`, `calendar-x-2`, `camera`, `camera-off`, `candy`, `candy-cane`, `candy-off`, `cannabis`, `captions`, `captions-off`, `car`, `car-front`, `car-taxi-front`, `caravan`, `carrot`, `case-lower`, `case-sensitive`, `case-upper`, `cassette-tape`, `cast`, `castle`, `cat`, `cctv`, `chart-area`, `chart-bar`, `chart-bar-big`, `chart-bar-decreasing`, `chart-bar-increasing`, `chart-bar-stacked`, `chart-candlestick`, `chart-column`, `chart-column-big`, `chart-column-decreasing`, `chart-column-increasing`, `chart-column-stacked`, `chart-line`, `chart-network`, `chart-no-axes-column`, `chart-no-axes-column-decreasing`, `chart-no-axes-column-increasing`, `chart-no-axes-combined`, `chart-no-axes-gantt`, `chart-pie`, `chart-scatter`, `chart-spline`, `check`, `check-check`, `chef-hat`, `cherry`, `chevron-down`, `chevron-first`, `chevron-last`, `chevron-left`, `chevron-right`, `chevron-up`, `chevrons-down`, `chevrons-down-up`, `chevrons-left`, `chevrons-left-right`, `chevrons-right`, `chevrons-right-left`, `chevrons-up`, `chevrons-up-down`, `chrome`, `church`, `cigarette`, `cigarette-off`, `circle`, `circle-alert`, `circle-arrow-down`, `circle-arrow-left`, `circle-arrow-out-down-left`, `circle-arrow-out-down-right`, `circle-arrow-out-up-left`, `circle-arrow-out-up-right`, `circle-arrow-right`, `circle-arrow-up`, `circle-check`, `circle-check-big`, `circle-chevron-down`, `circle-chevron-left`, `circle-chevron-right`, `circle-chevron-up`, `circle-dashed`, `circle-divide`, `circle-dollar-sign`, `circle-dot`, `circle-dot-dashed`, `circle-ellipsis`, `circle-equal`, `circle-fading-plus`, `circle-gauge`, `circle-help`, `circle-minus`, `circle-off`, `circle-parking`, `circle-parking-off`, `circle-pause`, `circle-percent`, `circle-play`, `circle-plus`, `circle-power`, `circle-slash`, `circle-slash-2`, `circle-stop`, `circle-user`, `circle-user-round`, `circle-x`, `circuit-board`, `citrus`, `clapperboard`, `clipboard`, `clipboard-check`, `clipboard-copy`, `clipboard-list`, `clipboard-minus`, `clipboard-paste`, `clipboard-pen`, `clipboard-pen-line`, `clipboard-plus`, `clipboard-type`, `clipboard-x`, `clock`, `clock-1`, `clock-10`, `clock-11`, `clock-12`, `clock-2`, `clock-3`, `clock-4`, `clock-5`, `clock-6`, `clock-7`, `clock-8`, `clock-9`, `clock-arrow-down`, `clock-arrow-up`, `cloud`, `cloud-cog`, `cloud-download`, `cloud-drizzle`, `cloud-fog`, `cloud-hail`, `cloud-lightning`, `cloud-moon`, `cloud-moon-rain`, `cloud-off`, `cloud-rain`, `cloud-rain-wind`, `cloud-snow`, `cloud-sun`, `cloud-sun-rain`, `cloud-upload`, `cloudy`, `clover`, `club`, `code`, `code-xml`, `codepen`, `codesandbox`, `coffee`, `cog`, `coins`, `columns-2`, `columns-3`, `columns-4`, `combine`, `command`, `compass`, `component`, `computer`, `concierge-bell`, `cone`, `construction`, `contact`, `contact-round`, `container`, `contrast`, `cookie`, `cooking-pot`, `copy`, `copy-check`, `copy-minus`, `copy-plus`, `copy-slash`, `copy-x`, `copyleft`, `copyright`, `corner-down-left`, `corner-down-right`, `corner-left-down`, `corner-left-up`, `corner-right-down`, `corner-right-up`, `corner-up-left`, `corner-up-right`, `cpu`, `creative-commons`, `credit-card`, `croissant`, `crop`, `cross`, `crosshair`, `crown`, `cuboid`, `cup-soda`, `currency`, `cylinder`

**D**
`dam`, `database`, `database-backup`, `database-zap`, `delete`, `dessert`, `diameter`, `diamond`, `diamond-minus`, `diamond-percent`, `diamond-plus`, `dice-1`, `dice-2`, `dice-3`, `dice-4`, `dice-5`, `dice-6`, `dices`, `diff`, `disc`, `disc-2`, `disc-3`, `disc-album`, `divide`, `dna`, `dna-off`, `dock`, `dog`, `dollar-sign`, `donut`, `door-closed`, `door-open`, `dot`, `download`, `drafting-compass`, `drama`, `dribbble`, `drill`, `droplet`, `droplets`, `drum`, `drumstick`, `dumbbell`

**E**
`ear`, `ear-off`, `earth`, `earth-lock`, `eclipse`, `egg`, `egg-fried`, `egg-off`, `ellipsis`, `ellipsis-vertical`, `equal`, `equal-not`, `eraser`, `euro`, `expand`, `external-link`, `eye`, `eye-off`

**F**
`facebook`, `factory`, `fan`, `fast-forward`, `feather`, `fence`, `ferris-wheel`, `figma`, `file`, `file-archive`, `file-audio`, `file-audio-2`, `file-axis-3d`, `file-badge`, `file-badge-2`, `file-box`, `file-chart-column`, `file-chart-column-increasing`, `file-chart-line`, `file-chart-pie`, `file-check`, `file-check-2`, `file-clock`, `file-code`, `file-code-2`, `file-cog`, `file-diff`, `file-digit`, `file-down`, `file-heart`, `file-image`, `file-input`, `file-json`, `file-json-2`, `file-key`, `file-key-2`, `file-lock`, `file-lock-2`, `file-minus`, `file-minus-2`, `file-music`, `file-output`, `file-pen`, `file-pen-line`, `file-plus`, `file-plus-2`, `file-question`, `file-scan`, `file-search`, `file-search-2`, `file-sliders`, `file-spreadsheet`, `file-stack`, `file-symlink`, `file-terminal`, `file-text`, `file-type`, `file-type-2`, `file-up`, `file-video`, `file-video-2`, `file-volume`, `file-volume-2`, `file-warning`, `file-x`, `file-x-2`, `files`, `film`, `filter`, `filter-x`, `fingerprint`, `fire-extinguisher`, `fish`, `fish-off`, `fish-symbol`, `flag`, `flag-off`, `flag-triangle-left`, `flag-triangle-right`, `flame`, `flame-kindling`, `flashlight`, `flashlight-off`, `flask-conical`, `flask-conical-off`, `flask-round`, `flip-horizontal`, `flip-horizontal-2`, `flip-vertical`, `flip-vertical-2`, `flower`, `flower-2`, `focus`, `fold-horizontal`, `fold-vertical`, `folder`, `folder-archive`, `folder-check`, `folder-clock`, `folder-closed`, `folder-code`, `folder-cog`, `folder-dot`, `folder-down`, `folder-git`, `folder-git-2`, `folder-heart`, `folder-input`, `folder-kanban`, `folder-key`, `folder-lock`, `folder-minus`, `folder-open`, `folder-open-dot`, `folder-output`, `folder-pen`, `folder-plus`, `folder-root`, `folder-search`, `folder-search-2`, `folder-symlink`, `folder-sync`, `folder-tree`, `folder-up`, `folder-x`, `folders`, `footprints`, `forklift`, `forward`, `frame`, `framer`, `frown`, `fuel`, `fullscreen`

**G**
`gallery-horizontal`, `gallery-horizontal-end`, `gallery-thumbnails`, `gallery-vertical`, `gallery-vertical-end`, `gamepad`, `gamepad-2`, `gauge`, `gavel`, `gem`, `ghost`, `gift`, `git-branch`, `git-branch-plus`, `git-commit-horizontal`, `git-commit-vertical`, `git-compare`, `git-compare-arrows`, `git-fork`, `git-graph`, `git-merge`, `git-pull-request`, `git-pull-request-arrow`, `git-pull-request-closed`, `git-pull-request-create`, `git-pull-request-create-arrow`, `git-pull-request-draft`, `github`, `gitlab`, `glass-water`, `glasses`, `globe`, `globe-lock`, `goal`, `grab`, `graduation-cap`, `grape`, `grid-2x2`, `grid-2x2-check`, `grid-2x2-x`, `grid-3x3`, `grip`, `grip-horizontal`, `grip-vertical`, `group`, `guitar`

**H**
`ham`, `hammer`, `hand`, `hand-coins`, `hand-heart`, `hand-helping`, `hand-metal`, `hand-platter`, `handshake`, `hard-drive`, `hard-drive-download`, `hard-drive-upload`, `hard-hat`, `hash`, `haze`, `hdmi-port`, `heading`, `heading-1`, `heading-2`, `heading-3`, `heading-4`, `heading-5`, `heading-6`, `headphones`, `headset`, `heart`, `heart-crack`, `heart-handshake`, `heart-off`, `heart-pulse`, `heater`, `hexagon`, `highlighter`, `history`, `hop`, `hop-off`, `hospital`, `hotel`, `hourglass`, `house`, `house-plug`, `house-plus`

**I**
`ice-cream-bowl`, `ice-cream-cone`, `id-card`, `image`, `image-down`, `image-minus`, `image-off`, `image-play`, `image-plus`, `image-up`, `images`, `import`, `inbox`, `indent-decrease`, `indent-increase`, `indian-rupee`, `infinity`, `info`, `inspection-panel`, `instagram`, `italic`, `iteration-ccw`, `iteration-cw`

**J–K**
`japanese-yen`, `joystick`, `kanban`, `key`, `key-round`, `key-square`, `keyboard`, `keyboard-music`, `keyboard-off`

**L**
`lamp`, `lamp-ceiling`, `lamp-desk`, `lamp-floor`, `lamp-wall-down`, `lamp-wall-up`, `land-plot`, `landmark`, `languages`, `laptop`, `laptop-minimal`, `lasso`, `lasso-select`, `laugh`, `layers`, `layers-2`, `layers-3`, `layout-dashboard`, `layout-grid`, `layout-list`, `layout-panel-left`, `layout-panel-top`, `layout-template`, `leaf`, `leafy-green`, `lectern`, `letter-text`, `library`, `library-big`, `life-buoy`, `ligature`, `lightbulb`, `lightbulb-off`, `link`, `link-2`, `link-2-off`, `linkedin`, `list`, `list-check`, `list-checks`, `list-collapse`, `list-end`, `list-filter`, `list-minus`, `list-music`, `list-ordered`, `list-plus`, `list-restart`, `list-start`, `list-todo`, `list-tree`, `list-video`, `list-x`, `loader`, `loader-circle`, `loader-pinwheel`, `locate`, `locate-fixed`, `locate-off`, `lock`, `lock-keyhole`, `lock-keyhole-open`, `lock-open`, `log-in`, `log-out`, `logs`, `lollipop`, `luggage`

**M**
`magnet`, `mail`, `mail-check`, `mail-minus`, `mail-open`, `mail-plus`, `mail-question`, `mail-search`, `mail-warning`, `mail-x`, `mailbox`, `mails`, `map`, `map-pin`, `map-pin-check`, `map-pin-check-inside`, `map-pin-minus`, `map-pin-minus-inside`, `map-pin-off`, `map-pin-plus`, `map-pin-plus-inside`, `map-pin-x`, `map-pin-x-inside`, `map-pinned`, `martini`, `maximize`, `maximize-2`, `medal`, `megaphone`, `megaphone-off`, `meh`, `memory-stick`, `menu`, `merge`, `message-circle`, `message-circle-code`, `message-circle-dashed`, `message-circle-heart`, `message-circle-more`, `message-circle-off`, `message-circle-plus`, `message-circle-question`, `message-circle-reply`, `message-circle-warning`, `message-circle-x`, `message-square`, `message-square-code`, `message-square-dashed`, `message-square-diff`, `message-square-dot`, `message-square-heart`, `message-square-more`, `message-square-off`, `message-square-plus`, `message-square-quote`, `message-square-reply`, `message-square-share`, `message-square-text`, `message-square-warning`, `message-square-x`, `messages-square`, `mic`, `mic-off`, `mic-vocal`, `microscope`, `microwave`, `milestone`, `milk`, `milk-off`, `minimize`, `minimize-2`, `minus`, `monitor`, `monitor-check`, `monitor-cog`, `monitor-dot`, `monitor-down`, `monitor-off`, `monitor-pause`, `monitor-play`, `monitor-smartphone`, `monitor-speaker`, `monitor-stop`, `monitor-up`, `monitor-x`, `moon`, `moon-star`, `mountain`, `mountain-snow`, `mouse`, `mouse-off`, `mouse-pointer`, `mouse-pointer-2`, `mouse-pointer-ban`, `mouse-pointer-click`, `move`, `move-3d`, `move-diagonal`, `move-diagonal-2`, `move-down`, `move-down-left`, `move-down-right`, `move-horizontal`, `move-left`, `move-right`, `move-up`, `move-up-left`, `move-up-right`, `move-vertical`, `music`, `music-2`, `music-3`, `music-4`

**N–O**
`navigation`, `navigation-2`, `navigation-2-off`, `navigation-off`, `network`, `newspaper`, `nfc`, `notebook`, `notebook-pen`, `notebook-tabs`, `notebook-text`, `notepad-text`, `notepad-text-dashed`, `nut`, `nut-off`, `octagon`, `octagon-alert`, `octagon-pause`, `octagon-x`, `option`, `orbit`, `origami`

**P**
`package`, `package-2`, `package-check`, `package-minus`, `package-open`, `package-plus`, `package-search`, `package-x`, `paint-bucket`, `paint-roller`, `paintbrush`, `paintbrush-vertical`, `palette`, `panel-bottom`, `panel-bottom-close`, `panel-bottom-dashed`, `panel-bottom-open`, `panel-left`, `panel-left-close`, `panel-left-dashed`, `panel-left-open`, `panel-right`, `panel-right-close`, `panel-right-dashed`, `panel-right-open`, `panel-top`, `panel-top-close`, `panel-top-dashed`, `panel-top-open`, `panels-left-bottom`, `panels-right-bottom`, `panels-top-left`, `paperclip`, `parentheses`, `parking-meter`, `party-popper`, `pause`, `paw-print`, `pc-case`, `pen`, `pen-line`, `pen-off`, `pen-tool`, `pencil`, `pencil-line`, `pencil-off`, `pencil-ruler`, `pentagon`, `percent`, `person-standing`, `philippine-peso`, `phone`, `phone-call`, `phone-forwarded`, `phone-incoming`, `phone-missed`, `phone-off`, `phone-outgoing`, `pi`, `piano`, `pickaxe`, `picture-in-picture`, `picture-in-picture-2`, `piggy-bank`, `pilcrow`, `pilcrow-left`, `pilcrow-right`, `pill`, `pill-bottle`, `pin`, `pin-off`, `pipette`, `pizza`, `plane`, `plane-landing`, `plane-takeoff`, `play`, `plug`, `plug-2`, `plug-zap`, `plus`, `pocket`, `pocket-knife`, `podcast`, `pointer`, `pointer-off`, `popcorn`, `popsicle`, `pound-sterling`, `power`, `power-off`, `presentation`, `printer`, `printer-check`, `projector`, `proportions`, `puzzle`, `pyramid`

**Q–R**
`qr-code`, `quote`, `rabbit`, `radar`, `radiation`, `radical`, `radio`, `radio-receiver`, `radio-tower`, `radius`, `rail-symbol`, `rainbow`, `rat`, `ratio`, `receipt`, `receipt-cent`, `receipt-euro`, `receipt-indian-rupee`, `receipt-japanese-yen`, `receipt-pound-sterling`, `receipt-russian-ruble`, `receipt-swiss-franc`, `receipt-text`, `rectangle-ellipsis`, `rectangle-horizontal`, `rectangle-vertical`, `recycle`, `redo`, `redo-2`, `redo-dot`, `refresh-ccw`, `refresh-ccw-dot`, `refresh-cw`, `refresh-cw-off`, `refrigerator`, `regex`, `remove-formatting`, `repeat`, `repeat-1`, `repeat-2`, `replace`, `replace-all`, `reply`, `reply-all`, `rewind`, `ribbon`, `rocket`, `rocking-chair`, `roller-coaster`, `rotate-3d`, `rotate-ccw`, `rotate-ccw-square`, `rotate-cw`, `rotate-cw-square`, `route`, `route-off`, `router`, `rows-2`, `rows-3`, `rows-4`, `rss`, `ruler`, `russian-ruble`

**S**
`sailboat`, `salad`, `sandwich`, `satellite`, `satellite-dish`, `save`, `save-all`, `save-off`, `scale`, `scale-3d`, `scaling`, `scan`, `scan-barcode`, `scan-eye`, `scan-face`, `scan-line`, `scan-qr-code`, `scan-search`, `scan-text`, `school`, `scissors`, `scissors-line-dashed`, `screen-share`, `screen-share-off`, `scroll`, `scroll-text`, `search`, `search-check`, `search-code`, `search-slash`, `search-x`, `section`, `send`, `send-horizontal`, `send-to-back`, `separator-horizontal`, `separator-vertical`, `server`, `server-cog`, `server-crash`, `server-off`, `settings`, `settings-2`, `shapes`, `share`, `share-2`, `sheet`, `shell`, `shield`, `shield-alert`, `shield-ban`, `shield-check`, `shield-ellipsis`, `shield-half`, `shield-minus`, `shield-off`, `shield-plus`, `shield-question`, `shield-x`, `ship`, `ship-wheel`, `shirt`, `shopping-bag`, `shopping-basket`, `shopping-cart`, `shovel`, `shower-head`, `shrink`, `shrub`, `shuffle`, `sigma`, `signal`, `signal-high`, `signal-low`, `signal-medium`, `signal-zero`, `signature`, `signpost`, `signpost-big`, `siren`, `skip-back`, `skip-forward`, `skull`, `slack`, `slash`, `slice`, `sliders-horizontal`, `sliders-vertical`, `smartphone`, `smartphone-charging`, `smartphone-nfc`, `smile`, `smile-plus`, `snail`, `snowflake`, `sofa`, `sort-asc`, `sort-desc`, `soup`, `space`, `spade`, `sparkle`, `sparkles`, `speaker`, `speech`, `spell-check`, `spell-check-2`, `spline`, `split`, `spray-can`, `sprout`, `square`, `square-activity`, `square-arrow-down`, `square-arrow-down-left`, `square-arrow-down-right`, `square-arrow-left`, `square-arrow-out-down-left`, `square-arrow-out-down-right`, `square-arrow-out-up-left`, `square-arrow-out-up-right`, `square-arrow-right`, `square-arrow-up`, `square-arrow-up-left`, `square-arrow-up-right`, `square-asterisk`, `square-bottom-dashed-scissors`, `square-chart-gantt`, `square-check`, `square-check-big`, `square-chevron-down`, `square-chevron-left`, `square-chevron-right`, `square-chevron-up`, `square-code`, `square-dashed-bottom`, `square-dashed-bottom-code`, `square-dashed-kanban`, `square-dashed-mouse-pointer`, `square-divide`, `square-dot`, `square-equal`, `square-function`, `square-kanban`, `square-library`, `square-m`, `square-menu`, `square-minus`, `square-mouse-pointer`, `square-parking`, `square-parking-off`, `square-pen`, `square-percent`, `square-pi`, `square-pilcrow`, `square-play`, `square-plus`, `square-power`, `square-radical`, `square-scissors`, `square-sigma`, `square-slash`, `square-split-horizontal`, `square-split-vertical`, `square-square`, `square-stack`, `square-terminal`, `square-user`, `square-user-round`, `square-x`, `squircle`, `squirrel`, `stamp`, `star`, `star-half`, `star-off`, `step-back`, `step-forward`, `stethoscope`, `sticker`, `sticky-note`, `store`, `stretch-horizontal`, `stretch-vertical`, `strikethrough`, `subscript`, `sun`, `sun-dim`, `sun-medium`, `sun-moon`, `sun-snow`, `sunrise`, `sunset`, `superscript`, `swatch-book`, `swiss-franc`, `switch-camera`, `sword`, `swords`, `syringe`

**T**
`table`, `table-2`, `table-cells-merge`, `table-cells-split`, `table-columns-split`, `table-properties`, `table-rows-split`, `tablet`, `tablet-smartphone`, `tablets`, `tag`, `tags`, `tally-1`, `tally-2`, `tally-3`, `tally-4`, `tally-5`, `tangent`, `target`, `telescope`, `tent`, `tent-tree`, `terminal`, `test-tube`, `test-tube-diagonal`, `test-tubes`, `text`, `text-cursor`, `text-cursor-input`, `text-quote`, `text-search`, `text-select`, `theater`, `thermometer`, `thermometer-snowflake`, `thermometer-sun`, `thumbs-down`, `thumbs-up`, `ticket`, `ticket-check`, `ticket-minus`, `ticket-percent`, `ticket-plus`, `ticket-slash`, `ticket-x`, `timer`, `timer-off`, `timer-reset`, `toggle-left`, `toggle-right`, `tornado`, `torus`, `touchpad`, `touchpad-off`, `tower-control`, `toy-brick`, `tractor`, `traffic-cone`, `train-front`, `train-front-tunnel`, `train-track`, `tram-front`, `trash`, `trash-2`, `tree-deciduous`, `tree-palm`, `tree-pine`, `trees`, `trello`, `trending-down`, `trending-up`, `triangle`, `triangle-alert`, `triangle-right`, `trophy`, `truck`, `turtle`, `tv`, `tv-minimal`, `tv-minimal-play`, `twitch`, `twitter`, `type`, `type-outline`

**U–V**
`umbrella`, `umbrella-off`, `underline`, `undo`, `undo-2`, `undo-dot`, `unfold-horizontal`, `unfold-vertical`, `ungroup`, `university`, `unlink`, `unlink-2`, `unplug`, `upload`, `usb`, `user`, `user-check`, `user-cog`, `user-minus`, `user-pen`, `user-plus`, `user-round`, `user-round-check`, `user-round-cog`, `user-round-minus`, `user-round-pen`, `user-round-plus`, `user-round-search`, `user-round-x`, `user-search`, `user-x`, `users`, `users-round`, `utensils`, `utensils-crossed`, `utility-pole`, `variable`, `vault`, `vegan`, `venetian-mask`, `vibrate`, `vibrate-off`, `video`, `video-off`, `videotape`, `view`, `voicemail`, `volume`, `volume-1`, `volume-2`, `volume-x`, `vote`

**W–Z**
`wallet`, `wallet-cards`, `wallet-minimal`, `wallpaper`, `wand`, `wand-sparkles`, `warehouse`, `washing-machine`, `watch`, `waves`, `waypoints`, `webcam`, `webhook`, `webhook-off`, `weight`, `wheat`, `wheat-off`, `whole-word`, `wifi`, `wifi-high`, `wifi-low`, `wifi-off`, `wifi-zero`, `wind`, `wine`, `wine-off`, `workflow`, `worm`, `wrap-text`, `wrench`, `x`, `youtube`, `zap`, `zap-off`, `zoom-in`, `zoom-out`

#### 3.23.5 Legacy set (`icon/*` prefix) — full alphabetical catalog (~837 icons)

This is the **older set, kept for backward compatibility**. Most of these are duplicated in the modern set above with the `icon/` prefix removed — prefer the modern form for new work.

**A**
`icon/accessibility`, `icon/activity`, `icon/air-vent`, `icon/airplay`, `icon/alarm-check`, `icon/alarm-clock`, `icon/alarm-clock-off`, `icon/alarm-minus`, `icon/alarm-plus`, `icon/album`, `icon/alert-circle`, `icon/alert-octagon`, `icon/alert-triangle`, `icon/align-center`, `icon/align-center-horizontal`, `icon/align-center-vertical`, `icon/align-end-horizontal`, `icon/align-end-vertical`, `icon/align-horizontal-distribute-center`, `icon/align-horizontal-distribute-end`, `icon/align-horizontal-distribute-start`, `icon/align-horizontal-justify-center`, `icon/align-horizontal-justify-end`, `icon/align-horizontal-justify-start`, `icon/align-horizontal-space-around`, `icon/align-horizontal-space-between`, `icon/align-justify`, `icon/align-left`, `icon/align-right`, `icon/align-start-horizontal`, `icon/align-start-vertical`, `icon/align-vertical-distribute-center`, `icon/align-vertical-distribute-end`, `icon/align-vertical-distribute-start`, `icon/align-vertical-justify-center`, `icon/align-vertical-justify-end`, `icon/align-vertical-justify-start`, `icon/align-vertical-space-around`, `icon/align-vertical-space-between`, `icon/anchor`, `icon/angry`, `icon/annoyed`, `icon/aperture`, `icon/apple`, `icon/archive`, `icon/archive-restore`, `icon/armchair`, `icon/arrow-big-down`, `icon/arrow-big-left`, `icon/arrow-big-right`, `icon/arrow-big-up`, `icon/arrow-down`, `icon/arrow-down-circle`, `icon/arrow-down-left`, `icon/arrow-down-right`, `icon/arrow-left`, `icon/arrow-left-circle`, `icon/arrow-left-right`, `icon/arrow-right`, `icon/arrow-right-circle`, `icon/arrow-up`, `icon/arrow-up-circle`, `icon/arrow-up-down`, `icon/arrow-up-left`, `icon/arrow-up-right`, `icon/asterisk`, `icon/at-sign`, `icon/award`, `icon/axe`, `icon/axis-3d`

**B**
`icon/baby`, `icon/backpack`, `icon/baggage-claim`, `icon/banana`, `icon/banknote`, `icon/bar-chart`, `icon/bar-chart-2`, `icon/bar-chart-3`, `icon/bar-chart-4`, `icon/bar-chart-horizontal`, `icon/Barcode`, `icon/baseline`, `icon/bath`, `icon/battery`, `icon/battery-charging`, `icon/battery-full`, `icon/battery-low`, `icon/battery-medium`, `icon/battery-warning`, `icon/beaker`, `icon/bean`, `icon/bean-off`, `icon/bed`, `icon/bed-double`, `icon/bed-single`, `icon/beef`, `icon/beer`, `icon/bell`, `icon/bell-minus`, `icon/bell-off`, `icon/bell-plus`, `icon/bell-ring`, `icon/bike`, `icon/binary`, `icon/bitcoin`, `icon/bluetooth`, `icon/bluetooth-connected`, `icon/bluetooth-off`, `icon/bluetooth-searching`, `icon/bold`, `icon/bomb`, `icon/bone`, `icon/book`, `icon/book-open`, `icon/book-open-check`, `icon/bookmark`, `icon/bookmark-minus`, `icon/bookmark-plus`, `icon/bot`, `icon/box`, `icon/box-select`, `icon/boxes`, `icon/briefcase`, `icon/brush`, `icon/bug`, `icon/building`, `icon/building-2`, `icon/bus`

**C**
`icon/cake`, `icon/calculator`, `icon/calendar`, `icon/calendar-check`, `icon/calendar-check-2`, `icon/calendar-clock`, `icon/calendar-days`, `icon/calendar-heart`, `icon/calendar-minus`, `icon/calendar-off`, `icon/calendar-plus`, `icon/calendar-range`, `icon/calendar-search`, `icon/calendar-x`, `icon/calendar-x-2`, `icon/camera`, `icon/camera-off`, `icon/candy`, `icon/candy-off`, `icon/car`, `icon/carrot`, `icon/cast`, `icon/cat`, `icon/check`, `icon/check-check`, `icon/check-circle`, `icon/check-circle-2`, `icon/check-square`, `icon/chef-hat`, `icon/cherry`, `icon/chevron-down`, `icon/chevron-first`, `icon/chevron-last`, `icon/chevron-left`, `icon/chevron-right`, `icon/chevron-up`, `icon/chevrons-down`, `icon/chevrons-down-up`, `icon/chevrons-left`, `icon/chevrons-left-right`, `icon/chevrons-right`, `icon/chevrons-right-left`, `icon/chevrons-up`, `icon/chevrons-up-down`, `icon/chrome`, `icon/cigarette`, `icon/cigarette-off`, `icon/circle`, `icon/circle-dot`, `icon/circle-ellipsis`, `icon/circle-slashed`, `icon/citrus`, `icon/clapperboard`, `icon/clipboard`, `icon/clipboard-check`, `icon/clipboard-copy`, `icon/clipboard-edit`, `icon/clipboard-list`, `icon/clipboard-signature`, `icon/clipboard-type`, `icon/clipboard-x`, `icon/clock`, `icon/clock-1`, `icon/clock-2`, `icon/clock-3`, `icon/clock-4`, `icon/clock-5`, `icon/clock-6`, `icon/clock-7`, `icon/clock-8`, `icon/clock-9`, `icon/clock-10`, `icon/clock-11`, `icon/clock-12`, `icon/cloud`, `icon/cloud-cog`, `icon/cloud-drizzle`, `icon/cloud-fog`, `icon/cloud-hail`, `icon/cloud-lightning`, `icon/cloud-moon`, `icon/cloud-moon-rain`, `icon/cloud-off`, `icon/cloud-rain`, `icon/cloud-rain-wind`, `icon/cloud-snow`, `icon/cloud-sun`, `icon/cloud-sun-rain`, `icon/cloudy`, `icon/clover`, `icon/code`, `icon/code-2`, `icon/codepen`, `icon/codesandbox`, `icon/coffee`, `icon/cog`, `icon/coins`, `icon/columns`, `icon/command`, `icon/compass`, `icon/component`, `icon/concierge-bell`, `icon/contact`, `icon/contrast`, `icon/cookie`, `icon/copy`, `icon/copyleft`, `icon/copyright`, `icon/corner-down-left`, `icon/corner-down-right`, `icon/corner-left-down`, `icon/corner-left-up`, `icon/corner-right-down`, `icon/corner-right-up`, `icon/corner-up-left`, `icon/corner-up-right`, `icon/cpu`, `icon/credit-card`, `icon/croissant`, `icon/crop`, `icon/cross`, `icon/crosshair`, `icon/crown`, `icon/cup-soda`, `icon/curly-braces`, `icon/currency`

**D–E**
`icon/database`, `icon/database-backup`, `icon/delete`, `icon/diamond`, `icon/dice-1`, `icon/dice-2`, `icon/dice-3`, `icon/dice-4`, `icon/dice-5`, `icon/dice-6`, `icon/dices`, `icon/diff`, `icon/disc`, `icon/divide`, `icon/divide-circle`, `icon/divide-square`, `icon/dna`, `icon/dna-off`, `icon/dog`, `icon/dollar-sign`, `icon/download`, `icon/download-cloud`, `icon/dribbble`, `icon/droplet`, `icon/droplets`, `icon/drumstick`, `icon/dumbbell`, `icon/ear`, `icon/ear-off`, `icon/edit`, `icon/edit-2`, `icon/edit-3`, `icon/egg`, `icon/egg-fried`, `icon/egg-off`, `icon/equal`, `icon/equal-not`, `icon/eraser`, `icon/euro`, `icon/expand`, `icon/external-link`, `icon/eye`, `icon/eye-off`

**F**
`icon/facebook`, `icon/factory`, `icon/fan`, `icon/fast-forward`, `icon/feather`, `icon/figma`, `icon/file`, `icon/file-archive`, `icon/file-audio`, `icon/file-audio-2`, `icon/file-axis-3d`, `icon/file-badge`, `icon/file-badge-2`, `icon/file-bar-chart`, `icon/file-bar-chart-2`, `icon/file-box`, `icon/file-check`, `icon/file-check-2`, `icon/file-clock`, `icon/file-code`, `icon/file-cog`, `icon/file-cog-2`, `icon/file-diff`, `icon/file-digit`, `icon/file-down`, `icon/file-edit`, `icon/file-heart`, `icon/file-image`, `icon/file-input`, `icon/file-json`, `icon/file-json-2`, `icon/file-key`, `icon/file-key-2`, `icon/file-line-chart`, `icon/file-lock`, `icon/file-lock-2`, `icon/file-minus`, `icon/file-minus-2`, `icon/file-output`, `icon/file-pie-chart`, `icon/file-plus`, `icon/file-plus-2`, `icon/file-question`, `icon/file-scan`, `icon/file-search`, `icon/file-search-2`, `icon/file-signature`, `icon/file-spreadsheet`, `icon/file-symlink`, `icon/file-terminal`, `icon/file-text`, `icon/file-type`, `icon/file-type-2`, `icon/file-up`, `icon/file-video`, `icon/file-video-2`, `icon/file-volume`, `icon/file-volume-2`, `icon/file-warning`, `icon/file-x`, `icon/file-x-2`, `icon/files`, `icon/film`, `icon/filter`, `icon/fingerprint`, `icon/fish`, `icon/flag`, `icon/flag-off`, `icon/flag-triangle-left`, `icon/flag-triangle-right`, `icon/flame`, `icon/flashlight`, `icon/flashlight-off`, `icon/flask-conical`, `icon/flask-conical-off`, `icon/flask-round`, `icon/flip-horizontal`, `icon/flip-horizontal-2`, `icon/flip-vertical`, `icon/flip-vertical-2`, `icon/flower`, `icon/flower-2`, `icon/focus`, `icon/folder`, `icon/folder-archive`, `icon/folder-check`, `icon/folder-clock`, `icon/folder-closed`, `icon/folder-cog`, `icon/folder-cog-2`, `icon/folder-down`, `icon/folder-edit`, `icon/folder-heart`, `icon/folder-input`, `icon/folder-key`, `icon/folder-lock`, `icon/folder-minus`, `icon/folder-open`, `icon/folder-output`, `icon/folder-plus`, `icon/folder-search`, `icon/folder-search-2`, `icon/folder-symlink`, `icon/folder-tree`, `icon/folder-up`, `icon/folder-x`, `icon/folders`, `icon/form-input`, `icon/forward`, `icon/frame`, `icon/framer`, `icon/frown`, `icon/fuel`, `icon/function-square`

**G–H**
`icon/gamepad`, `icon/gamepad-2`, `icon/gauge`, `icon/gavel`, `icon/gem`, `icon/ghost`, `icon/gift`, `icon/git-branch`, `icon/git-branch-plus`, `icon/git-commit`, `icon/git-compare`, `icon/git-fork`, `icon/git-merge`, `icon/git-pull-request`, `icon/git-pull-request-closed`, `icon/git-pull-request-draft`, `icon/github`, `icon/gitlab`, `icon/glass-water`, `icon/glasses`, `icon/globe`, `icon/globe-2`, `icon/grab`, `icon/graduation-cap`, `icon/grape`, `icon/grid`, `icon/grip-horizontal`, `icon/grip-vertical`, `icon/hammer`, `icon/hand`, `icon/hand-metal`, `icon/hard-drive`, `icon/hard-hat`, `icon/hash`, `icon/haze`, `icon/heading`, `icon/heading-1`, `icon/heading-2`, `icon/heading-3`, `icon/heading-4`, `icon/heading-5`, `icon/heading-6`, `icon/headphones`, `icon/heart`, `icon/heart-crack`, `icon/heart-handshake`, `icon/heart-off`, `icon/heart-pulse`, `icon/help-circle`, `icon/hexagon`, `icon/highlighter`, `icon/history`, `icon/home`, `icon/hop`, `icon/hop-off`, `icon/hourglass`

**I–K**
`icon/ice-cream`, `icon/ice-cream-2`, `icon/image`, `icon/image-minus`, `icon/image-off`, `icon/image-plus`, `icon/import`, `icon/inbox`, `icon/indent`, `icon/indian-rupee`, `icon/infinity`, `icon/info`, `icon/inspect`, `icon/instagram`, `icon/italic`, `icon/japanese-yen`, `icon/joystick`, `icon/key`, `icon/keyboard`

**L**
`icon/lamp`, `icon/lamp-ceiling`, `icon/lamp-desk`, `icon/lamp-floor`, `icon/lamp-wall-down`, `icon/lamp-wall-up`, `icon/landmark`, `icon/languages`, `icon/laptop`, `icon/laptop-2`, `icon/lasso`, `icon/lasso-select`, `icon/laugh`, `icon/layers`, `icon/layout`, `icon/layout-dashboard`, `icon/layout-grid`, `icon/layout-list`, `icon/layout-template`, `icon/leaf`, `icon/library`, `icon/life-buoy`, `icon/lightbulb`, `icon/lightbulb-off`, `icon/line-chart`, `icon/link`, `icon/link-2`, `icon/link-2-off`, `icon/linkedin`, `icon/list`, `icon/list-checks`, `icon/list-end`, `icon/list-minus`, `icon/list-music`, `icon/list-ordered`, `icon/list-plus`, `icon/list-start`, `icon/list-video`, `icon/list-x`, `icon/loader`, `icon/loader-2`, `icon/locate`, `icon/locate-fixed`, `icon/locate-off`, `icon/lock`, `icon/log-in`, `icon/log-out`, `icon/luggage`

**M**
`icon/magnet`, `icon/mail`, `icon/mail-check`, `icon/mail-minus`, `icon/mail-open`, `icon/mail-plus`, `icon/mail-question`, `icon/mail-search`, `icon/mail-warning`, `icon/mail-x`, `icon/mails`, `icon/map`, `icon/map-pin`, `icon/map-pin-off`, `icon/martini`, `icon/maximize`, `icon/maximize-2`, `icon/medal`, `icon/megaphone`, `icon/megaphone-off`, `icon/meh`, `icon/menu`, `icon/message-circle`, `icon/message-square`, `icon/mic`, `icon/mic-2`, `icon/mic-off`, `icon/microscope`, `icon/microwave`, `icon/milestone`, `icon/milk`, `icon/milk-off`, `icon/minimize`, `icon/minimize-2`, `icon/minus`, `icon/minus-circle`, `icon/minus-square`, `icon/monitor`, `icon/monitor-off`, `icon/monitor-smartphone`, `icon/monitor-speaker`, `icon/moon`, `icon/more-horizontal`, `icon/more-vertical`, `icon/mountain`, `icon/mountain-snow`, `icon/mouse`, `icon/mouse-pointer`, `icon/mouse-pointer-2`, `icon/mouse-pointer-click`, `icon/move`, `icon/move-3d`, `icon/move-diagonal`, `icon/move-diagonal-2`, `icon/move-horizontal`, `icon/move-vertical`, `icon/music`, `icon/music-2`, `icon/music-3`, `icon/music-4`

**N–O**
`icon/navigation`, `icon/navigation-2`, `icon/navigation-2-off`, `icon/navigation-off`, `icon/network`, `icon/newspaper`, `icon/nut`, `icon/nut-off`, `icon/octagon`, `icon/option`, `icon/outdent`

**P**
`icon/package`, `icon/package-2`, `icon/package-check`, `icon/package-minus`, `icon/package-open`, `icon/package-plus`, `icon/package-search`, `icon/package-x`, `icon/paint-bucket`, `icon/paintbrush`, `icon/paintbrush-2`, `icon/palette`, `icon/palmtree`, `icon/paperclip`, `icon/party-popper`, `icon/pause`, `icon/pause-circle`, `icon/pause-octagon`, `icon/pen-tool`, `icon/pencil`, `icon/percent`, `icon/person-standing`, `icon/phone`, `icon/phone-call`, `icon/phone-forwarded`, `icon/phone-incoming`, `icon/phone-missed`, `icon/phone-off`, `icon/phone-outgoing`, `icon/pie-chart`, `icon/piggy-bank`, `icon/pilcrow`, `icon/pin`, `icon/pin-off`, `icon/pipette`, `icon/pizza`, `icon/Placeholder`, `icon/plane`, `icon/play`, `icon/play-circle`, `icon/plug`, `icon/plug-2`, `icon/plug-zap`, `icon/plus`, `icon/plus-circle`, `icon/plus-square`, `icon/pocket`, `icon/podcast`, `icon/pointer`, `icon/pound-sterling`, `icon/power`, `icon/power-off`, `icon/printer`, `icon/puzzle`

**Q–S**
`icon/qr-code`, `icon/quote`, `icon/radio`, `icon/radio-receiver`, `icon/rectangle-horizontal`, `icon/rectangle-vertical`, `icon/recycle`, `icon/redo`, `icon/redo-2`, `icon/refresh-ccw`, `icon/refresh-cw`, `icon/refrigerator`, `icon/regex`, `icon/repeat`, `icon/repeat-1`, `icon/reply`, `icon/reply-all`, `icon/rewind`, `icon/rocket`, `icon/rocking-chair`, `icon/rotate-3d`, `icon/rotate-ccw`, `icon/rotate-cw`, `icon/rss`, `icon/ruler`, `icon/russian-ruble`, `icon/sailboat`, `icon/salad`, `icon/sandwich`, `icon/save`, `icon/scale`, `icon/scale-3d`, `icon/scaling`, `icon/scan`, `icon/scan-face`, `icon/scan-line`, `icon/scissors`, `icon/screen-share`, `icon/screen-share-off`, `icon/scroll`, `icon/search`, `icon/send`, `icon/separator-horizontal`, `icon/separator-vertical`, `icon/server`, `icon/server-cog`, `icon/server-crash`, `icon/server-off`, `icon/settings`, `icon/settings-2`, `icon/share`, `icon/share-2`, `icon/sheet`, `icon/shield`, `icon/shield-alert`, `icon/shield-check`, `icon/shield-close`, `icon/shield-off`, `icon/shirt`, `icon/shopping-bag`, `icon/shopping-cart`, `icon/shovel`, `icon/shower-head`, `icon/shrink`, `icon/shrub`, `icon/shuffle`, `icon/sidebar`, `icon/sidebar-close`, `icon/sidebar-open`, `icon/sigma`, `icon/signal`, `icon/signal-high`, `icon/signal-low`, `icon/signal-medium`, `icon/signal-zero`, `icon/siren`, `icon/skip-back`, `icon/skip-forward`, `icon/skull`, `icon/slack`, `icon/slash`, `icon/slice`, `icon/sliders`, `icon/sliders-horizontal`, `icon/smartphone`, `icon/smartphone-charging`, `icon/smile`, `icon/smile-plus`, `icon/snowflake`, `icon/sofa`, `icon/sort-asc`, `icon/sort-desc`, `icon/soup`, `icon/speaker`, `icon/spline`, `icon/sprout`, `icon/square`, `icon/star`, `icon/star-half`, `icon/star-off`, `icon/stethoscope`, `icon/sticker`, `icon/sticky-note`, `icon/stop-circle`, `icon/stretch-horizontal`, `icon/stretch-vertical`, `icon/strikethrough`, `icon/subscript`, `icon/subtitles`, `icon/sun`, `icon/sun-dim`, `icon/sun-medium`, `icon/sun-moon`, `icon/sun-snow`, `icon/sunrise`, `icon/sunset`, `icon/superscript`, `icon/swiss-franc`, `icon/switch-camera`, `icon/sword`, `icon/swords`, `icon/syringe`

**T–Z**
`icon/table`, `icon/table-2`, `icon/tablet`, `icon/tag`, `icon/tags`, `icon/target`, `icon/tent`, `icon/terminal`, `icon/terminal-square`, `icon/text-cursor`, `icon/text-cursor-input`, `icon/thermometer`, `icon/thermometer-snowflake`, `icon/thermometer-sun`, `icon/thumbs-down`, `icon/thumbs-up`, `icon/ticket`, `icon/timer`, `icon/timer-off`, `icon/timer-reset`, `icon/toggle-left`, `icon/toggle-right`, `icon/tornado`, `icon/toy-brick`, `icon/train`, `icon/trash`, `icon/trash-2`, `icon/tree-deciduous`, `icon/tree-pine`, `icon/trees`, `icon/trello`, `icon/trending-down`, `icon/trending-up`, `icon/triangle`, `icon/trophy`, `icon/truck`, `icon/tv`, `icon/tv-2`, `icon/twitch`, `icon/twitter`, `icon/type`, `icon/umbrella`, `icon/underline`, `icon/undo`, `icon/undo-2`, `icon/unlink`, `icon/unlink-2`, `icon/unlock`, `icon/upload`, `icon/upload-cloud`, `icon/usb`, `icon/user`, `icon/user-check`, `icon/user-cog`, `icon/user-minus`, `icon/user-plus`, `icon/user-x`, `icon/users`, `icon/utensils`, `icon/utensils-crossed`, `icon/vegan`, `icon/venetian-mask`, `icon/verified`, `icon/vibrate`, `icon/vibrate-off`, `icon/video`, `icon/video-off`, `icon/view`, `icon/voicemail`, `icon/volume`, `icon/volume-1`, `icon/volume-2`, `icon/volume-x`, `icon/wallet`, `icon/wand`, `icon/wand-2`, `icon/watch`, `icon/waves`, `icon/webcam`, `icon/webhook`, `icon/wheat`, `icon/wheat-off`, `icon/wifi`, `icon/wifi-off`, `icon/wind`, `icon/wine`, `icon/wine-off`, `icon/wrap-text`, `icon/wrench`, `icon/x`, `icon/x-circle`, `icon/x-octagon`, `icon/x-square`, `icon/youtube`, `icon/zap`, `icon/zap-off`, `icon/zoom-in`, `icon/zoom-out`

#### 3.23.6 Non-standard names / file bugs

The Web Guidelines icon page contains several names that **break the naming convention** in both sets. Reproduce verbatim until renamed:

| Verbatim name        | Issue                                                       |
| -------------------- | ----------------------------------------------------------- |
| `icon/Placeholder`   | Capital P — placeholder stub, candidate for removal         |
| `icon/Barcode`       | Capital B — should be `icon/barcode` (modern set has correct lowercase `barcode`) |
| `icon/check-circle-2` | Duplicates modern `circle-check-big`; kept for back-compat |
| `icon/Link`          | Capital L — Petpooja-specific link variant                  |
| `icon/Support`       | Capital S — Petpooja-specific                               |
| `icon/E-way Bill`    | Has hyphen and space                                        |
| `icon/E Bill`        | Has space                                                   |
| `icon/Loyalty`       | Capital L                                                   |
| `icon/Gift`          | Capital G                                                   |
| `icon/GST`           | All caps                                                    |
| `icon/Tax-k`         | Trailing `-k` — incomplete name?                            |
| `icon/notebook 1`    | Trailing ` 1` — file-bug version suffix                     |
| `tool-02`            | Missing `icon/` prefix; sits between `icon/zoom-out` and `icon/zoom-in` |
| `whatsapp`           | **Appears TWICE on the page** — once after `tool-02`, once near the end (duplicate) |
| `star-07`, `star-08` | No prefix, version-numbered decorative star variants        |
| `Placeholder image`  | No prefix; image-not-found state                            |
| `blocks-integration` | No prefix; integrations marker                              |
| `Store-outlet`       | No prefix, capitalised; Petpooja-specific                   |
| `Cash Drawer 1`      | Has space + trailing ` 1`                                   |
| `day-end`            | Petpooja-specific POS marker, no prefix                     |
| `column configure`   | Has space                                                   |
| `Update details`     | Capital U, has space                                        |
| `What's New`         | Has apostrophe + capitalisation                             |
| `What's new`         | **Duplicate of above with different casing** — file bug     |
| `Marketing (1) `     | Capital M, has parentheses, **trailing space** — file bug   |
| `Expense`, `Withdrawal`, `Cash_Topup`, `Birthday`, `anniversary`, `duplicate`, `Text` | No prefix; Petpooja-specific finance/CRM glyphs |
| `icon/drawer`, `icon/user-star`, `icon/Gift`, `icon/Loyalty` | Petpooja-specific in legacy prefix form |

> **Rule:** when implementing, use the **exact Figma name** including casing, spaces, parentheses, and trailing whitespace. Surface drift to design — these names should be cleaned up in Figma, not in code.

#### 3.23.7 Total count

2,422 icons total on page `4:29`:
- **~1,565** modern (prefix-less) glyphs — the primary Lucide v0.300+ set, recommended for new work
- **~837** legacy (`icon/*`) glyphs — older Lucide set, most names duplicated in modern set
- **~20** Petpooja-specific glyphs (mixed naming, scattered throughout)

> **Compared to the Mobile Guidelines file**, which ships 886 icons. Web has ~3× more, including many newer Lucide glyphs (`badge-*`, `chart-*`, `circle-*`, `house-*`, `panel-*`, `route-*`, `square-*`, `user-round-*`, etc.) that have no mobile equivalent. **If a design needs a glyph that exists only on web but not on mobile, surface the gap.**

---

## 4. Deprecated / do-not-use pages

Hard refusals — do not introduce these into a new design:

| Figma page name             | Why                                                                |
| --------------------------- | ------------------------------------------------------------------ |
| `--`                        | Empty separator page (skip)                                        |
| `Don't Use`                 | Empty placeholder page (skip)                                      |
| `(OLD) Don't use - Menus`   | Old menu pattern, deprecated                                       |
| `(Archived) Side Nav`       | Use the active `Side Nav` (§3.6.1) instead                         |
| `(Archived) Nav Items`      | Archived; do not use                                               |

> Note: `Breadcrumbs - Don't Use` is on the deprecated list in Figma but **user has overridden** — Breadcrumbs are treated as **active** here (§3.6.5).

---

## 5. Known file-level drift & file bugs

1. **Imported-library tokens leak into Web components.** Modal, Dropdowns, and some buttons reference styles from an imported library that does NOT appear in `base.md`: `Base / White`, `Gray / 200`, `Gray / 300`, `Primary / 600`, `Primary / Brand`, `Banner red`, `Shadow / xs`, `Shadow / xl`, `Button Shadow`, `detail` (text style), `slate/500` (colour), `Drawer` (shadow). When implementing, map these to the closest `base.md` equivalents and surface the divergence.
2. **POS Input uses Mobile text styles on a Desktop file** (§3.3). Treat as intentional in POS billing contexts; suspect elsewhere.
3. **Toaster Success fill is `#EFFDF3`**, slightly off from `Success/BG` `#ECFDF3` (`base.md §1.3`). Use the `base.md` value in code.
4. **Page name typo** — `Dropdowns & Droodown List` (should be "Dropdown").
5. **Variant naming typo** — `Sucess` (should be "Success") in Toaster and Table Cell - Badge.
6. **Style name typo** — `Desktop/Heading/Small/Semibolds` (extra "s"); see `base.md §2.6`.
7. **Generic variant names** — `_Pagination_BUttons` uses opaque names like `Frame 1410090391` instead of semantic names. Treat as layout slots; behaviour must be inferred from position.
8. **Breadcrumbs** is on a `Don't Use` page despite being treated as active by user override.

---

## 6. What this file does NOT contain (and where to find it)

- **Colour tokens (Brand, Neutral, Feedback, Surface, Gradient):** `base.md §1` — pointers in §1.1 above.
- **Text styles (Desktop / Mobile × Display / Heading / Body / Caption):** `base.md §2` — pointers in §1.2 above.
- **Variables ("Colors" collection):** `base.md §1`.
- **Detailed anatomy of non-default variants (Hover, Pressed, Disabled, Error, etc.):** not yet extracted — request a targeted re-extraction.
- **Spacing, radius, grid, breakpoint, motion tokens as a system:** not defined in either file at the token level; infer from the per-component anatomy above and ask before generalising.

When designing for web, your token vocabulary is **`base.md` + the 10 shadows in §2** and your component vocabulary is **§3** above. Nothing else.

---

## 7. Variant anatomy appendix

Detailed per-variant anatomy for every component. Each component section below is structured **by axis** (Size, Type, State) — because variants are combinatorial along these axes (e.g. Buttons = 4 Sizes × 5 Types × 4 States × Icon combos), per-axis tables compress thousands of individual variants into a small number of rules.

> **How to read:** find the row matching your target (e.g. `Primary / Hover / Medium`). All anatomy attributes not listed in a row inherit from the component's default in §3.

### 7.1 Buttons — full variant anatomy (272 variants → axis rules)

Every Button variant resolves to one row from each of the four axis tables below. Combine the rows to get the full spec.

**Constant across all variants:** `radius 8`, `gap 0` (text-only) or `gap 4` (with icons) or `gap 10` (only-icon), layout `HORIZONTAL`, `align CENTER/CENTER`.

#### 7.1.1 Size axis (governs height + padding + text style)

| Size           | Height | Padding `[T, R, B, L]`  | Text style                    | Only-Icon size | Only-Icon padding |
| -------------- | ------ | ----------------------- | ----------------------------- | -------------- | ----------------- |
| Small          | 32     | `[4, 14, 4, 14]`        | `Desktop/Body/Small/Medium`   | 32 × 32        | `[6, 6, 6, 6]`    |
| Medium         | 38     | `[10, 16, 10, 16]`      | `Desktop/Body/Medium/Medium`  | 38 × 38        | `[7, 7, 7, 7]`    |
| Large          | 44     | `[10, 16, 10, 16]`      | `Desktop/Body/Large/Medium`   | 44 × 44        | `[7, 7, 7, 7]`    |
| Extra Large    | 50     | `[10, 16, 10, 16]`      | `Desktop/Body/Large/Medium`   | 50 × 50        | `[7, 7, 7, 7]`    |

> When `Only Icon=True` AND `State=Disable`, Small grows to 34 × 34 with `[7, 7, 7, 7]` — file bug, but reproduce as-is.

#### 7.1.2 Type axis (governs default fill / stroke / effect / text fill)

| Type            | Fill                                 | Stroke              | Effect          | Text fill                       |
| --------------- | ------------------------------------ | ------------------- | --------------- | ------------------------------- |
| Primary         | `Brand/Primary`                      | —                   | —               | `Neutral/White`                 |
| Secondary       | `Neutral/White` *(Small uses `Brand/Gray/highContrast/700`)* | `Neutral/Stroke` (1px) | `Button Shadow` | `Neutral/Text`                  |
| Tertiary        | `Neutral/White`                      | `Brand/Primary` (1px) | `Button Shadow` | `Brand/Primary`                 |
| Quaternary      | none (transparent)                   | —                   | —               | `Brand/Gray/highContrast/700`   |
| Action Button   | `Neutral/White`                      | `Neutral/Stroke` (1px) | —             | — (icon-only, no text)          |

#### 7.1.3 State axis (overrides fill / effect; text fill follows)

| State          | Override fill                                                                                       | Override stroke                                | Add effect            | Override text fill |
| -------------- | --------------------------------------------------------------------------------------------------- | ---------------------------------------------- | --------------------- | ------------------ |
| Default        | per Type                                                                                            | per Type                                       | per Type              | per Type           |
| Hover          | Primary → `Brand/Dark/600`; Secondary/Tertiary/Action → `Brand/Light/100` (`Tertiary/Small` may use `#F5F8FF`); Quaternary → unchanged | Action Button (Small): → `Neutral/Disabled`    | drop Type's `Button Shadow` | unchanged           |
| While Pressed  | same as Hover                                                                                       | per Type                                       | `Button Shadow Hovered` | unchanged          |
| Disable        | **All Types collapse to `Neutral/Grey 1`** *(no stroke, no effect except Secondary/Tertiary keep `Button Shadow`)* | drop Type's stroke                             | drop or keep per Type | `Neutral/Sub Content` |

#### 7.1.4 Icon axis (governs width + gap)

Width grows in steps as icons are added. Height is unchanged. Gap goes from `0` (text-only) to `4` (with one or both side icons) to `10` (only-icon square). Default text-only width is 90 (Small/Medium with default `"Button"` label).

| Icon Left | Icon Right | Only Icon | Width (Small example)            | Gap |
| --------- | ---------- | --------- | -------------------------------- | --- |
| False     | False      | False     | 90                               | 0   |
| True      | False      | False     | ~+8 over text-only               | 4   |
| False     | True       | False     | ~+13 (text-only width 90 → 103)  | 0–4 |
| True      | True       | False     | ~+15 (90 → 105)                  | 4   |
| —         | —          | True      | square (32/38/44/50 by Size)     | 10  |
| NA        | NA         | N         | Action Button (square only)      | 10  |

> The Figma file uses both `False` and `NA` / both `True` and the combination toggles for "no icon" / "has icon" — semantically equivalent but bookkeeping differs by Type. Action Button always uses `Icon Left=NA, Icon Right=NA, Only Icon=N` (it's structurally only-icon).

#### 7.1.5 Drift / file bugs in Button variants

1. The "Tertiary / Small / Hover" variant uses a raw hex `#F5F8FF` instead of the token `Brand/Light/100` (`#F2F5F8`). Slight off-token — use the token in code.
2. "Secondary / Small / Default" uses `Brand/Gray/highContrast/700` (= `#FFFFFF`) for the surface fill while all larger sizes use `Neutral/White`. Same colour, different token — inconsistency.
3. "Only Icon=True / Disable / Small" grows to 34 × 34 with `[7,7,7,7]` padding while non-disabled Small only-icon is 32 × 32 with `[6,6,6,6]`. Likely a slip — but reproduce as-is.
4. "Quaternary / Hover" and "Quaternary / While Pressed" have **no fill change** in Figma (they remain transparent). If a hover affordance is needed in code, apply `Brand/Light/100` background ourselves and surface the gap to design.

### 7.2 Input Fields — full variant anatomy

Three core text-field sets (`_Text field`, `_pills_Text field`, `_+x, pills_Text field`) each carry **192 variants**: `State` × `Text-Config` × `Size` × `Alignment` × `Password?` × `Focused?`. Inside the variant is an inner `Input` frame that holds the visual treatment — that's what the rows below describe.

**Constant across all input variants:** input frame `radius 8`, layout `HORIZONTAL`, `gap 8`, left padding `12` (text field) or `16` (pills variants), stroke weight `1`. Outer wrapper layout is always `VERTICAL` with `gap 6` (label → input → supporting text).

#### 7.2.1 Size axis — `_Text field` (input frame heights)

| Size         | Outer h | Input h | Input pad `[T, R, B, L]`     |
| ------------ | ------- | ------- | ----------------------------- |
| Extra Small  | 53      | 32      | `[7, 0, 7, 12]`               |
| Small        | 59      | 38      | `[0, 0, 0, 12]` *(centered)*  |
| Large        | 65      | 44      | `[13.5, 0, 13.5, 12]`         |
| Extra Large  | 71      | 50      | `[15.5, 0, 15.5, 12]`         |

#### 7.2.2 Size axis — `_pills_Text field` (taller, pills inside)

| Size         | Outer h | Input h | Input pad `[T, R, B, L]`     |
| ------------ | ------- | ------- | ----------------------------- |
| Extra Small  | 88      | 67      | `[7, 16, 7, 16]`              |
| Small        | 95      | 74      | `[10.5, 16, 10.5, 16]`        |
| Large        | 101     | 80      | `[13.5, 16, 13.5, 16]`        |
| Extra Large  | 105     | 84      | `[15.5, 16, 15.5, 16]`        |

> `_+x, pills_Text field` shares pills-style padding but `Show Trailing Icon` defaults to `true` (`+x more` chip) and its default height is slightly smaller. Same axis rules otherwise.

#### 7.2.3 State axis (fill / stroke of the inner `Input` frame)

| State    | Fill            | Stroke            | Default effect (Text-Config=Placeholder) | Effect (Text-Config=Input) |
| -------- | --------------- | ----------------- | ---------------------------------------- | -------------------------- |
| Enabled  | `Neutral/White` | `Neutral/Stroke`  | —                                        | `Shadow/xs` *(library)*    |
| Disabled | `Neutral/Grey 2`| `Neutral/Stroke`  | —                                        | —                          |
| Error    | `Neutral/White` | `Error/Content` *(pills variants sometimes bind to `Primary/Red Stroke` library token — drift)* | `Input Box` | `Focused w/Error input Box` |

#### 7.2.4 Focused? axis (overrides effect)

| Focused? | Effect (Enabled state)   | Effect (Error state)      |
| -------- | ------------------------- | ------------------------- |
| No       | per Text-Config above     | per Text-Config above     |
| Yes      | `Focused Effect`          | `Focused Error Effect`    |

`Focused Effect` and `Focused Error Effect` are library effect styles (not in §2 — they're imported tokens). Map to a 2-3 px blue/red focus ring respectively.

#### 7.2.5 Alignment axis (label position)

| Alignment | Layout                                                                                       |
| --------- | -------------------------------------------------------------------------------------------- |
| Top       | Outer `VERTICAL`: label above input.                                                         |
| Left      | Outer `HORIZONTAL`: label to the left of input (anchor frame width grows accordingly).       |

No visual treatment change on the Input frame itself.

#### 7.2.6 Password? axis

| Password? | Effect on content                                                       |
| --------- | ----------------------------------------------------------------------- |
| False     | `Visible Text` (default placeholder `"Enter Placeholder Text Here"`).   |
| True      | `Hidden Text` (filled bullets) shows in place of plain text; trailing eye-toggle icon usually exposed via `Show Trailing?`. |

No box geometry change.

#### 7.2.7 Helper components on the Input Fields page

| Component           | Variants | Size | Notes                                                                      |
| ------------------- | -------- | ---- | -------------------------------------------------------------------------- |
| `Input Text field`  | 5        | 340 × 59 default | Wrapper: 5 variants `Default / pills / X More Pills / Disabled / x_pills (Disabled)` |
| `_swticher_icon`    | 2        | 16 × 16          | `indian-rupee` / `percent` — vector with stroke `Neutral/Text` 1.5 px      |
| `_Trailing-Type`    | 2        | 28 × 16          | `Trailing Icon` / `Switcher` — wraps a 16 × 16 icon with `pad [0, 12, 0, 0]` |
| `Scroll bar`        | 1        | 16 × 323         | Track 16w `pad [4, 4, 4, 4]`, inner bar 8w fill `#E5E7EB` `radius 8`       |
| `Pills` *(standalone)*       | n/a | 408 × 24 | Row of 4 pill badges, `gap 8`                                            |
| `Pills- Disabled` *(standalone)* | n/a | 256 × 21 | 3 pills                                                                |
| `x_Pills`           | n/a | 278 × 21 | Pills row + `+x more` overflow indicator                                   |
| `x_Pills - Disabled`| n/a | 278 × 21 | Disabled version of above                                                  |

#### 7.2.8 Drift / file bugs

1. `_pills_Text field` Error variants bind stroke to `Primary/Red Stroke` (library token), while `_Text field` uses `Error/Content` from `base.md`. Same red, different token — surface to design.
2. `Shadow/xs`, `Focused Effect`, `Focused Error Effect`, `Input Box`, `Focused w/Error input Box` are **library** effect styles, not the 10 `Pretty Shadows/*` in §2. Map to base subtle shadows + focus rings.
3. Three text-field sets (`_Text field` / `_pills_Text field` / `_+x, pills_Text field`) share the entire 192-variant axis matrix but differ only in inner content / padding scheme — choose by use-site need, never mix axes across sets.

### 7.3 Side Nav — full variant anatomy (31 variants)

#### 7.3.1 `_Nav Text Item` (12 variants — single icon rail item)

| Type      | State                 | W × H    | Fill            |
| --------- | --------------------- | -------- | --------------- |
| Collapsed | Inactive              | 64 × 56  | `Brand/Primary` |
| Collapsed | Active                | 64 × 56  | `Brand/Primary` |
| Collapsed | Active Solo Hover     | 64 × 56  | `Brand/Primary` |
| Collapsed | Hover                 | 64 × 56  | `Brand/Primary` |
| Collapsed | Active Expanded       | 64 × 252 | `Brand/Primary` |
| Collapsed | Active Expanded Hover | 64 × 56  | `Brand/Primary` |
| Collapsed | Expanded              | 64 × 252 | `Brand/Dark/600` |
| Open      | Inactive              | 164 × 56 | `Brand/Primary` |
| Open      | Hover                 | 164 × 56 | `Brand/Primary` |
| Open      | Active                | 165 × 56 | `Brand/Primary` *(1 px wider — file quirk)* |
| Open      | Active Expanded       | 164 × 252| `Brand/Primary` |
| Open      | Expanded              | 164 × 252| `Brand/Dark/600` *(non-active expanded uses darker rail)* |

All variants: `pad [4, 8, 4, 8]`, `gap 0`. Active states render an inner `Neutral/White` highlight bubble.

#### 7.3.2 `_Nav_menu_item` (5 variants — sub-menu row)

| State     | Type     | W × H     | Fill              | Radius |
| --------- | -------- | --------- | ----------------- | ------ |
| Open      | Inactive | 207 × 48  | `Brand/Dark/600`  | 4      |
| Open      | Hover    | 207 × 48  | `Brand/Primary`   | 4      |
| Open      | Active   | 207 × 48  | — (transparent)   | 4      |
| Collapsed | Inactive | 48 × 48   | — (transparent)   | 4      |
| Collapsed | Active   | 48 × 48   | — (transparent)   | 4      |

All `pad [12, 12, 12, 12]`, `gap 16`. Label text style `Desktop/Body/Large/Medium`, fill `Neutral/White`.

#### 7.3.3 `Nav Bar` (10 variants — full-height left rail)

| Variant                                                                                              | Width | Height | Fill              |
| ---------------------------------------------------------------------------------------------------- | ----- | ------ | ----------------- |
| `Variant9`, `Default`                                                                                | 64    | 1024   | `Brand/Primary`   |
| `Open`, `Accountant`, `Settings`, `Marketing`, `Sales`, `Purchase`, `Banking`, `Inventory`           | 250   | 1024   | `Brand/Primary`   |

The named variants (Accountant, Settings, etc.) are pre-populated with that module's nav items expanded — visual treatment identical, only inner content differs.

#### 7.3.4 `_Menu Item` (2 variants — expandable menu row)

| Type    | W × H    | Fill            |
| ------- | -------- | --------------- |
| Default | 176 × 40 | `Brand/Dark/600`|
| Hover   | 176 × 40 | `Neutral/White` |

`pad [11, 8, 11, 8]`, `gap 105`, `radius 6`. Label text style `Desktop/Body/Medium/Regular`. Default state text fill `Neutral/White`; Hover state inverts to dark text on white surface.

#### 7.3.5 `_Menu Listing` (2 variants — list container)

| Property 1     | W × H    | Notes                                |
| -------------- | -------- | ------------------------------------ |
| With Title     | 192 × 234| Vertical list with section heading   |
| Without Title  | 192 × 55 | Single-item compact list             |

### 7.4 Tabs — full variant anatomy (10 variants)

#### 7.4.1 `Tabs` (2 variants — underline-style)

Both 100 × 35, `pad [0, 16, 16, 16]` on the inner content row, `gap 4`. The visual difference between `Current=No / Yes` is the bottom-border colour (rectangle child 100 × 2): inactive vs. `Brand/Primary` underline for the current tab.

#### 7.4.2 `Filled Tab` (6 variants — pill-style)

| Active | State        | Type      | W × H    | Padding              | Fill            | Radius |
| ------ | ------------ | --------- | -------- | -------------------- | --------------- | ------ |
| False  | Placeholder  | Default   | 85 × 40  | `[11.5, 24, 11.5, 24]`| — (transparent) | —      |
| False  | Placeholder  | Icon only | 72 × 40  | `[10, 24, 10, 24]`   | — (transparent) | —      |
| False  | Placeholder  | Badg      | 111 × 47 | `[11.5, 24, 11.5, 24]`| — (transparent) | —      |
| True   | Focus        | Default   | 85 × 40  | `[11.5, 24, 11.5, 24]`| `Neutral/White` | 8      |
| True   | Focus        | Icon only | 72 × 40  | `[10, 24, 10, 24]`   | `Neutral/White` | 8      |
| True   | Focus        | Badg      | 111 × 47 | `[11.5, 24, 11.5, 24]`| `Neutral/White` | 8      |

All `gap 4`, label text style `Desktop/Body/Medium/Medium`.

#### 7.4.3 `Fill tab bar` (2 variants — container)

Both 466 × 52, `pad [6, 6, 6, 6]`, `gap 0`, `radius 8`, fill `Brand/Gray/lowContrast/a50` (`#6C849D @ 12%`). The two variants (`Icon only=True/False`) differ in what kind of `Filled Tab` they contain.

### 7.5 Pagination — full variant anatomy (9 variants)

#### 7.5.1 `_Pagination_BUttons` (5 variants — different button-row layouts)

| Property 1 (slot)        | W × H    | Use                                   |
| ------------------------ | -------- | ------------------------------------- |
| `Variant5`               | 116 × 32 | Compact: ≤ 3 visible page buttons      |
| `Frame 1410090391`       | 368 × 32 | Standard: ~7 page buttons              |
| `Frame 1410090392`       | 410 × 32 | Wider: with ellipsis or extra buttons  |
| `Frame 1410090393`       | 452 × 32 | Widest                                 |
| `Frame 1410090394`       | 452 × 32 | Widest (alt config)                    |

All `gap 10`. Internal page buttons are 32 × 32, `radius 8`. Active page button fill `Brand/Primary` (verified in default-anatomy section §3.7).

#### 7.5.2 `_Forward-Button` (2) and `_Backward-Button` (2)

Both sets have `Default` and directional variants — all 32 × 32, single-icon chevron buttons.

### 7.6 Calendar — full variant anatomy (22 variants)

#### 7.6.1 `Date Range picker` (2 variants — input + popover trigger)

| Property 1 | W × H    | Notes                                                                |
| ---------- | -------- | -------------------------------------------------------------------- |
| Default    | 302 × 38 | Closed state — input only                                            |
| clicked    | 302 × 38 | Open state — popover (724 × 508) rendered below; popover stroke `Brand/Light/100`, effect `Pretty Shadows/42` |

#### 7.6.2 `_calenderCell` (18 variants — day cell)

All cells: 32 × 32, `pad [5, 11, 5, 11]`, `gap 10`, `radius 6`.

| Type      | Position             | State    | Fill              |
| --------- | -------------------- | -------- | ----------------- |
| Inactive  | Leading/Trailing     | Default  | `Neutral/White`   |
| Inactive  | Leading/Trailing     | Hover    | `Brand/Light/100` |
| Inactive  | Leading/Trailing     | Disabled | `Neutral/White`   |
| Today     | Leading/Trailing     | Default  | `Brand/Light/400` |
| Today     | Leading/Trailing     | Hover    | `Brand/Light/400` |
| Today     | Leading/Trailing     | Disabled | `Neutral/White`   |
| Active    | Leading/Trailing     | Default  | `Brand/Primary`   |
| Active    | Leading/Trailing     | Hover    | `Brand/Primary`   |
| Active    | Leading/Trailing     | Disabled | `Neutral/Disabled`|
| Active    | Middle               | Default  | `Brand/Light/100` |
| Active    | Middle-Leading       | Default  | `Brand/Light/100` |
| Active    | Middle-Trailing      | Default  | `Brand/Light/100` |
| Active    | Middle               | Hover    | `Brand/Light/100` |
| Active    | Middle-Leading       | Hover    | `Brand/Light/100` |
| Active    | Middle-Trailing      | Hover    | `Brand/Light/100` |
| Active    | Middle               | Disabled | `Neutral/Disabled`|
| Active    | Middle-Leading       | Disabled | `Neutral/Disabled`|
| Active    | Middle-Trailing      | Disabled | `Neutral/Disabled`|

> Number text style `Desktop/Body/Medium/Regular`, fill `Neutral/Text` (default) or `Neutral/White` (on `Active` fills) or `Neutral/Disabled` (on disabled cells).

#### 7.6.3 `Calendar` (2 variants — full picker)

| Variant | W × H     | Notes                                                       |
| ------- | --------- | ------------------------------------------------------------ |
| Default | 248 × 344 | Single-month picker. `pad [12, 12, 12, 12]`, `gap 12`        |
| Range   | 488 × 344 | Two-month picker (range select). `pad [12, 12, 12, 12]`, `gap 16` |

Both: `radius 6`, fill `Neutral/White`, stroke `Brand/Light/100` (1 px), effect `Pretty Shadows/42`.

### 7.7 Breadcrumbs — full variant anatomy (4 variants in `_Breadcrumb button base`)

| Type | State   | W × H    | Notes                                        |
| ---- | ------- | -------- | -------------------------------------------- |
| Icon | Default | 20 × 20  | Single icon (typically `home`)               |
| Icon | Active  | 20 × 20  | Active state of icon                         |
| Text | Default | 89 × 20  | Text crumb (default text style + fill)       |
| Text | Active  | 89 × 20  | Active state of text crumb                   |

All `pad [0, 0, 0, 0]`, `gap 0`. The active/default distinction is in text fill: `Neutral/Sub Content` (default) vs `Neutral/Text` (active).

> Standalone `Breadcrumbs` bar (`693 × 44`) composes these crumbs with chevron separators; see §3.6.5 for the bar anatomy.

### 7.8 Modal / Popups — full variant anatomy (51 variants across 6 sets)

#### 7.8.1 `Modal/Popup` (9 variants — page-level overlay)

All 1440 × 1024 (full page). Dim overlay differs by carousel state:

| Type                    | With Photo? | With Carousel? | Page-dim fill   |
| ----------------------- | ----------- | -------------- | --------------- |
| With Form/Custom Content| False       | False          | `#192839 @ 50%` |
| With Form/Custom Content| True        | False          | `#192839 @ 50%` |
| With Form/Custom Content| False       | True           | `#39191A @ 50%` *(reddish dim)* |
| Confirmation            | False       | False          | `#192839 @ 50%` |
| Confirmation            | True        | False          | `#192839 @ 50%` |
| Confirmation            | False       | True           | `#192839 @ 50%` |
| Pop Alert               | False       | False          | `#192839 @ 50%` |
| Pop Alert               | True        | False          | `#192839 @ 50%` |
| Pop Alert               | False       | True           | `#39191A @ 50%` *(reddish dim)* |

> Reddish dim on Carousel variants is a file quirk — use the standard `#192839 @ 50%` (= `Neutral/Text` at 50%) in code unless red-tinted dim is intentional.

#### 7.8.2 `_Modal header` (3 variants — header strip)

All fill `Base / White` (library; map to `Neutral/White`).

| Type                       | W × H     |
| -------------------------- | --------- |
| Left aligned               | 400 × 175 |
| Center aligned             | 400 × 177 |
| Horizontal left aligned    | 400 × 131 |

#### 7.8.3 `_Featured icon` (24 variants — header icon decoration)

All variants: fill `Base/White` (lib → `Neutral/White`), stroke `Gray/200` (lib → `Neutral/Stroke`).

Size axis — square dimensions, radius, stroke weight:

| Size | W × H     | Radius | Stroke weight |
| ---- | --------- | ------ | ------------- |
| xs   | 24 × 24   | 4      | 1             |
| sm   | 32 × 32   | 6      | 1             |
| md   | 40 × 40   | 8      | 1             |
| lg   | 48 × 48   | 9.6    | 1.2           |

Type axis — inner icon and its stroke colour (icon glyph only — chrome stays the same):

| Type        | Inner icon            | Inner stroke colour      |
| ----------- | --------------------- | ------------------------ |
| Success     | `check-circle`        | `Success / 600` *(lib)*  |
| Warning     | `alert-triangle`      | `Warning / 600` *(lib)*  |
| Save        | `save`                | `Brand/Primary` *(lib)*  |
| Delete      | `trash-2`             | `Error/Content`          |
| Info        | `info`                | `Prediction/Content`     |
| Custom icon | instance-swap         | inherits                 |

> All 6 Types × 4 Sizes = 24 variants — anatomy table is the Cartesian product of the two axes above.

#### 7.8.4 `_Modal action-1` (2 variants — single-button footer)

Both 560 × 125, `pad [32, 0, 0, 0]`. The two variants are `Destructive=False/True` — the primary button's fill switches between `Brand/Primary` and `Error/Header` accordingly.

#### 7.8.5 `_Modal action-2` (1 variant — two-button horizontal footer)

560 × 125, `pad [32, 0, 0, 0]`. Two side-by-side 250 × 44 buttons separated by a 1 px divider.

#### 7.8.6 `_Modal actions` (12 variants — flexible button group)

Width depends on Breakpoint; height depends on Type:

| Type                                    | Breakpoint | W × H     | Padding top   |
| --------------------------------------- | ---------- | --------- | ------------- |
| Vertical fill container                 | Desktop    | 560 × 181 | 32            |
| Vertical fill container                 | Mobile     | 343 × 157 | 24            |
| Horizontal fill container               | Desktop    | 560 × 125 | 32            |
| Horizontal fill container               | Mobile     | 343 × 157 | 24            |
| Horizontal right aligned (checkbox)     | Desktop    | 560 × 125 | 32            |
| Horizontal right aligned (checkbox)     | Mobile     | 343 × 189 | 24            |

Each is duplicated for `Destructive=False/True` (12 variants total). Destructive flips the primary button fill to `Error/Header`.

> **Note on `Mobile` breakpoint:** these mobile variants live inside the web file — they're for responsive web layouts narrower than ~640 px, NOT for the native mobile app (`mobile.md`).

### 7.9 Checkboxes & Radio Buttons — full variant anatomy (42 + 42 variants)

Both sets share axes: `Size × State × Selected/Checked × With Text × Support Text`. The anchor below holds `With Text=No, Support Text=No` (visual treatment of the box itself).

#### 7.9.1 `Radio Buttons` (42 variants → axis rules)

**Sizes:**
- Small: outer 16 × 16, `_Checkbox base` 16 × 16, `radius 8` (full circle).
- Medium: outer 20 × 20, `_Checkbox base` 20 × 20, `radius 10`.

**State × Selected:**

| State    | Selected | Fill              | Stroke           |
| -------- | -------- | ----------------- | ---------------- |
| Default  | No       | `Neutral/White`   | `Neutral/Stroke` (1px) |
| Hover    | No       | `Brand/Light/100` | `Brand/Primary` (1px)  |
| Focused  | No       | `Neutral/White`   | `Brand/Primary` (1px)  |
| Disabled | No       | `Neutral/White`   | `Neutral/Stroke` (1px) |
| Default  | Yes      | `Brand/Light/100` | `Brand/Primary` (1px)  |
| Hover    | Yes      | `Brand/Light/100` | `Brand/Primary` (1px)  |
| Focused  | Yes      | `Brand/Light/100` | `Brand/Primary` (1px)  |
| Disabled | Yes      | `Brand/Light/100` | `Brand/Primary` (1px)  |

Selected state renders an inner filled dot (typically `Brand/Primary`). Multiply by `With Text` / `Support Text` for the remaining 28 variants (these only add outer label rows; the base box stays identical).

#### 7.9.2 `Checkboxes` (42 variants → axis rules)

**Sizes:**
- Small: outer 16 × 16, `_Checkbox base` 16 × 16, `radius 4`.
- Medium: outer 20 × 20, `_Checkbox base` 20 × 20, `radius 4` (some Hover/Focused variants render `radius 6` — minor file inconsistency).

**State × Checked:**

| State    | Checked | Fill              | Stroke           |
| -------- | ------- | ----------------- | ---------------- |
| Default  | No      | `Neutral/White`   | `Neutral/Stroke` (1px) |
| Hover    | No      | `Brand/Light/100` | `Brand/Primary` (1px)  |
| Focused  | No      | `Neutral/White`   | `Brand/Primary` (1px)  |
| Disabled | No      | `Neutral/White`   | `Neutral/Stroke` (1px) |
| Default  | Yes     | `Brand/Primary`   | `Brand/Primary` (1px)  |
| Hover    | Yes     | `Brand/Primary`   | `Brand/Primary` (1px)  |
| Focused  | Yes     | `Brand/Primary`   | `Brand/Primary` (1px)  |
| Disabled | Yes     | `Brand/Primary`   | `Brand/Primary` (1px)  |

Checked state renders an inner `check` icon glyph (typically `Neutral/White`).

> **The ONLY structural difference between a Checkbox and a Radio at the box level is `radius`: 4 (Checkbox) vs 8/10 (Radio).**

### 7.10 Toggle — full variant anatomy (64 variants across 3 sets)

#### 7.10.1 `Toggle` (60 variants — switch track + handle)

Axes: `Size × State × Status × Icon × With Text × Support Text`. The anchor below holds `Icon=No, With Text=No, Support Text=No` (the bare switch):

| Size  | State    | Status | W × H    |
| ----- | -------- | ------ | -------- |
| Small | Default  | On     | 36 × 20  |
| Small | Default  | Off    | 36 × 20  |
| Small | Focused  | On     | 36 × 20  |
| Small | Focused  | Off    | 36 × 20  |
| Small | Disable  | On     | 36 × 20  |
| Small | Disable  | Off    | 36 × 20  |

Track fill colour by `State × Status`:
- `Status=On, State=Default`: track fill `Brand/Primary`.
- `Status=On, State=Disable`: track fill `Neutral/Disabled`.
- `Status=Off, State=Default`: track fill `Neutral/Stroke`.
- `Status=Off, State=Disable`: track fill `Neutral/Disabled`.
- `State=Focused`: adds focus-ring effect (library `Focused Effect`).

Handle (knob): circle inside the track, fill `Neutral/White`, slides to left (`Off`) or right (`On`). When `Icon=Yes`, the knob carries an inner icon glyph.

`With Text=Yes Left` / `Yes Right` adds a label sibling beside the switch; `Support Text=Yes` adds a second-line caption below the label.

#### 7.10.2 `Option` (3 variants — single segmented-control segment)

All 71 × 26, `pad [8, 16, 8, 16]`, `gap 10`, `radius 8`.

| State    | Fill                |
| -------- | ------------------- |
| Default  | — (transparent)     |
| hover    | `Brand/Light/200`   |
| active   | `Brand/Primary`     |

Label text style `Desktop/Body/Small/Medium`, fill `Neutral/Text` (Default/Hover) or `Neutral/White` (Active).

#### 7.10.3 `OptionSwitcher` (1 variant — segmented-control container)

260 × 34, `pad [4, 4, 4, 4]`, `gap 4`, `radius 8`, fill `Neutral/White`, stroke `Neutral/Stroke` (1px). Holds 3 × `Option` segments.

### 7.11 Table — full variant anatomy (85 variants across 19 sets)

**Constants across every cell:**
- Outer cell h = 56; inner `Cell Content` h = 55; trailing 1px `Neutral/Stroke` rectangle as bottom border.
- Inner layout = `HORIZONTAL`, `gap 8` (except Type=Double-Line / Type7 use `gap 0`).
- Data cells: inner fill `Neutral/White`. Head cells: inner fill `Brand/Light/100`.

#### 7.11.1 Data cells — width × padding by Type

| Set                              | Variant                  | W    | Inner pad `[T, R, B, L]` |
| -------------------------------- | ------------------------ | ---- | ------------------------ |
| Table Cell - Text Based          | Type=Text                | 91   | `[16, 10, 16, 10]`       |
|                                  | Type=Double Line Text    | 95   | `[7, 10, 7, 10]`         |
|                                  | Type=Date                | 95   | `[16, 10, 16, 10]`       |
|                                  | Type=Date & Time         | 155  | `[16, 10, 16, 10]`       |
|                                  | Type=Numbers             | 140  | `[16, 42, 16, 10]` *(right-aligned, extra right pad)* |
| Table Cell - Icon Based          | Line=Single              | 127  | `[13, 10, 13, 10]`       |
|                                  | Line=Double              | 127  | `[1, 10, 1, 10]`         |
| Table Cell - Checkbox            | Single                   | 40   | `[13, 10, 13, 10]`       |
| Table Cell - Star                | Empty / Type2-4          | 45   | `[13, 10, 13, 10]`       |
| Table Cell - Toggle              | Single                   | 160  | `[13, 10, 13, 10]`       |
| Table Cell - Tick Untick         | Single / Line2           | 36   | `[13, 10, 13, 10]`       |
| Table Cell - Image Based         | With Out Description     | 139  | `[7, 10, 7, 10]`         |
|                                  | With Description         | 139  | `[7, 10, 7, 10]`         |
| Table Cell - Upload              | Upload / Uploaded / Change | 139 | `[7, 10, 7, 10]`         |
| Table Cell - Action Buttons      | Icon Based               | 261  | `[10, 10, 10, 10]`       |
| Table Cell - Special Input Field | (10 Type variants)       | 261  | `[10, 10, 10, 10]` *(Type7 uses gap 0)* |

#### 7.11.2 Badge cell widths by Type (`Table Cell - Badge` — 13 variants)

All `pad [10, 10, 10, 10]`. Widths vary with badge label length:

| Type                | Width |
| ------------------- | ----- |
| Failed              | 71    |
| Rejected            | 87    |
| Duplicate           | 91    |
| Reviewed            | 92    |
| Uploaded            | 92    |
| Failed + Icon       | 93    |
| Uploading           | 112   |
| Processing 1        | 118   |
| Reviewed Draft      | 124   |
| Discount            | 139   |
| Sucess *(sic)*      | 156   |
| Sucess with MD      | 176   |
| Type11              | 181   |

Per-type badge fill colour mirrors the Badge component family (§7.13 Badges) — Success → green wash, Failed/Rejected → red, Reviewed/Processing → blue, etc.

#### 7.11.3 Head cells — `Brand/Light/100` background

All head-cell sets share width 133 × height 56 with inner pad `[13, 10, 13, 10]`, inner fill `Brand/Light/100`, except where noted:

| Set                          | Variant                                              | Width | Notes                                  |
| ---------------------------- | ---------------------------------------------------- | ----- | -------------------------------------- |
| Head Cell - Sort             | State=Inactive/Active × Asc/Dsc=DSC/ASC (4 variants) | 133   | Sort indicator arrow per state         |
| Head Cell Numbers - Sort     | Same axis matrix (4 variants)                        | 133   | Right-aligned numeric sort             |
| Head Cell - Edit             | Active?=Closed/Opened (2 variants)                   | 207   | Wider — has edit + filter affordances  |
| Head Cell - Checkbox         | Closed × Yes                                         | 40    | Like a Checkbox data cell but `Brand/Light/100` fill |
| Head Cell - Sort Updated     | Inactive / Active                                    | 133   | Simplified sort header                 |
| Head Cell - Filter           | Inactive / Active / Opened                           | 133   | Filter popover trigger                 |

#### 7.11.4 Supplementary cell components

| Set / Standalone               | Variant                                                  | W × H    | Notes                                                 |
| ------------------------------ | -------------------------------------------------------- | -------- | ----------------------------------------------------- |
| `Favourites` (set)             | State=Default                                            | 25 × 25  | Star icon, no fill                                    |
|                                | State=Hover                                              | 25 × 25  | fill `Neutral/Grey 1` (highlight)                     |
|                                | State=Added                                              | 25 × 25  | filled star (`Brand/Primary` glyph)                   |
| `State` (set) — status dot     | False Positive / Pending Review / Confirmed Fraud / Under investigation / Default | 8 × 8 | 8×8 ellipse, fill bound to status colour:<br>• Default → `Success/Content`<br>• Pending Review → `Warning/Content`<br>• Confirmed Fraud / Under investigation → `Error/Content` (or stronger red)<br>• False Positive → `Neutral/Sub Content` |
| `Table Cell - Status` (standalone) | —                                                    | 139 × 56 | Status-pill wrapper — inner pad `[7, 10, 7, 10]`      |
| `_Before` (standalone)         | —                                                        | 112 × 32 | 3 × 32 × 32 action buttons, `gap 8`, `radius 8`, fill `Brand/Gray/highContrast/700`, stroke `Neutral/Stroke` |
| `_After` (standalone)          | —                                                        | 112 × 32 | Same as `_Before`                                     |

### 7.12 Dropdowns — full variant anatomy (44 variants across 6 sets)

#### 7.12.1 `dropdown menu` (4 variants — popover container)

All `radius 6`, effect `Pretty Shadows/99`, fill `#FFFFFF` (background section).

| Type             | W × H     |
| ---------------- | --------- |
| Org Switcher     | 344 × 708 |
| Normal           | 213 × 392 |
| Checkboxes       | 213 × 392 |
| Customer profile | 228 × 242 |

#### 7.12.2 `menu item` & `menu item - with badge` (17 variants each — anchor view)

All variants 236 × 32, `pad [6, 8, 6, 8]`, `gap 8`. State changes fill / radius:

| State    | Fill              | Radius |
| -------- | ----------------- | ------ |
| default  | `#FFFFFF`         | none   |
| disabled | `#FFFFFF`         | none   |
| hover    | `Brand/Light/100` | 6      |
| Selected | `Brand/Light/100` | 6      |

The `Type` axis (`Menu Item / Sub Menu Item / header`) changes indentation (Sub Menu Item adds left padding) and decorations. The `Size` axis (`Large / Small`) governs height (Small=32, Large=40 typical). `with badge` set adds an `Outled ID Badge?` slot on the right.

#### 7.12.3 `Menu List items` (2 variants — list container)

Both 236 × 288, `gap 8`, fill `#FFFFFF`.

| Type     | Inner padding `[T, R, B, L]` |
| -------- | ---------------------------- |
| Normal   | `[8, 0, 8, 0]`               |
| Checkbox | `[8, 0, 8, 0]`               |

#### 7.12.4 `Menu List items - with badge` (1 variant)

236 × 288, `pad [8, 8, 8, 8]`, `gap 8`, fill `#FFFFFF`. Type=Normal only.

#### 7.12.5 `Star` (3 variants — dropdown indicator dot)

All 22 × 22, no padding. Types `Type2 / Type3 / Type4` are stylistic variants of the star glyph.

### 7.13 Badges — full variant anatomy (7 + 2 = 9 variants)

#### 7.13.1 `Badges` (7 Type variants — pill-style chip)

All 170 × 24, `pad [4, 12, 4, 12]`, `gap 4`, `radius 72` (effectively pill).

| Type    | Fill                   |
| ------- | ---------------------- |
| Red     | `Error/BG` (`#FFF5F6`) |
| Blue    | `#E3EBFF` *(raw hex; no `base.md` token — closest match: `Prediction/BG` `#ECF4FF`)*    |
| Green   | `Success/BG`           |
| Purple  | `#F3E3FF` *(raw hex; no `base.md` token — flag for design)*          |
| Yellow  | `#FFFCF5` *(close to `Warning/BG` — actually identical)*             |
| Teal    | `#C1E2ED` *(raw hex; no `base.md` token)*                            |
| Default | `Neutral/Grey 1`       |

> **Drift:** Blue / Purple / Teal use raw hex backgrounds that have no `base.md` equivalent. When implementing, propose adding tokens (e.g. `Info/BG`, `Brand/Purple/BG`, `Brand/Teal/BG`) and surface to design.

#### 7.13.2 `Icon Badge` (2 State variants — small status dot with arrow)

Both 20 × 20, `pad [4, 4, 4, 4]`, `gap 4`, `radius 16` (full circle).

| State | Fill        | Inner icon       |
| ----- | ----------- | ---------------- |
| Up    | `Success/BG`| `icon/arrow-up`  |
| Down  | `Error/BG`  | `icon/arrow-down`|

### 7.14 Toaster — full variant anatomy (5 Type variants)

All 411 × 66, `pad [16, 40, 16, 16]`, `gap 9`, `radius 8`, effect `Pretty Shadows/98`.

| Type           | Fill        | `base.md` token equivalent |
| -------------- | ----------- | --------------------------- |
| Sucess *(sic)* | `#EFFDF3`   | ~ `Success/BG` `#ECFDF3` *(off-token — flag)*    |
| Warning        | `#FFFCF1`   | ~ `Warning/BG` `#FFFCF5` *(off-token — flag)*    |
| Info           | `#F1F8FE`   | ~ `Prediction/BG` `#ECF4FF` *(off-token — flag)* |
| Error          | `#FCF0F0`   | ~ `Error/BG` `#FFF5F6` *(off-token — flag)*      |
| Neutral        | `#FFFFFF`   | `Neutral/White`             |

> All Toast types use **raw hex** fills that are 2–4 hex steps off the `base.md` status `BG` tokens. **In code, use the `base.md` tokens; don't reproduce the slight off-shades.** Surface as design drift.

### 7.15 Tooltip — full variant anatomy (6 Position variants)

| Position        | W × H    | Internal `gap` (caret offset) | Notes                                  |
| --------------- | -------- | ----------------------------- | -------------------------------------- |
| Center          | 282 × 59 | −6                            | Caret on top edge, body below          |
| Bottom          | 282 × 59 | −6                            | Caret on bottom edge, body above       |
| Left            | 282 × 59 | −6                            | Caret on right edge, body to the left  |
| Right           | 282 × 59 | −6                            | Caret on left edge, body to the right  |
| Position Left   | 291 × 52 | −4                            | Off-center variant — caret at one end  |
| Position Right  | 291 × 52 | −4                            | Off-center variant — caret at other end |

Body always: `pad [6, 6, 6, 6]`, `gap 10`, `radius 5`, fill `Neutral/Text` (`#192839`). Tooltip text style `Desktop/Body/Small/Regular`, fill `Neutral/White`.

### 7.16 Side Drawers — full variant anatomy (4 variants in `Side Drawer`)

All fill `Neutral/White`, layout `VERTICAL`, height 1024, full bleed.

| Type     | Supporting Text | W   | Header fill          | `gap` (between header+footer) |
| -------- | --------------- | --- | -------------------- | ----------------------------- |
| Normal   | False           | 518 | `Brand/Light/200`    | 863                           |
| Special  | False           | 518 | `Brand/Light/200`    | 863                           |
| Normal   | True            | 529 | `Brand/Light/200`    | 592                           |
| Special  | True            | 529 | `Brand/Light/200`    | 592                           |

`Supporting Text=True` adds a sub-heading row in the header (drawer grows ~11 px wider, the inner content takes less of the `gap` due to additional header height).

> Header / body / footer pads: header `pad [26, 32, 26, 32]`, body `pad [24, 32, 24, 32]`, footer `pad [17, 32, 17, 32]`. Footer fill also `Brand/Light/200`.

Standalone content components (`_SPL Drawer Content`, `_Drawer Content`, `Add Party`) are pre-arranged content layouts that plug into the drawer body (454 wide × 828 tall, vertical layout).

### 7.17 Loaders — full variant anatomy (4 frames in `Spinner-Round/Spinner-Round-05`)

| Property 1 | W × H   | Notes                                                         |
| ---------- | ------- | ------------------------------------------------------------- |
| 1          | 22 × 22 | Spinner frame 1 — indicator at 0°                             |
| 2          | 22 × 22 | Spinner frame 2 — indicator at 90°                            |
| 3          | 22 × 22 | Spinner frame 3 — indicator at 180°                           |
| 4          | 22 × 22 | Spinner frame 4 — indicator at 270°                           |

The 4 variants are animation keyframes — rotate through them at ~150 ms / frame for a smooth spin. Composed of two overlapping 17 × 17 ellipses (track + indicator).

### 7.18 Stepper / Horizontal Progress Bar — full variant anatomy (12 variants across 2 sets)

#### 7.18.1 `Progress bar Local component` (3 variants — single step + connector)

All 159 × 60, layout `HORIZONTAL`, `gap 8`. The 3 variants are stylistic states of the whole step + connector line:

| Property 1 | Connector line stroke |
| ---------- | --------------------- |
| Active     | `Brand/Primary`       |
| Disabled   | `Neutral/Disabled`    |
| Success    | `Success/Content`     |

Inner step indicator (a `States` instance) carries the colour for the dot; line `Neutral/Disabled` connects to the next step.

#### 7.18.2 `States` (9 variants — step indicator dot)

All 25 × 25.

| Type   | State    | Layout              | Fill              | Notes                              |
| ------ | -------- | ------------------- | ----------------- | ---------------------------------- |
| Number | Active   | `pad [10,10,10,10]` | `Brand/Primary`   | White number inside                |
| Number | Success  | `pad [10,10,10,10]` | `Success/Content` | White number inside                |
| Number | Disabled | `pad [10,10,10,10]` | `Neutral/Disabled`| Muted number inside                |
| Tick   | Active   | `gap 12.5, radius 12.5` | —              | Tick glyph inside, no chrome       |
| Tick   | Success  | `pad [10,10,10,10]` | `Success/Content` | White tick inside                  |
| Tick   | Disabled | `pad [10,10,10,10]` | `Neutral/Disabled`| Muted tick inside                  |
| Icon   | Active   | `gap 12.5, radius 12.5` | —              | Icon glyph inside, no chrome       |
| Icon   | Success  | `gap 12.5, radius 12.5` | —              | Icon glyph inside, no chrome       |
| Icon   | Disabled | `gap 12.5, radius 12.5` | —              | Icon glyph inside, no chrome       |

All numbered/ticked filled-dot states use `radius 99` (full circle).

### 7.19 POS Billing Screen — full variant anatomy (12 variants across 3 sets)

#### 7.19.1 `Cart Items` (3 State variants — cart row)

All 642 wide, layout `VERTICAL`, `gap 12`, fill `#FFFFFF`.

| State        | Height | Radius |
| ------------ | ------ | ------ |
| Default      | 56     | —      |
| Expanded     | 196    | 8      |
| with variant | 195    | 8      |

#### 7.19.2 `Cart Section` (6 State variants — full cart panel)

All 666 × 953, fill `Neutral/White`.

| State                      | Notes                                     |
| -------------------------- | ----------------------------------------- |
| Empty State                | Empty cart illustration + CTA             |
| Empty with item            | Single-item cart, charges section closed  |
| Items added Closed         | Multi-item cart, charges section closed   |
| Charges Open               | Multi-item cart, charges drawer expanded  |
| empty with charges open    | Charges expanded with no items            |
| combo                      | Cart contains a combo item                |

All states share the same outer dimensions — content varies inside.

#### 7.19.3 `Item Listing` (3 variants — product tile)

All 130 × 88, `pad [8, 8, 8, 8]`, `gap 8`, `radius 8`, fill `Neutral/White`, stroke `Brand/Light/100` (1 px).

| Property 1 | Notes                                  |
| ---------- | -------------------------------------- |
| Default    | Single product                         |
| combo      | Combo product (badge indicator)        |
| variant    | Product with size/variant indicator    |

### 7.20 POS Header — full variant anatomy (3 State variants)

All 1440 × 75, `pad [16, 32, 16, 32]`, `gap 1029`, fill `Neutral/White`, stroke `Neutral/Stroke`.

| State    | Notes                                     |
| -------- | ----------------------------------------- |
| Default  | Normal POS operating state                |
| Login    | Login / not-yet-authenticated state       |
| Day End  | Closing-of-day state with summary actions |

All 3 share identical chrome — content of the right-side action group changes per state.

### 7.21 Sub-Sidemenu — full variant anatomy (2 State variants in `_List_item`)

Both 226 × 44, `pad [0, 24, 0, 24]`, layout `VERTICAL`.

| State    | Fill              |
| -------- | ----------------- |
| Inactive | — (transparent)   |
| Active   | `Brand/Light/100` |

The outer `Sub Side Menu` standalone (270 × 997, vertical) holds many `_List_item` rows + section headers + a `Drawer` shadow effect.

### 7.22 Slider / Range — full variant anatomy (2 standalone components)

Both 256 × 8, `radius 4`, track fill `Brand/Light/300`.

| Component        | Fill range frame                  | Use                                 |
| ---------------- | --------------------------------- | ----------------------------------- |
| `Slider / Range` | inner 135 × 8 (no fill)           | Two-handle range slider             |
| `Slider / Value` | inner 83 × 8, radius 4, fill `Brand/Primary` | Single-value slider with filled progress portion |

### 7.23 Top Nav — full variant anatomy

Single standalone component (no variants) — `Top NavBar` 1440 × 64, `pad [0, 20, 0, 88]`, `gap 1026`, fill `#FFFFFF`. Logo group on left (112 × 37), action group on right (573 × 64, `gap 12`).

### 7.24 Filters — full variant anatomy (2 standalone components, no variants)

| Component   | W × H     | Fill              | Stroke            | Effect          | Notes                                   |
| ----------- | --------- | ----------------- | ----------------- | --------------- | --------------------------------------- |
| `Filter`    | 252 × 330 | `#FFFFFF`         | —                 | `Filter Shadow` | `radius 8`, `gap 21`, vertical          |
| `Date & Time` | 406 × 386 | `Neutral/White` | `Neutral/Stroke` (1px) | `Filter Shadow` | `radius 12`, vertical, with 56-px header, 268-px body, 62-px footer rows |

---

## 8. Summary — what got extracted

- **All 1,500+ variants** across 23 active component families compressed into axis-rule tables in §7.
- Every variant's fill / stroke / effect / size / padding is captured, either explicitly (in tables) or implicitly (anchor + axis delta).
- Drift between Figma values and `base.md` tokens is flagged inline at every occurrence (look for ⚠️ / "drift" / "off-token").
- Components with effectively infinite variant content (Icons: 2,422) are summarised under naming rules (§3.23) — query Figma when a specific glyph is needed.

When you need a spec for a specific (component, axis combination) that isn't covered above, the data is in Figma — request a targeted re-extraction by component + variant key (e.g. "Button / Tertiary / Hover / Large with icon-right").

