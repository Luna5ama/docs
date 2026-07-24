# DOCUMENTATION AUTHORING

## OVERVIEW

Authoring contract for the Starlight MDX corpus and its reference subdomains.
`current/` is supported documentation; `aperture/` is hidden legacy migration material.

## STRUCTURE

```text
docs/
├── current/Guides/Your First Shaderpack/ # Ordered, cumulative tutorial
├── current/How To/                       # Standalone focused tasks
├── current/Reference/                    # Exact shader API and format contracts
├── aperture/                             # Legacy Aperture migration notes
├── index.mdx                             # Custom splash homepage
└── 404.mdx                               # Custom splash error page
```

## WHERE TO LOOK

| Task | Location | Contract |
|------|----------|----------|
| Tutorial step | `current/Guides/Your First Shaderpack/` | Sequence, code snapshot, and media move together |
| Focused shader task | `current/How To/` | One small problem; no prior chapter assumed |
| Shader API lookup | `current/Reference/` | Technical names and behavior are authoritative |
| Program pipeline status | `current/Reference/Programs/overview.mdx` | Deliberately marked `Unfinished` |
| Legacy migration | `aperture/migration.mdx` | Do not present as current Iris behavior |
| Landing/error copy | `index.mdx`, `404.mdx` | Splash frontmatter and Starlight cards |

## CONVENTIONS

- Standard frontmatter: `title`, `description`, then `sidebar.label` and numeric `sidebar.order`.
- Put support state in `sidebar.badge` with `text` and Starlight `variant`; keep the Programs overview `Unfinished` badge until that page is completed and reviewed.
- Splash-only fields (`template`, `hero`, disabled edit/prev/next metadata) belong to `index.mdx` and `404.mdx`.
- Frontmatter renders the page title. Start prose sections at `##`; use `###`/`####` only for real nesting or technical signatures.
- Write concise headings and simple present tense. Keep `OptiFine` and `GLSL` capitalization exact; do not abbreviate established terms.
- Backtick exact code terms and shader filenames; bold named non-code concepts. Say “shader pack” and “resource pack.”
- Include `.vsh`/`.fsh` when the stage matters, use `*` for a file family, and omit the extension only when all stages are meant.
- Use `rgba` swizzles only for color channels; otherwise use `xyzw`.
- Preserve exact API spelling in filenames, titles, headings, and code: `MC_VERSION`, `mc_chunkFade`, `workGroupsRender`.
- Guide filenames encode sequence (`0_intro` through `6_next_steps`); keep the prefix and sidebar order aligned.
- Guide steps 1-5 link a matching `IrisShaders/tutorial-code` stage snapshot. Code changes require checking that snapshot and the associated `src/assets/beginner_tutorial/` images.
- How To pages solve one small shader problem and link outward to the exact Reference entries they use.
- Reference pages are terse contracts: declaration or directive, validity/location metadata, behavior, compatibility limits, then cross-links.
- Grouped Uniform and `Shaders.Properties` pages repeat `## identifier`, optional inline `<Badge>`, typed fence, explanation, and thematic break.
- Single-entry macro, constant, and attribute pages use a backticked `###` signature, bold metadata such as `**Location**` or `**Valid Programs**`, then a thematic break.
- Program entries lead with required/optional stages, buffers, and suffixes; buffer entries use signature headings plus `####` capability sections.
- Use typed fences (`glsl`, `properties`, `ts`, `json`, `text`); add `title="..."` when a filename or profile matters.
- Use `:::note`, `:::tip`, `:::caution[Warning]`, and `:::danger`; reserve cautions/dangers for actionable compatibility or correctness limits.
- Import only used Starlight components after frontmatter. Use `Badge` for status and `LinkCard` for navigation tiles.
- Internal prose links are root-relative, lowercase routes, normally with a trailing slash; backtick technical link labels.
- Published routes normalize display directories: `Your First Shaderpack` becomes `your-first-shaderpack`, and `Shaders.Properties` becomes `shadersproperties`.
- Heading anchors are generated. Keep technical headings stable and link to their normalized fragment instead of adding manual IDs.
- For any file or heading rename, search the old route/fragment across this corpus, check the derived `/og/` path, run `pnpm build`, and open the changed routes and fragments; the build has no link checker.
- Keep article media under `src/assets/`, reference it relative to the MDX file, and provide meaningful alt text.
- Treat `aperture/oldInfo` as non-routable scratch material; current feature documentation belongs under `current/`.

## ANTI-PATTERNS

- Do not add page-level `#` headings; the three in `Miscellaneous/debugging_shaders.mdx` are legacy outliers.
- Do not copy missing `description`/`sidebar` metadata from thin Mod Support stubs or the top-level `order` in `pbr_standards.mdx`.
- Do not copy unused `Aside`, `Badge`, or `CardGrid` imports from existing pages.
- Do not follow README's missing `alphaTestRef` template pointer; use the matching nearby Reference pattern.
- Do not add translations yet; the repository does not support i18n.
- Do not create a competing page before checking for an existing home under `Guides`, `How To`, or `Reference`.
- Do not move current API material into `aperture/`, or cite `oldInfo` as published documentation.
