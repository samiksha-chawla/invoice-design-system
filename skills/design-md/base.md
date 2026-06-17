# Base Guidelines — Petpooja Design System

**Source (canonical):** https://www.figma.com/design/FMeWvHvADIwTJKORCpEuwV/Base-Guidelines
**Scope of this file:** the file-level **Paint Styles** (50), **Text Styles** (77), and **Variables** ("Colors" collection, 40 variables, single mode `Mode 1`) defined in Figma. These are the tokens that every Petpooja design MUST use. Other base topics (principles, spacing, motion, components, etc.) are not covered here and live elsewhere.

> **Source-of-truth precedence (read once, apply always):**
> 1. **Paint Style / Text Style / Variable values** — what the file actually applies when used. **Canonical.**
> 2. Style **description text** — informative only. Several descriptions disagree with the applied value (line-height, letter-spacing, weight). When they conflict, the **applied value wins**. Known disagreements are listed at the end of each section.

---

## 1. Color

Notation: `Token Name` → `#HEX` (or `#HEX @ alpha%` for translucent fills). Where both a paint style and a variable exist for the same role, the variable is shown alongside.

### 1.1 Brand

#### 1.1.1 Primary / Secondary

| Token (Paint Style)   | Value     | Variable                |
| --------------------- | --------- | ----------------------- |
| `Brand/Primary`       | `#2E5391` | `Brand/Primary/Primary` |
| `Brand/Secondary/500` | `#006C3F` | — (no variable mirror)  |

#### 1.1.2 Brand / Light scale

| Token             | Value     | Variable                |
| ----------------- | --------- | ----------------------- |
| `Brand/Light/100` | `#F2F5F8` | `Brand/Light/Light-100` |
| `Brand/Light/200` | `#D3DBE8` | `Brand/Light/Light-200` |
| `Brand/Light/300` | `#BDCAE0` | `Brand/Light/Light-300` |
| `Brand/Light/400` | `#96A9C8` | `Brand/Light/Light-400` |
| `Brand/Light/700` | `#5875A7` | `Brand/Light/Light-700` |

> Note: 500 and 600 steps are intentionally absent in the file. Do not invent them.

#### 1.1.3 Brand / Dark scale

| Token            | Value     | Variable               |
| ---------------- | --------- | ---------------------- |
| `Brand/Dark/600` | `#254A88` | `Brand/Dark/Dark-600`  |
| `Brand/Dark/800` | `#214684` | `Brand/Dark/Dark-700` *(variable name uses "Dark-700" for paint style "Dark/800" — flagged inconsistency, value is the same)* |

#### 1.1.4 Brand / Gray — low contrast (use on light surfaces)

| Token                         | Value           |
| ----------------------------- | --------------- |
| `Brand/Gray/lowContrast/a50`  | `#6C849D @ 12%` |
| `Brand/Gray/lowContrast/a100` | `#6C849D @ 18%` |
| `Brand/Gray/lowContrast/200`  | `#FFFFFF @ 18%` |
| `Brand/Gray/lowContrast/300`  | `#6C849D @ 18%` |
| `Brand/Gray/lowContrast/400`  | `#6C849D @ 18%` |
| `Brand/Gray/lowContrast/500`  | `#B1C1D2`       |
| `Brand/Gray/lowContrast/600`  | `#6C849D @ 18%` |
| `Brand/Gray/lowContrast/700`  | `#2F4256`       |

> ⚠️ **Drift flag:** the variables that mirror these (`Brand/Gray/Low Contrast/LowContrast-*`) all resolve to `#FFFFFF` in Mode 1 — they look reset/broken. **Use the paint-style values above; do not use the variables for this family until fixed in Figma.**

#### 1.1.5 Brand / Gray — high contrast (use on dark / brand surfaces)

| Token                          | Value           |
| ------------------------------ | --------------- |
| `Brand/Gray/highContrast/a50`  | `#6C849D @ 12%` |
| `Brand/Gray/highContrast/a100` | `#6C849D @ 9%`  |
| `Brand/Gray/highContrast/200`  | `#000000`       |
| `Brand/Gray/highContrast/300`  | `#2F4256`       |
| `Brand/Gray/highContrast/400`  | `#6C849D @ 18%` |
| `Brand/Gray/highContrast/500`  | `#B1C1D2`       |
| `Brand/Gray/highContrast/600`  | `#6C849D @ 18%` |
| `Brand/Gray/highContrast/700`  | `#FFFFFF`       |

