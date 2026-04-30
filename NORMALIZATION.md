# Normalization Instructions

Use this file when stitched HTML sources have conflicting visual systems or when the user asks to normalize the style of assembled sections/pages.

## When Normalization Is Needed

Do not assume that preserving every source stylesheet will create a coherent final page.

Before writing normalized stitch output, inspect the source styles and identify whether the inputs use:

- Different global body styles.
- Different typography systems.
- Different color palettes.
- Different button or card treatments.
- Conflicting CSS custom properties.
- Generic selectors that may leak across sections.

If source files have distinct visual systems, create a stitched-page normalization layer.

## Core Principle

Normalization is not an override pass. It is a style-stripping pass followed by a rebuild from shared tokens.

For normalized stitched output:

- Preserve content, semantic structure, IDs, anchors, scripts, and layout intent.
- Strip source-specific presentation from the stitched HTML.
- Keep only classes and attributes that express layout, alignment, visibility, or behavior.
- Rebuild typography, color, spacing, borders, radius, shadows, buttons, cards, and decorative treatments from `outputs/css/tokens.css` and the stitched stylesheet.

Do not rely on source-specific visual styles or Tailwind presentation utilities to create the final normalized look.

## Purpose First

Before choosing a visual direction, identify the intended purpose of the stitched page.

Use the user's request first. If the user does not state the purpose, infer it from:

- Output file name.
- Folder name.
- Source file names.
- Page titles.
- Hero copy.
- Navigation labels.
- Section content.

The purpose should describe what the final stitched page is meant to be, such as "portfolio homepage", "agency landing page", "pricing page", or "product overview page".

Do not choose the normalization direction only because a source appears first. Source order may affect page flow, but page purpose should drive the final visual system.

If the purpose cannot be inferred and it would change the visual direction, ask the user before writing files.

## Normalization Rules

- Keep original source-specific CSS files unchanged.
- Use `outputs/css/tokens.css` as the source of truth for global style decisions.
- Load `tokens.css` before the stitched-specific stylesheet.
- For normalized stitched pages, do not link source-specific CSS files by default.
- Link source-specific CSS only when it contains required layout or behavior that cannot be cleanly represented in the stitched stylesheet.
- Name the stitched CSS file after the stitched HTML file.
  Example: `home-stitched.html` uses `../css/home-stitched.css`.
- Add a unique class to the stitched body, such as `home-stitched-page`.
- Scope stitched overrides under that body class.
- Normalize shared page-level decisions:
  - Background.
  - Text color.
  - Font family.
  - Type scale.
  - Heading weight and rhythm.
  - Section spacing.
  - Content width.
  - Grid and card gaps.
  - Buttons.
  - Cards.
  - Image placeholders.
  - Border radius.
  - Accent colors.
- Preserve source layout and content unless the user asks for redesign.
- Define shared global tokens in `outputs/css/tokens.css`; use the stitched stylesheet to apply those tokens and handle page-specific overrides.
- Remove source-specific Tailwind presentation utilities from the stitched HTML. Do not keep them and try to override them later.

## Style Stripping Rules

When normalizing stitched HTML, remove classes that encode visual presentation.

Strip these class categories from the stitched HTML:

- Typography: `text-*`, `font-*`, `leading-*`, `tracking-*`, `uppercase`, `lowercase`, `capitalize`, `italic`, `not-italic`.
- Color and paint: `text-*` color utilities, `bg-*`, `from-*`, `via-*`, `to-*`, `gradient-*`, `fill-*`, `stroke-*`.
- Spacing: `p-*`, `px-*`, `py-*`, `pt-*`, `pr-*`, `pb-*`, `pl-*`, `m-*`, `mx-*`, `my-*`, `mt-*`, `mr-*`, `mb-*`, `ml-*`, `gap-*`, `space-*`.
- Borders and shape: `border-*`, `rounded-*`, `ring-*`, `outline-*`, `divide-*`.
- Effects: `shadow-*`, `opacity-*`, `blur-*`, `filter`, `backdrop-*`, `mix-blend-*`.
- Sizing used only for visual emphasis: arbitrary text/sizing values such as `text-[...]`, `h-[...]`, `w-[...]`, `min-h-[...]`, `max-w-[...]` when they are not required for layout.

Preserve classes that express layout, alignment, structure, visibility, or behavior:

