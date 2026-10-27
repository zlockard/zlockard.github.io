---
description: "Use when creating, regenerating, or refining movie posters, raster PNG sleeve artwork, IMDb-inspired title lettering, VHS sleeves and cassette labels, poster sizing, or poster styling for this site."
applyTo: "static/posters/**,layouts/shortcodes/moviesummary.html,themes/PaperMod2/assets/css/extended/custom.css"
---

# Approved movie-poster design

The approved default for **future poster generation** is the latest
[2026 raster-sleeve collection](../../static/posters/prototypes/2026-comparison.html),
including its IMDb-inspired title lettering and clean, outlined tape labels.
These designs are installed at the canonical paths in `static/posters/`;
the gallery retains archived previous covers for comparison.
This supersedes the earlier abstract-only sleeve-art preference.

Use [Rawhead Rex](../../static/posters/rawhead-rex-1989.svg) as
a complete reference. The archived original
[Troll 2](../../static/posters/prototypes/originals/troll-2.svg) and
[Bad Biology](../../static/posters/prototypes/originals/bad-biology.svg) remain construction
references, not the default illustration or lettering style for new covers.
See the [authoring guide](../../README.md) for the optional `poster` parameter.

## Composition and proportions

- Show an illustrated VHS sleeve on the left, with the cassette partly pulled
  out to the right. Orient the cassette vertically, with its reels stacked.
- The sleeve's front face must be approximately **7.4 tall by 4.1 wide**
  (height/width about 1.805), excluding the perspective bevel. The current
  reference front faces are 380 units tall and 210.5 units wide.
- The sleeve fits closely around the cassette, with only small top and bottom
  margins. Do not make the sleeve noticeably taller than the tape.
- Keep the sleeve's right edge open: the dark material immediately beyond the
  cover must be the cassette, not a closed side panel on the sleeve.
- Give both the sleeve and cassette visible top faces with consistent
  perspective. The cassette also has a shaded right face.
- Match the cassette's rounded front corners on its projected edge faces.
  At the bottom-right join, connect the curves along their shared tangent;
  do not leave a notch, disconnected edge, square projection, or abrupt step.
  Preserve the approved top-right corner when refining the bottom.

## Original raster sleeve artwork

- View the actual primary image on the movie's IMDb page before designing.
  Understand its broad ideas, mood, palette, and lettering; do not infer them
  from a search snippet or claim to have viewed an inaccessible image.
- Draw a new composition from those concepts and the movie's settings or props.
  Do not copy, trace, crop, or embed the official poster, its exact logo, or actor
  likenesses. IMDb is a visual reference, not an asset source.
- Prefer atmospheric, illustrated scenes with recognizable silhouettes, layered
  landscapes or interiors, gradients, mist or lighting, and subtle pigment grain.
  Keep the imagery non-graphic and readable at thumbnail size. Do not revert to
  the old two-symbol abstract template or merely rasterize an old cover.
- Use a regular PNG image for the sleeve-front art, including its title.
  The approved sleeve PNGs are **421 x 760 pixels**, exactly twice the
  210.5 x 380 SVG-unit front face. Keep that ratio; use at least this resolution
  for comparable detail. This is not the full VHS composition's 2:3 ratio.
- Keep the reusable sleeve bevel, black cassette, and ground shadow in SVG.
  Embed the PNG as a data URI in an SVG `image` at x2, y30, width210.5, height380,
  so the wrapper is self-contained when displayed through an HTML `img`.
  Retain a companion PNG for editing. No remote image dependencies.
- Coordinate the sleeve top with the front palette; the approved prototypes
  lighten a sampled upper-front color with 18% white.
- Do not include "Backyard Video" branding or host-written explanations.
  Movie titles, years, a small VHS mark, and relevant in-world signs are fine.

## Reference-inspired title lettering

- Loosely match the IMDb reference's typographic character: weight, width,
  serif or brush style, slant, capitalization, colors, outlines, shadows,
  metallic effects, and restrained distressing. Exact logo matching is neither
  necessary nor desired. Preserve the movie's title wording.
- Choose movie-specific treatments instead of one shared display font.
  Approved examples in the 2026 collection include red slab-serif Rawhead Rex,
  gold stencil Terror Squad, white italic Savage Beach, pink script Yes Madam,
  chrome-blue BMX Bandits, cyan/pink brush Thrashin, classic red/black serif
  Faster, Pussycat! Kill! Kill!, and purple-on-yellow brush Street Trash.
- Use available local fonts to create the raster lettering; do not download
  fonts or change the website's typography. Verify that the drawing environment
  actually renders the chosen face rather than silently substituting a fallback.
  The rendered PNG must not depend on fonts being installed on visitors' devices.
- Vary title placement and composition between movies: top and bottom titles,
  stacked lines, modest angles, and tight title panels are all approved.
  Mix coordinated warm/cool, light/dark, and saturated/pastel palettes.
- Keep title text at least 4.5:1 contrast against the sleeve background.
  A contrasting title panel is fine when needed. Measure actual glyph bounds,
  including rotation, strokes, shadows, and descenders; refit size and spacing
  without clipping or collisions. Never stretch letters or art nonuniformly.

## Cassette labels and refinement scope

- Preserve the approved cassette faces, reels, grip, label panel, and rounded
  joins. Keep tape lettering separate from the illustrated sleeve title.
- Use fitted vector outlines for the rotated tape-title lettering and VHS mark,
  as in the 2026 prototypes, rather than font-dependent SVG text that can render
  inconsistently. Preserve the full title and keep paths within the label panel.
  The current title outline is centered at x262, y232.5 before a 90-degree
  rotation, with measured width at most 139 and height at most 11 SVG units.
- For typography-only requests, change only title lettering and its immediate
  backdrop. Preserve all illustration pixels outside the title bands, palette,
  sleeve construction, and corrected cassette labels.
- Keep exploratory revisions separate and show current/new comparisons.
  Approval of these style instructions is not permission to replace existing
  live posters or change event-page poster references automatically.

## Display and verification

- Keep the complete composition in a 2:3 portrait SVG canvas; this is distinct
  from the narrower sleeve-front ratio.
- Artwork must read clearly at the existing 84px desktop and 72px mobile widths.
  Check full-size artwork as well as actual thumbnails in light and dark modes.
- Keep the rectangular CSS shadow off the poster wrapper. A soft ground shadow
  inside the artwork is intentional.
- Keep the design static, with no animation.
- Verify the sleeve ratio numerically. Check face joins, exposed cassette
  edges, close sleeve fit, and clipping; loading successfully is not enough.
- Review collection contact sheets to confirm meaningful layout, color, and
  font variety. Check title/art overlap and contrast, not just asset loading.
- For collections, provide side-by-side current/new views with large, 84px,
  and 72px previews on light and dark backgrounds, as in the 2026 gallery.
- For lettering-only revisions, verify pixel equality outside the title bands
  and unchanged cassette geometry and labels against a saved baseline.
- Build Hugo into an isolated verification destination, not tracked `public`;
  verify the generated assets match their sources and image references resolve.
- Reuse the same poster for repeat screenings. Preserve movie metadata and
  unrelated site styles when refining artwork.