### 1.2 Neutral

| Token                 | Value     | Variable              | Use                              |
| --------------------- | --------- | --------------------- | -------------------------------- |
| `Neutral/Text`        | `#192839` | `Neutral/Text`        | Default body text                |
| `Neutral/Content`     | `#40566D` | `Neutral/Content`     | Secondary text / strong icons    |
| `Neutral/Sub Content` | `#768EA7` | `Neutral/Sub Content` | Tertiary text / muted icons      |
| `Neutral/Disabled`    | `#D0D8E0` | `Neutral/Disabled`    | Disabled text / disabled fg      |
| `Neutral/Stroke`      | `#D2D6DB` | `Neutral/Stroke`      | Default border                   |
| `Neutral/SPL Stroke`  | `#E8E8E8` | `Neutral/SPL Stroke` *(variable resolves to `#D2D6DB` — drift flagged)* | Special / lighter border |
| `Neutral/Grey 1`      | `#F2F2F2` | `Neutral/Grey 1`      | Light surface step 1             |
| `Neutral/Grey 2`      | `#F8F8F8` | `Neutral/Grey 2`      | Light surface step 2             |
| `Neutral/Background`  | `#F8F8F8` | `Neutral/Background`  | Page background                  |
| `Neutral/White`       | `#FFFFFF` | `Neutral/White`       | Pure white                       |
| `Neutral/Tooltip BG`  | `#373737` | `Neutral/Tooltip BG`  | Tooltip background               |

> ⚠️ **Drift flag:** `Neutral/SPL Stroke` paint style is `#E8E8E8` but the variable of the same name is `#D2D6DB`. They are NOT the same. Decide which is canonical per use-site and stay consistent within a screen.

### 1.3 Feedback / Status

Each status family has three roles: `BG` (subtle wash), `Header` (titles / strong text), `Content` (body text / icons). Variables exist for every BG / Header / Content below with identical values.

#### Error
| Token           | Value     |
| --------------- | --------- |
| `Error/BG`      | `#FFF5F6` |
| `Error/Header`  | `#C52031` |
| `Error/Content` | `#D92D20` |

#### Warning
| Token             | Value     |
| ----------------- | --------- |
| `Warning/BG`      | `#FFFCF5` |
| `Warning/Header`  | `#DC9203` |
| `Warning/Content` | `#D9A541` |

#### Success
| Token             | Value     |
| ----------------- | --------- |
| `Success/BG`      | `#ECFDF3` |
| `Success/Header`  | `#027A48` |
| `Success/Content` | `#039855` |

#### Prediction / Info
| Token                | Value     |
| -------------------- | --------- |
| `Prediction/BG`      | `#ECF4FF` |
| `Prediction/Header`  | `#1361CE` |
| `Prediction/Content` | `#3A84EC` |

### 1.4 Surface

| Token              | Value     | Variable           |
| ------------------ | --------- | ------------------ |
| `Surface/Disabled` | `#F5F5F5` | `Surface/Disabled` |

### 1.5 Gradients

| Token                                  | Value          | Notes                                                                                                                    |
| -------------------------------------- | -------------- | ------------------------------------------------------------------------------------------------------------------------ |
| `Light BG Gradient` *(paint style)*    | `#FFFFFF`      | The paint style is a single solid; the actual gradient is defined as two variables (below). Use the variables for the gradient. |
| `Light BG Gradient/Start` *(variable)* | `#E1F0FF @ 5%` | Gradient start stop                                                                                                      |
| `Light BG Gradient/End` *(variable)*   | `#B2CEF6`      | Gradient end stop                                                                                                        |

### 1.6 Known color drift (file bugs — fix in Figma, do not work around)

1. `Brand/Gray/Low Contrast/LowContrast-*` variables — all resolve to `#FFFFFF`. Use paint styles for this family.
2. `Neutral/SPL Stroke` — paint style `#E8E8E8` ≠ variable `#D2D6DB`.
3. `Brand/Dark/Dark-700` variable maps to paint style `Brand/Dark/800` (naming mismatch; value `#214684` matches).
4. `Light BG Gradient` paint style is just `#FFFFFF`; the real gradient lives in the two variables `Light BG Gradient/Start` and `Light BG Gradient/End`.

