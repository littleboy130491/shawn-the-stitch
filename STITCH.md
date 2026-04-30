# Stitch Instructions

Use this file when the user asks to combine, stitch, merge, or assemble existing HTML files or sections.

## Inputs

- Source HTML files usually come from the same `outputs/` directory or subdirectory.
- If the user provides an explicit source list, use that list.
- If files are numbered, infer the arrangement from the numbers.
- Example order: `01-hero.html`, `02-features.html`, `03-footer.html`.
- If the arrangement is not explicit and cannot be inferred from filenames, ask the user for the order before writing the stitched file.

## Output Location

- Always create a new HTML file.
- Never overwrite source files or previous stitched files.
- Place the stitched file in `outputs/`.
- If all source files are in the same `outputs/` subfolder, place the stitched file in that same subfolder.

## Naming Rules

- Use kebab-case for stitched HTML file names.
- If the user gives an output name, use that name in kebab-case.
- If the stitched page has a clear purpose, use that purpose.
- Example: `homepage-stitched.html` or `pricing-page-stitched.html`.
- If no output name or clear purpose is available, use `stitched.html`.
- If the target filename exists, create a numbered variant such as `stitched-2.html`, `stitched-3.html`, and so on.

## Stitching Rules

- Preserve source section IDs unless they conflict.
- If duplicate IDs exist, rename the duplicates so every ID in the final file is unique.
- Preserve existing stylesheet links and scripts that are needed by the stitched content.
- Avoid adding unrelated design changes while stitching.
- Keep the final HTML static and easy to edit manually.

## Completion Checklist

- Source order is explicit or safely inferred.
- The stitched file is new and inside `outputs/`.
- No source file was overwritten.
- Duplicate IDs were resolved.
- Required CSS and script references are present.
