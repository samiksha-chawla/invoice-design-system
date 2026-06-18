# Invoice Design System — Claude Code Plugin

The Petpooja design guidelines, packaged as a Claude Code plugin. It ships the
`invoice-design` skill, which strictly enforces the Invoice Design System as defined
in Figma (base + web + mobile guidelines).

## Install

In Claude Code:

```
/plugin marketplace add samiksha-chawla/invoice-design-system
/plugin install invoice-design-system@invoice-design
```

Then restart Claude Code (or reload plugins). The `invoice-design` skill will be
available — it activates when you ask to "design", "create UI", "build a screen",
"apply the design system", or "design review".

## What's inside

| File                        | Purpose                                   |
| --------------------------- | ----------------------------------------- |
| `skills/invoice-design/SKILL.md` | The enforcer skill (loaded by Claude)     |
| `skills/invoice-design/base.md`  | Base guidelines (always loaded)           |
| `skills/invoice-design/web.md`   | Web guidelines (loaded for web surfaces)  |
| `skills/invoice-design/mobile.md`| Mobile guidelines (loaded for mobile)     |

## Source of truth

Figma is canonical. If the local `.md` files disagree with Figma, **Figma wins** —
flag the drift and update the local copy.

| Layer  | Figma file |
| ------ | ---------- |
| Base   | https://www.figma.com/design/FMeWvHvADIwTJKORCpEuwV/Base-Guidelines |
| Web    | https://www.figma.com/design/yJFajRsXtj45oDRWYvauhI/Web-Guidelines  |
| Mobile | https://www.figma.com/design/BYjfyLF2DEQhdU1jszWt2g/Mobile-Guidelines |
