# Reference-aligned reconstruction notes

This pass uses the supplied reference screenshots as the visual target rather than treating the site as a generic academic portfolio.

## Reference-specific changes

- Set the page surface to `#f5f5f5` and rebuilt the interior-page typography around the screenshot proportions.
- Rebuilt **Bio** as an asymmetric two-column page: long-form serif biography on the left, key links / education / selected appointments and honors on the right. The portrait-led layout is removed.
- Rebuilt **Publications** as a wide typographic list with numbered serif entries, gray authors, compact status lines, and disclosure-style abstracts.
- Added a desktop **sticky, vertically centered publications navigator** in the right column.
- Added scroll-aware section highlighting: the active publications heading turns muted gold and receives the narrow gold rule shown in the reference.
- On tablet/mobile the publications navigator becomes an inline section bar rather than consuming a fixed side column.
- Rebuilt the footer as a full-width `#1a1a1a` directory with four desktop columns, muted gray links, uppercase headings, social links, and bottom-aligned copyright.
- Kept the user's existing biography/research text rather than filling the layout with invented biography content.
- Standardized shared navigation and page geometry across Bio, Publications, Software, Teaching, and the homepage.

## Important source files

- `styles.scss` — global design system, Bio layout, Publications scrollspy/TOC styling, footer, responsive behavior
- `bio/index.qmd` — Bio structure and content
- `publications/index.qmd` — publication list, right-side navigator, scrollspy JavaScript
- `index.qmd` — homepage
- `software/index.qmd`
- `teaching/index.qmd`
- `_quarto.yml`

## Rendering

The source is intended to be rendered with:

```bash
quarto preview
```

or:

```bash
quarto render
```

Quarto writes to `docs/`.

The Quarto CLI is not available in the editing environment used for this pass, so the changed source blocks and compiled CSS have also been mirrored into the existing `docs/` tree for immediate inspection. A future local Quarto render should use the source `.qmd` files and `styles.scss` as the authoritative version.

## August 10 refinement

- Restored the previous typography system: Inter for sans-serif interface/meta text and Newsreader for editorial serif text/headings.
- Kept the reference-aligned Bio, Publications, sticky scrollspy TOC, and directory footer structures unchanged.
- Removed Quarto's residual `column-page` constraint from the custom site shell so the homepage/header/footer center against the viewport rather than inside Quarto's narrower page grid.

## Homepage refinement — 2026-08-10
- Added more top breathing room above the masthead.
- Removed Email from the top external-links row; the masthead now shows ORCID, LinkedIn, and Bluesky.
- Matched the Working Papers heading typography to Recent Talks and Awards, Honours and Grants.
- Made Recent Talks a fixed-height, independently scrollable panel on desktop.
- Reordered talk entries so venue is the prominent first row, with the date aligned to the right and a short `Topic:` summary below.
- Simplified the footer to Kai Cooper + icon links for Email, ORCID, LinkedIn, and Bluesky; removed the ambiguous Bootstrap person/cloud substitutes.
- Kept the copyright and PhD affiliation line at the bottom of the footer.

## 2026-08-10 layout consistency pass

- Standardized masthead, page shell, and interior navigation to the same 1424px maximum width used by the Bio page.
- Fixed the Publications Quarto grid so its header, navigation, content shell, and footer align with the same left/right margins as the other pages.
- Increased vertical spacing between the interior navigation and subpage headings.
- Restored real top-of-page breathing room by overriding Quarto's direct-child padding reset on the masthead.
- Removed the redundant Kai Cooper home link from the homepage masthead; the homepage title remains the identity anchor.
- Rebuilt Teaching in a reference-style two-column layout with an introductory block and compact course metadata.
- Rebuilt Software around a single Autobounds visual card with image, title, subtitle, description, and arrow links to GitHub, the paper, and related research.
- Added an original Autobounds partial-identification illustration at `assets/images/autobounds-visual.svg` rather than copying the reference site's imagery.
- Made the dark footer background viewport-wide on all pages while aligning its internal content to the shared Bio-width shell.
- Replaced font-dependent footer social glyphs with inline SVG icons for Email, ORCID, LinkedIn, and Bluesky.

## Margin correction (2026-08-10)

- Restored the wide Bio two-column geometry by overriding Quarto's generic `aside` grid placement on `.bio-sidebar`. Quarto applies `grid-column: body-end / page-end !important` to generic `<aside>` elements; this was creating implicit columns and collapsing the Bio copy width.
- Standardized the desktop outer gutter to 56px per side for the masthead, page shell, publications wrapper, and footer contents (subject to the 1424px maximum content width).
- Retained the smaller responsive gutters at tablet/mobile breakpoints.
- Verified at a 1394px viewport that Home, Bio, Publications, Software, Teaching, and footer contents all run from x=56px to x=1338px.
