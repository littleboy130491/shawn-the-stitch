# Agent Instructions

This project is a controlled workspace for creating static HTML wireframes and stitching existing HTML sections/pages together.

## Workflow Routing

- For any request to generate, create, or revise a wireframe, read `WIREFRAME.md` before writing files.
- For any request to combine, stitch, merge, or assemble HTML files/sections, read `STITCH.md` before writing files.
- If a request involves both wireframing and stitching, read both files and complete the wireframe work before stitching.

## File Boundaries

- Write generated project files only inside `outputs/`.
- Read source/reference material from `resources/`.
- Do not overwrite existing files unless the user explicitly asks for that exact file to be replaced.
- Root instruction files such as `AGENTS.md`, `WIREFRAME.md`, and `STITCH.md` may be edited only when the user explicitly asks to update project instructions.

## Output Expectations

- Prefer simple, static HTML and CSS.
- Keep generated assets easy to inspect and edit manually.
- Use clear file names, stable IDs, and shared CSS tokens so later agents can continue the work consistently.
