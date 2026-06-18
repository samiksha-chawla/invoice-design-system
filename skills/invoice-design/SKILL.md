---
name: invoice-design
version: 0.1.0
description: |
  Petpooja design guidelines enforcer. Loads base design rules on every invocation,
  then conditionally loads web or mobile rules based on the requested surface.
  These guidelines are derived strictly from the official Figma source files
  and MUST NOT be violated under any circumstance.
  Use when asked to "design", "create UI", "build a screen", "apply design system",
  "design review", "use design guidelines", or any task that produces visual / UI output.
triggers:
  - design a screen
  - apply design guidelines
  - use the design system
  - build a UI
  - design review against guidelines
allowed-tools:
  - Read
  - Glob
  - Grep
  - AskUserQuestion
---

# /invoice-design — Petpooja Design Guidelines

Strict enforcement of the Petpooja design system as defined in Figma. **Base
guidelines apply to every design.** Web or mobile guidelines layer on top of
base according to the target surface.

## Source of truth (Figma)

| Layer    | Figma file                                                                                     | Local copy |
| -------- | ---------------------------------------------------------------------------------------------- | ---------- |
| Base     | https://www.figma.com/design/FMeWvHvADIwTJKORCpEuwV/Base-Guidelines                            | `base.md`   |
| Web      | https://www.figma.com/design/yJFajRsXtj45oDRWYvauhI/Web-Guidelines                             | `web.md`    |
| Mobile   | https://www.figma.com/design/BYjfyLF2DEQhdU1jszWt2g/Mobile-Guidelines                          | `mobile.md` |

Figma is canonical. If `base.md` / `web.md` / `mobile.md` ever disagree with
Figma, **Figma wins** — flag the drift to the user and update the local copy.

## Iron rules — non-negotiable

1. **Base is always loaded.** Read `base.md` before producing or reviewing
   any visual output. No exceptions.
2. **Conditional layer is required.** If the work is web → also read
   `web.md`. If it's mobile (iOS/Android) → also read `mobile.md`. If both
   surfaces are in scope, read both.
3. **Do not invent tokens.** Colors, type sizes, spacing, radii, shadows,
   motion timings — use ONLY the values defined in the loaded guidelines.
   If a needed token does not exist, stop and ask; do not guess.
4. **Do not invent components.** Use only the components catalogued in the
   guidelines. If a needed component is missing, propose it explicitly and
   wait for confirmation.
5. **Do not violate, soften, or "modernize" any rule** to make a design
   work. If a request conflicts with the guidelines, surface the conflict
   to the user and ask them to choose: change the request, or escalate to
   amend the guideline.

## Workflow — when this skill is invoked

1. **Always:** Read `base.md` in full. Treat its rules as preconditions for
   every step that follows.
2. **Detect surface.** From the user's request, infer the target:
   - Mentions of "web", "website", "dashboard", "landing", "browser",
     "responsive", "desktop" → web.
   - Mentions of "mobile", "iOS", "Android", "app", "native", "phone",
     "tablet" (when the tablet is the native app) → mobile.
   - Ambiguous → use AskUserQuestion to confirm before proceeding.
3. **Load layer.** Read `web.md` and/or `mobile.md` accordingly.
4. **Plan against rules.** Before writing code or producing visuals, draft a
   short checklist mapping the task to the relevant tokens, components, and
   patterns. Cite the section you're relying on (e.g. "base.md §Color/
   Surface", "web.md §Grid/12-col").
5. **Produce the output.** Stay inside the loaded vocabulary.
6. **Self-review.** Before reporting done, re-check the output against the
   iron rules above. If anything was invented, fix it.

## How to detect drift between Figma and local copies

If the user references a token or component that doesn't appear in the local
`.md` files, OR if Figma has been updated more recently than the local copy:

1. Note the discrepancy in your response.
2. Do not silently improvise. Ask whether to fetch the missing piece from
   Figma now and update the local file.

## Extraction status

The Figma → local-file extraction is being performed **incrementally**. Each
file declares its own extraction status at the top. Sections marked
`[NOT YET EXTRACTED FROM FIGMA]` are **not yet authoritative** — if you need
one of those sections to complete a task, stop and ask the user to extract
that section from Figma first.

## When to NOT just blindly apply rules

The guidelines are non-negotiable for design output, but the user may:

- Ask "what does the guideline say about X" → answer from the docs, no
  design output needed.
- Ask to update a guideline → that's a Figma operation, not a local override.
  Do not edit `base.md`/`web.md`/`mobile.md` to reflect a change that hasn't
  landed in Figma yet.
- Ask for an experimental / off-system mockup → require explicit acknowledgment
  ("yes, intentionally off-system") before producing it, and clearly label the
  output as non-canonical.
