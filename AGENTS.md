# Agent Instructions

This project is a controlled workspace for creating static HTML wireframes and stitching existing HTML sections/pages together.

## Workflow Routing

- For any request to generate, create, or revise a wireframe, read `WIREFRAME.md` before writing files.
- For any request to combine, stitch, merge, or assemble HTML files/sections, read `STITCH.md` before writing files.
- For any request to normalize, harmonize, unify, or make stitched page styles consistent, read `NORMALIZATION.md` before writing files.
- If a request involves both wireframing and stitching, read both files and complete the wireframe work before stitching.
- If a request involves stitching and style normalization, read both `STITCH.md` and `NORMALIZATION.md` before writing files.

## File Boundaries

- Write generated project files only inside `outputs/`.
- Read source/reference material from `resources/`.
- Do not overwrite existing files unless the user explicitly asks for that exact file to be replaced.
- Root instruction files such as `AGENTS.md`, `WIREFRAME.md`, `STITCH.md`, and `NORMALIZATION.md` may be edited only when the user explicitly asks to update project instructions.

## Output Expectations

- Prefer simple, static HTML and CSS.
- Keep generated assets easy to inspect and edit manually.
- Use clear file names, stable IDs, and shared CSS tokens so later agents can continue the work consistently.
- Define shared global style decisions in `outputs/css/tokens.css`; page-specific CSS should reference those tokens instead of inventing a separate design system.
- For normalized stitched pages, strip source presentation classes and source-specific visual styles. Preserve layout, alignment, structure, IDs, anchors, and behavior, then rebuild presentation from `outputs/css/tokens.css`.
