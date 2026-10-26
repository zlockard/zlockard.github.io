---
description: "Use when creating, regenerating, or refining movie posters, VHS sleeve and cassette artwork, poster sizing, or poster styling for this site."
applyTo: "static/posters/**,layouts/shortcodes/moviesummary.html,themes/PaperMod2/assets/css/extended/custom.css"
---

# Approved movie-poster design

Use the current [Troll 2](../../static/posters/troll-2.svg) and
[Bad Biology](../../static/posters/bad-biology.svg) artwork as the approved
references. Preserve their established composition when making new posters.
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
- Use clean silhouettes, restrained detail, consistent strokes, aligned margins,
  and bold, readable titles. Recenter artwork when changing the sleeve width.
- Never stretch the lettering or illustrations with nonuniform scaling.
- Do not include "Backyard Video" branding or host-written explanations.
  Movie titles, years, a small VHS mark, and relevant in-world signs are fine.
- Preserve each reference's color identity: cream/forest green/burnt orange
  for Troll 2, and deep purple/coral/turquoise/acid green for Bad Biology.

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
