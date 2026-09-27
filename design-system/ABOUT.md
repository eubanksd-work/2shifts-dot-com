# design-system/

A file copy of the Second Shift design system. The live, browsable version is the Claude artifact
https://claude.ai/artifact/A5rRc8KytkovYAmwXx4Jm3 -- that is the one that gets edited and the one
future work is built from. This folder is a snapshot committed alongside the site so the brand
travels with the code and survives if the artifact ever doesn't.

What's in it

  README.md            The brand book: voice, foundations, iconography, motion, where it applies.
  tokens.json          Colors (Paper and Night themes), type scale, spacing, radius, borders.
  components/          Button, ServiceRow, PilotSteps guidelines and previews; Cover.
  assets/Logos/        The six logo files (same files as ../brand/, plus a usage note).
  fonts/               Libre Baskerville and Open Sans as woff2 (open source, OFL).
  design-system.json   The artifact's index. Bookkeeping only; leave it alone.

Keeping them in sync

When the artifact changes, re-copy these files. When something in this folder changes first,
publish it back to the artifact. Don't let the two drift; if they disagree, the artifact wins.

Using the tokens on the site

index.html declares the same values as CSS custom properties on :root. If a token changes in
tokens.json, change it in index.html too; there is no build step wiring the two together.