- Display and layout: `block`, `inline-block`, `inline-flex`, `flex`, `grid`, `hidden`, responsive display variants.
- Flex/grid structure: `flex-col`, `flex-row`, `flex-wrap`, `grid-cols-*`, `grid-rows-*`, `col-span-*`, `row-span-*`.
- Alignment: `items-*`, `justify-*`, `content-*`, `self-*`, `place-*`, `text-left`, `text-center`, `text-right`.
- Positioning and layering: `relative`, `absolute`, `fixed`, `sticky`, `inset-*`, `top-*`, `right-*`, `bottom-*`, `left-*`, `z-*`.
- Overflow and object behavior: `overflow-*`, `object-*`.
- Layout sizing when required: `w-full`, `h-full`, `min-h-screen`, `aspect-*`, and semantic sizing needed to preserve the layout.
- Responsive layout variants for the allowed categories above.

If a stripped spacing or sizing class is needed to preserve layout rhythm, replace it with a semantic class and define the value in CSS using `tokens.css`. For example, replace `px-7 py-14` with `class="stitched-section"` and define `.stitched-section` from spacing tokens.

Do not preserve arbitrary Tailwind values for typography, spacing, color, radius, or effects in normalized output.

## Token Source of Truth

`outputs/css/tokens.css` owns the normalized global design system. Do not create a separate competing token system inside the stitched stylesheet.

When normalization needs a shared decision, define or update the relevant token in `tokens.css` first, then reference it from the stitched stylesheet. This applies to:

- Color roles.
- Font families.
- Type sizes.
- Line heights.
- Font weights.
- Section spacing.
- Content widths.
- Grid gaps.
- Card spacing.
- Button sizing.
- Border radii.
- Shadows.

The stitched stylesheet may define page-scoped aliases only when they point back to `tokens.css` values. For example:

```css
.home-stitched-page {
  --stitched-bg: var(--color-background);
  --stitched-text: var(--color-text);
  --stitched-section-padding: var(--space-section-y);
}
```

Do not define unrelated hard-coded values in the stitched stylesheet when a token should exist in `tokens.css`.

## Scale Requirements

Normalization must define and apply a small shared scale instead of only remapping colors.

Define or confirm `tokens.css` has global custom properties for:

- Font family.
- Body text size.
- Small text size.
- Navigation text size.
- Button text size.
- Eyebrow or label text size.
- Card heading size.
- Section heading size.
- Hero heading size.
- Body line height.
- Heading line height.
- Section block padding.
- Section inline padding.
- Content max width.
- Grid gap.
- Card padding.
- Element gap.

Use the same token for the same role across all stitched sources. For example, all nav links should use the same navigation text token, all primary buttons should use the same button text token, and all service/card headings should use the same card heading token.

## Typography Rules

- Normalize font sizes by role, not by source page.
- Do not leave source-specific Tailwind typography utilities in the stitched HTML.
- Apply type through semantic selectors and classes in the stitched stylesheet.
- Keep only intentional hierarchy differences:
  - One hero heading scale.
  - One section heading scale.
  - One card heading scale.
  - One body copy scale.
  - One caption or metadata scale.
- Use consistent font weight for equivalent roles such as nav links, buttons, labels, and cards.
- Use consistent line heights for equivalent roles.

## Spacing Rules

- Normalize spacing by role, not by source page.
- Use shared tokens for section padding, grid gaps, card padding, button padding, and repeated vertical spacing.
- Do not leave source-specific Tailwind spacing utilities in the stitched HTML.
- Apply spacing through semantic selectors and classes in the stitched stylesheet.
- Keep hero sections allowed to have larger vertical space, but make their internal rhythm consistent with each other.
- Ensure adjacent stitched sections have deliberate transitions and consistent top/bottom spacing.

## Verification

Before completing a normalized stitched page, check that:

- Source-specific presentation stylesheets are not linked unless explicitly required for layout or behavior.
- Source-specific Tailwind presentation utilities have been stripped from the stitched HTML.
- Equivalent nav links use the same font size, weight, and color.
- Equivalent buttons use the same font size, height, padding, radius, and color treatment.
- Equivalent card headings and copy use the same type scale.
- Section padding follows the global token scale from `tokens.css`.
- Repeated grids use consistent gaps.
- The page does not visibly switch design systems between stitched sources.

## Theme Direction

If the user does not specify a visual direction, infer the dominant style from:

- The page purpose.
- The target audience implied by the content.
- The strongest existing visual system.
- The first or hero section, only when it matches the page purpose.
- Consistency across the final stitched page.

Document both the inferred page purpose and the chosen direction briefly in the completion note.