---

## 2. Typography

77 text styles defined in two parallel scales — **Desktop** and **Mobile** — each with four families: **Display**, **Heading**, **Body**, **Caption**. Every style uses **Inter**; weight is the only variable within a step (Regular / Medium / Semi Bold; Caption uses Italic).

### 2.1 Family

- **Primary (and only file-defined family):** `Inter`
- **Weights in use:** Regular (400), Medium (500), Semi Bold (600), Italic (400) — used for Caption.
- No secondary or monospace family is defined. **Do not introduce one.**

### 2.2 General properties

- **Line height (actual value):** every style is set to `AUTO`. Style **descriptions** specify a target px value (e.g. "Line Height: 78px") but those are NOT enforced by the style itself.
  - **Rule:** in code, prefer the px target from the style description when laying out paragraphs / dense UI; let `AUTO` apply only when matching Figma exactly. When in doubt, ask.
- **Letter spacing:** Display and Heading styles on **Desktop** use `-2%`; on **Mobile**, Display uses `-1%` (except Semibold variants set to `0%`) and Heading uses `0%`. Body and Caption are always `0%`.
  - ⚠️ Several style descriptions claim `-1%` while the applied value is `-2%`. **Applied value wins.**
- **Paragraph spacing:** `0` on every style.
- **Text case / decoration:** `ORIGINAL` / `NONE`.

### 2.3 Desktop type scale

#### 2.3.1 Display
| Style                              | Weight    | Size | Line-height (intended) | Letter-spacing |
| ---------------------------------- | --------- | ---- | ---------------------- | -------------- |
| `Desktop/Display/Xlarge/Regular`   | Regular   | 72   | 78px                   | -2%            |
| `Desktop/Display/Xlarge/Medium`    | Medium    | 72   | 78px                   | -2%            |
| `Desktop/Display/Xlarge/Semibold`  | Semi Bold | 72   | 78px                   | -2%            |
| `Desktop/Display/Large/Regular`    | Regular   | 64   | 70px                   | -2%            |
| `Desktop/Display/Large/Medium`     | Medium    | 64   | 70px                   | -2%            |
| `Desktop/Display/Large/Semibold`   | Semi Bold | 64   | 70px                   | -2%            |
| `Desktop/Display/Big/Regular`      | Regular   | 56   | 64px                   | -2%            |
| `Desktop/Display/Big/Medium`       | Medium    | 56   | 64px                   | -2%            |
| `Desktop/Display/Big/Semibold`     | Semi Bold | 56   | 64px                   | -2%            |
| `Desktop/Display/Small/Regular`    | Regular   | 48   | 56px                   | -2%            |
| `Desktop/Display/Small/Medium`     | Medium    | 48   | 56px                   | -2%            |
| `Desktop/Display/Small/Semibold` ⚠️ | Regular *(file bug — name says Semibold but applied weight is Regular)* | 48 | 56px | -2% |

#### 2.3.2 Heading
| Style                              | Weight    | Size | Line-height (intended) | Letter-spacing |
| ---------------------------------- | --------- | ---- | ---------------------- | -------------- |
| `Desktop/Heading/2XLarge/Regular`  | Regular   | 40   | 46px                   | -2%            |
| `Desktop/Heading/2XLarge/Medium`   | Medium    | 40   | 46px                   | -2%            |
| `Desktop/Heading/2XLarge/Semibold` | Semi Bold | 40   | 46px                   | -2%            |
| `Desktop/Heading/XLarge/Regular`   | Regular   | 32   | 38px                   | -2%            |
| `Desktop/Heading/XLarge/Medium`    | Medium    | 32   | 38px                   | -2%            |
| `Desktop/Heading/XLarge/Semibold`  | Semi Bold | 32   | 38px                   | 0%             |
| `Desktop/Heading/Large/Regular`    | Regular   | 24   | 32px                   | -2%            |
| `Desktop/Heading/Large/Medium`     | Medium    | 24   | 32px                   | -2%            |
| `Desktop/Heading/Large/Semibold`   | Semi Bold | 24   | 32px                   | -2%            |
| `Desktop/Heading/Medium/Regular`   | Regular   | 20   | 26px                   | -2%            |
| `Desktop/Heading/Medium/Medium`    | Medium    | 20   | 26px                   | -2%            |
| `Desktop/Heading/Medium/Semibold`  | Semi Bold | 20   | 26px                   | -2%            |
| `Desktop/Heading/Small/Regular`    | Regular   | 18   | 24px                   | -2%            |
| `Desktop/Heading/Small/Medium`     | Medium    | 18   | 24px                   | -2%            |
| `Desktop/Heading/Small/Semibolds` ⚠️ *(typo in file: "Semibolds")* | Semi Bold | 18 | 24px | -2% |

