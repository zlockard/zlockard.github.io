---
description: "Use when creating, regenerating, or refining movie posters, VHS sleeve and cassette artwork, poster sizing, or poster styling for this site."
applyTo: "static/posters/**,layouts/shortcodes/moviesummary.html,themes/PaperMod2/assets/css/extended/custom.css"
---

# Approved movie-poster design

Use the current [Troll 2](../../static/posters/troll-2.svg) and
[Bad Biology](../../static/posters/bad-biology.svg) artwork as the approved
references for VHS construction and their individual color identities.
Keep that construction consistent while varying the sleeve-front design.
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

## Artwork and typography

- Create original, full-color SVG illustrations, not reproductions of official
  posters, logos, or actor likenesses. Keep all SVG resources local.
- Include recognizable, non-graphic elements from the actual movie, rather
  than only generic genre symbols. Reference examples include Nilbog, green
  food, and vegetation for Troll 2; abnormal cells and chemical motifs for
  Bad Biology.
- Prefer the original restrained, abstract illustrations and symbolic movie
  props over literal scenes, detailed characters, or photographic artwork.
  The fuller scene-based revision was rejected in favor of the abstract covers.
- Preserve existing illustration shapes when the request is only for layout,
  color, or typography changes. Repositioning and uniform scaling are fine.
- Use clean silhouettes, restrained detail, consistent strokes, aligned margins,
  and bold, readable titles. Recenter artwork when changing the sleeve width.
- Never stretch the lettering or illustrations with nonuniform scaling.
- Do not include "Backyard Video" branding or host-written explanations.
  Movie titles, years, a small VHS mark, and relevant in-world signs are fine.
- Preserve each reference's color identity: cream/forest green/burnt orange
  for Troll 2, and deep purple/coral/turquoise/acid green for Bad Biology.

## Sleeve-front variety

- Do not give every movie the same title-above-art template. Mix artwork-first
  covers with lower titles, boxed lower titles, angled headings, left- and
  right-aligned titles, side-by-side motifs, and staggered title lines.
- Preserve the established varied layouts when changing only colors or fonts.
  Useful examples are [Savage Beach](../../static/posters/savage-beach-1989.svg),
  [Rock and Roll Nightmare](../../static/posters/rock-and-roll-nightmare-1987.svg),
  [Miami Connection](../../static/posters/miami-connection-1987.svg), and
  [Alien Private Eye](../../static/posters/alien-private-eye-1989.svg).
- Mix saturated and pastel colorways, warm and cool hues, and light and dark
  sleeve backgrounds. Use coordinated, contrasting colors for titles and motifs;
  do not merely recolor a small accent while leaving every sleeve alike.
- Vary title typography with condensed display faces, bold serifs, monospace,
  humanist or wide sans-serifs, heavy lettering, and italic treatments.
  Use system-font stacks with appropriate generic fallbacks; do not introduce
  font downloads or change the site's typography for poster styling.
- Keep title text at least 4.5:1 contrast against the sleeve background.
  Measure actual title bounds and refit font sizes, line spacing, and positions
  for each font treatment. Check fallback fonts as well as the preferred face.
  Do not stretch text, distort glyphs, or let titles touch borders or artwork.
- Keep these variations on the sleeve. Preserve the black cassette, its labels,
  and its approved geometry unless a cassette change is specifically requested.

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
- Reuse the same poster for repeat screenings. Preserve movie metadata and
  unrelated site styles when refining artwork.
