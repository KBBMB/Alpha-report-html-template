---
name: alpha-report-html-template
description: Build fixed 16:9 HTML company-report slide decks for corporate reports, trend reports, brand decks, and internal presentation demos. Use this skill when the user wants PPT-like paged HTML rather than a long scrolling webpage, with one slide per section, unified typography, restrained branding, embedded base64 images, and reusable slide patterns.
---

Build a fixed-canvas HTML slide deck, not a long webpage.

## Purpose

Generate reusable 16:9 HTML report decks that feel like company presentation pages: clean, structured, restrained, and suitable for screenshotting, presenting, or later exporting.

## When to use

Trigger this skill when the user wants any of the following:
- 公司汇报 / company report
- trend report / trend deck
- 品牌报告 / brand presentation
- 固定 16:9 HTML slide
- PPT 风格 HTML 翻页稿
- 可复用的报告模板或 demo 样张

Do not use this skill for:
- long scrolling landing pages
- dashboard-style layouts
- highly animated web storytelling pages

## Core output contract

Always keep these rules:
- Use a fixed 1600 × 900 canvas by default.
- Treat each page as one `<section class="slide">`.
- Keep a unified `header / main / footer` structure.
- Place the logo at the top-right on every slide by default.
- Keep logo height in the 40–44 px range.
- Cover and closing slides are mandatory master pages: always follow the locked template structure and composition rather than inventing new layouts.
- Agenda and body/content slides may be customized when the user provides clear direction, but if not customized, fall back to the default preset system.
- ALL logos, photos, illustrations, and decorative image assets must be embedded directly inside the HTML as base64/data URI resources.
- Do not rely on sibling image files, relative paths, remote URLs, or external asset folders for final delivery.
- The final HTML must remain fully functional when a user saves only that single `.html` file via right-click Save As.
- Preserve a corporate / clean / structured visual tone.
- Avoid webpage feel, dashboard feel, and decorative AI-style visuals.

## Typography and color

Default design tokens:
- Chinese font: 思源黑体（Source Han Sans SC / Noto Sans SC）
- English font: Outfit
- Major English titles: Outfit Bold
- Brand red: `#CE3C27`
- Neutral gray: `#626366`
- Dark text: `#212121`

Prefer local fonts first. If the user later needs cross-device stability, upgrade to a bundled `@font-face` strategy.

## Required slide coverage

The skill should understand these 11 slide types:
- cover
- agenda
- section-divider
- text-image
- full-image
- image-grid
- insight
- data-highlight
- chart-table
- summary
- thank-you

For MVP, ensure at least these 7 core types are available:
- cover
- agenda
- text-image
- insight
- chart-table
- summary
- thank-you

## Workflow

When producing or updating output:
1. Read `references/style-spec.md` as the authoritative ruleset.
2. Read `references/template-variables.md` before generating cover / closing metadata or other replaceable text fields.
3. Use `assets/alpha-company-report-demo.html` and `assets/alpha-company-report-demo-cn.html` as the synced visual samples.
4. If layout rules, slide types, logo sizing, chart styles, or language-specific font strategy change, update the demos in the same pass.
5. Auto-generate sensible defaults for replaceable fields when the user does not provide them.
6. Do not expose raw placeholder syntax like `{{variable_name}}` in final user-facing HTML.
7. Favor one visual focus per slide.
8. Keep small-screen readability guardrails: for non-decorative body text, avoid dropping below roughly 13–15 px equivalent, and raise line-height / spacing with it when needed.
9. Treat chart / table / framework slides as a separate large-type system: chart labels, in-bar values, axis labels, matrix copy, table heads, and key numbers should use more aggressive readability sizing than ordinary body slides.

## Demo-sync rule

Treat the demo as the visible sample of current skill capability, not as a disposable mock.

Whenever rules change, sync the demo immediately.

## Quality check

Before handing off, verify:
- every page is an independent slide
- 16:9 sizing is preserved
- header / footer / logo structure is present
- thank-you is the fixed last slide
- chart-table pages cover bar / line / pie / table when included
- typography, spacing, corner radius, and image treatment stay consistent
- every image reference in final delivery is embedded as data URI rather than linked file path
- saving only the single HTML file does not break image display

## Bundled resources

- `references/style-spec.md`
  - Full rule source for layout, typography, color, spacing, slide taxonomy, MVP, and QA.
- `references/template-variables.md`
  - Replaceable-field contract and default-generation rules for cover / closing metadata.
- `assets/alpha-company-report-demo.html`
  - Current synced English HTML demo sample for browser preview and visual regression checking.
- `assets/alpha-company-report-demo-cn.html`
  - Current synced Chinese HTML demo sample for browser preview and visual regression checking.

## Working style

Default to a unified, centralized template system.

Tighten presentation quality by adjusting composition, density, spacing, hierarchy, and component consistency before adding new flourish.