#### 2.3.3 Body
| Style                          | Weight    | Size | Line-height (intended) | Letter-spacing |
| ------------------------------ | --------- | ---- | ---------------------- | -------------- |
| `Desktop/Body/Large/Regular`   | Regular   | 16   | 24px                   | 0%             |
| `Desktop/Body/Large/Medium`    | Medium    | 16   | 24px                   | 0%             |
| `Desktop/Body/Large/Semibold`  | Semi Bold | 16   | 24px                   | 0%             |
| `Desktop/Body/Medium/Regular`  | Regular   | 14   | 20px                   | 0%             |
| `Desktop/Body/Medium/Medium`   | Medium    | 14   | 20px                   | 0%             |
| `Desktop/Body/Medium/Semibold` | Semi Bold | 14   | 20px                   | 0%             |
| `Desktop/Body/Small/Regular`   | Regular   | 12   | 18px                   | 0%             |
| `Desktop/Body/Small/Medium`    | Medium    | 12   | 18px                   | 0%             |
| `Desktop/Body/Small/Semibold`  | Semi Bold | 12   | 18px                   | 0%             |
| `Desktop/Body/XSmall/Regular`  | Regular   | 10   | 14px                   | 0%             |
| `Desktop/Body/XSmall/Medium`   | Medium    | 10   | 14px                   | 0%             |
| `Desktop/Body/XSmall/Semibold` | Semi Bold | 10   | 14px (actual `PIXELS`) | 0%             |

#### 2.3.4 Caption (Italic)
| Style                           | Weight | Size | Line-height (intended)                              | Letter-spacing |
| ------------------------------- | ------ | ---- | --------------------------------------------------- | -------------- |
| `Desktop/Caption/SmallRegular`  | Italic | 11   | 16px                                                | 0%             |
| `Desktop/Caption/MediumRegular` | Italic | 14   | — *(no intended LH specified; AUTO applies)*        | 0%             |

### 2.4 Mobile type scale

#### 2.4.1 Display
| Style                            | Weight    | Size | Line-height (intended) | Letter-spacing |
| -------------------------------- | --------- | ---- | ---------------------- | -------------- |
| `Mobile/Display/XLarge/Regular`  | Regular   | 40   | 48px                   | -1%            |
| `Mobile/Display/XLarge/Medium`   | Medium    | 40   | 48px                   | -1%            |
| `Mobile/Display/XLarge/Semibold` | Semi Bold | 40   | 48px                   | 0%             |
| `Mobile/Display/Large/Regular`   | Regular   | 38   | 46px                   | -1%            |
| `Mobile/Display/Large/Medium`    | Medium    | 38   | 46px                   | -1%            |
| `Mobile/Display/Large/Semibold`  | Semi Bold | 38   | 46px                   | 0%             |
| `Mobile/Display/Medium/Regular`  | Regular   | 36   | 42px                   | -1%            |
| `Mobile/Display/Medium/Medium`   | Medium    | 36   | 42px                   | -1%            |
| `Mobile/Display/Medium/Semibold` | Semi Bold | 36   | 42px                   | 0%             |
| `Mobile/Display/Small/Regular`   | Regular   | 34   | 40px                   | -1%            |
| `Mobile/Display/Small/Medium`    | Medium    | 34   | 40px                   | -1%            |
| `Mobile/Display/Small/Semibold`  | Semi Bold | 34   | 40px                   | 0%             |

