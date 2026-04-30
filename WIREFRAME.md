# Wireframe Instructions

Use this file when the user asks to generate, create, or revise a wireframe.

## Inputs

- Reference files must come from `resources/`.
- If references are inside a subfolder, mirror that folder under `outputs/`.
- Example: references in `resources/about/` should produce HTML in `outputs/about/`.

## Output Location

- Write wireframe HTML only inside `outputs/`.
- Write native CSS only inside `outputs/css/`.
- Do not overwrite existing HTML files. If a target file exists, create a numbered variant such as `landing-page-2.html`.

## CSS Rules

- Use `outputs/css/tokens.css` as the shared CSS token file.
- If `outputs/css/tokens.css` does not exist, create it before creating wireframe HTML.
- Use `outputs/css/placeholders.css` for reusable image and icon placeholder styles.
- Put typography, colors, theme values, reusable component styling, borders, shadows, and visual treatments in native CSS.
- Keep typography and color values sourced from CSS variables whenever practical.
- Use Tailwind CSS from the CDN for layout, spacing, sizing, grid/flex behavior, and responsive utilities.
- Avoid duplicating hard-coded colors or font values inside HTML utility classes.

## Placeholder Rules

- If a reference contains photos, illustrations, logos, or icons that are not available as source assets, use placeholders instead of recreating exact images.
- Preserve the role, size, layout position, and visual weight of the referenced asset.
- Use descriptive labels such as `Hero image`, `Product photo`, `Brand logo`, or `Search icon`.
- Use image placeholders for large visual blocks, cards, avatars, thumbnails, and gallery items.
- Use icon placeholders for small symbolic UI elements, feature icons, social icons, and control icons.
- Link `outputs/css/placeholders.css` when using placeholder classes.
- Use `outputs/placeholder-template.html` as the reference for placeholder markup patterns.

## HTML Rules

- Include the Tailwind CDN script in each generated HTML file.
- Link the shared token stylesheet with the correct relative path.
- Use `css/tokens.css` for HTML files directly inside `outputs/`.
- Use `../css/tokens.css` for HTML files one folder below `outputs/`.
- Use deeper relative paths for deeper folders.
- Every major page section must have a unique `id`.
- Important interactive or structural elements must also have stable IDs.
- Example: a carousel section can use `id="testimonials"` for the section and `id="testimonial-carousel"` for the carousel wrapper.

## Naming Rules

- Use kebab-case for generated HTML file names.
- If the user gives a page name, use that name in kebab-case.
- Example: "About Us" becomes `about-us.html`.
- If one reference file maps to one HTML file, reuse the reference filename in kebab-case.
- Example: `resources/about/Hero Section.png` becomes `outputs/about/hero-section.html`.
- If multiple references in one folder form a single page, name the page `index.html` in the mirrored output folder.
- Example: `resources/about/*` becomes `outputs/about/index.html`.
- If creating alternatives, add a short suffix such as `-v2` or `-alt`.

## Completion Checklist

- Generated files are inside `outputs/`.
- CSS tokens are reused from `outputs/css/tokens.css`.
- Placeholder assets use `outputs/css/placeholders.css` when source images/icons are unavailable.
- Tailwind CDN is present.
- CSS link path is correct for the HTML file location.
- Sections and important elements have useful IDs.
- Existing files were not overwritten.