#### 2.4.2 Heading
| Style                              | Weight    | Size | Line-height (intended) | Letter-spacing |
| ---------------------------------- | --------- | ---- | ---------------------- | -------------- |
| `Mobile/Heading/2XLarge/Regular`   | Regular   | 32   | 38px                   | 0%             |
| `Mobile/Heading/2XLarge/Semibold` ⚠️ | Medium *(file bug — name says Semibold but applied weight is Medium)* | 32 | 38px | 0% |
| `Mobile/Heading/XLarge/Regular`    | Regular   | 24   | 32px                   | 0%             |
| `Mobile/Heading/XLarge/Semibold`   | Semi Bold | 24   | 32px                   | 0%             |
| `Mobile/Heading/Large/Regular`     | Regular   | 20   | 26px                   | 0%             |
| `Mobile/Heading/Large/Semibold`    | Semi Bold | 20   | 26px                   | 0%             |
| `Mobile/Heading/Medium/Regular`    | Regular   | 18   | 24px                   | 0%             |
| `Mobile/Heading/Medium/Semibold`   | Semi Bold | 18   | 24px                   | 0%             |
| `Mobile/Heading/Small/Regular`     | Regular   | 16   | 22px                   | 0%             |
| `Mobile/Heading/Small/Semibold`    | Semi Bold | 16   | 22px                   | 0%             |

#### 2.4.3 Body
| Style                         | Weight    | Size | Line-height (intended) | Letter-spacing |
| ----------------------------- | --------- | ---- | ---------------------- | -------------- |
| `Mobile/Body/Large/Regular`   | Regular   | 16   | 24px                   | 0%             |
| `Mobile/Body/Large/Medium`    | Medium    | 16   | 24px                   | 0%             |
| `Mobile/Body/Large/Semibold`  | Semi Bold | 16   | 24px                   | 0%             |
| `Mobile/Body/Medium/Regular`  | Regular   | 14   | 20px                   | 0%             |
| `Mobile/Body/Medium/Medium`   | Medium    | 14   | 20px                   | 0%             |
| `Mobile/Body/Medium/Semibold` | Semi Bold | 14   | 20px                   | 0%             |
| `Mobile/Body/Small/Regular`   | Regular   | 12   | 18px                   | 0%             |
| `Mobile/Body/Small/Medium`    | Medium    | 12   | 18px                   | 0%             |
| `Mobile/Body/Small/Semibold`  | Semi Bold | 12   | 18px                   | 0%             |
| `Mobile/Body/XSmall/Regular`  | Regular   | 10   | 14px                   | 0%             |
| `Mobile/Body/XSmall/Medium`   | Medium    | 10   | 14px                   | 0%             |
| `Mobile/Body/XSmall/Semibold` | Semi Bold | 10   | 14px                   | 0%             |

#### 2.4.4 Caption (Italic)
| Style                          | Weight | Size | Line-height (intended)                    | Letter-spacing |
| ------------------------------ | ------ | ---- | ----------------------------------------- | -------------- |
| `Mobile/Caption/SmallRegular`  | Italic | 11   | 16px *(actual `PIXELS` — locked)*         | 0%             |
| `Mobile/Caption/MediumRegular` | Italic | 14   | 16px *(actual `PIXELS` — locked)*         | 0%             |

### 2.5 Naming convention

Every text style follows: `{Surface}/{Family}/{Size step}/{Weight}` where
- `{Surface}` = `Desktop` | `Mobile`
- `{Family}` = `Display` | `Heading` | `Body` | `Caption`
- `{Size step}` = surface-relative (Display has `Xlarge / Large / Big / Small` on Desktop and `XLarge / Large / Medium / Small` on Mobile — naming differs slightly between surfaces)
- `{Weight}` = `Regular` | `Medium` | `Semibold` *(Captions use `SmallRegular` / `MediumRegular`)*

When picking a style: **match the target surface first**, then family, then size, then weight. Never mix `Desktop/*` styles into a Mobile design or vice versa.

### 2.6 Known typography drift (file bugs — fix in Figma, do not work around)

1. `Desktop/Display/Small/Semibold` — name says Semibold but applied weight is **Regular**.
2. `Desktop/Heading/Small/Semibolds` — typo in style name (trailing "s").
3. `Mobile/Heading/2XLarge/Semibold` — name says Semibold but applied weight is **Medium**.
4. Many style **descriptions** state line-height `78px / 70px / 46px / etc.` while the actual `lineHeight` property is `AUTO`. Description is informational; rendering follows `AUTO` unless overridden.
5. Several Desktop Display/Heading style descriptions state letter-spacing `-1%` while the applied value is `-2%`.
