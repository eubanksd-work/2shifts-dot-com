# 2shifts.com

The website for Second Shift Automation, LLC. Two static pages, no build step, hosted on GitHub Pages at the custom domain 2shifts.com.

## What's here

```
index.html          The main page. All HTML, CSS and the one animation live in this file.
confidentiality.html  Where client data lives, for firms that ask before engaging. Self-contained, same shape as index.html.
404.html            Served for any address that isn't a real page. Same design, no animation, deliberately.
CNAME               Tells GitHub Pages which domain serves it. Leave as-is.
.nojekyll           Stops GitHub Pages running the files through Jekyll. Leave as-is.
fonts/              The three woff2 files the site loads, plus their licenses (see below).
brand/              Every logo, icon and image asset (see below).
design-system/      File copy of the design system (tokens, brand book, components, fonts). See its ABOUT.md.
private/            Not in this repo. Ignored here and kept in its own private repository. See below.
README.md           This file.
```

## private/

This repo is public and GitHub Pages serves the whole root, so anything that should not be read by strangers lives in `private/`. That folder is listed in `.gitignore` and is its own git repository, pushed to the private `2shifts-private` repo. A fresh clone of this repo does not include it; clone `2shifts-private` into `private/` to get it back.

```
private/documents/       Draft business paperwork: pilot scope, engagement letter, handoff guide, invoice.
private/backlog.md       What's deliberately not done yet, and why.
private/memory-bank.md   Working status between sessions. Short-lived; not a record.
```

Changes under `private/` are committed and pushed from inside `private/`, separately from the site.

## Deploying

Push to `main`. GitHub Pages (Settings → Pages → source: main, root) publishes within a minute or two. Hard-refresh (Ctrl+Shift+R) if a change doesn't show; Pages caches aggressively.

`2shifts.com` is verified at the GitHub account level (Settings → Pages → Verified domains), which is what stops anyone else claiming the domain on their own Pages site if this repo is ever renamed or deleted. Keep the `_github-pages-challenge-<account>` TXT record at Namecheap; removing it un-verifies the domain. Turn on Enforce HTTPS once the domain is cut over and the certificate issues.

DNS at Namecheap is half done. Google Workspace mail is live (`MX` to `smtp.google.com`), and the GitHub Pages domain-verification `TXT` record is in place and verified. The web records are still Namecheap's parking defaults, so the domain does not serve this site yet. To cut it over, replace the parked `A` record on `@` with GitHub's four, and repoint the `www` `CNAME` away from `parkingpage.namecheap.com`:

```
A     @     185.199.108.153
A     @     185.199.109.153
A     @     185.199.110.153
A     @     185.199.111.153
CNAME www   <github-username>.github.io.
```

Leave every `MX` and `TXT` record alone; they carry mail and the domain verification. Nothing in this repo touches DNS.

## Editing copy

The pitch is in `index.html`. The sections in order: header, hero, services (a ledger of rows), pilot (the dark band with the terms), about, footer. Find the text, change it, commit. Keep to the voice in the design system: first person, plain, no "free", no "small", no "law" as a descriptor of the client, a true em dash where a dash belongs.

`confidentiality.html` is the exception on first person. It states commitments, so it uses none; see Voice in the design system.

The footer year is hard-coded; bump it each January.

## Fonts

Libre Baskerville (headings, wordmark) and Open Sans (everything you read), self-hosted from `fonts/` and declared in the `@font-face` rules at the top of the `<style>` block. Nothing the site loads comes from a third party, so no visitor request leaves this origin and there is nothing to disclose about font CDNs.

Three files, latin subsets, about 90 KB together:

| File | Covers |
|---|---|
| `open-sans-latin-var.woff2` | Open Sans, variable, weights 400/500/600 from one file |
| `libre-baskerville-latin-400.woff2` | Libre Baskerville regular |
| `libre-baskerville-latin-400-italic.woff2` | Libre Baskerville italic, used by the one word in the headline |

These are the same bytes Google Fonts serves for the latin subset. The full-unicode originals are in `design-system/fonts/`; don't swap them in, they are eight times the size for characters the copy never uses. To refresh a file, request it from the Google Fonts `css2` API and take the URL whose `unicode-range` begins `U+0000-00FF`.

Both families are SIL Open Font License 1.1. `fonts/LICENSE-LibreBaskerville.txt` and `fonts/LICENSE-OpenSans.txt` are the license texts, and they have to stay with the font files. That is the whole obligation: keep them in the repo, don't rename the families.

## The mark and its animation

The header logo is an inline SVG: an outlined circle, a filled second half, an amber dot. The filled half is drawn as a thick stroke on a smaller circle and swept in with `stroke-dashoffset` on first load (900ms), then the dot fades in (400ms). Pure CSS, plays once. The geometry (radius 20, stroke 40, dash 62.832 of 125.664) is documented in the design system under Motion; copy it, don't re-derive it.

## brand/ assets

| File | Use |
|---|---|
| `mark-light.svg` | The mark, ink on transparent. Light backgrounds. Source of truth for the geometry. |
| `mark-dark.svg` | The mark, paper on transparent. Dark backgrounds. |
| `avatar-light.svg`, `avatar-light-512.png` | Mark on its paper ground, square. Profile photos: cal.com, Google Workspace, LinkedIn. **Default.** |
| `avatar-dark.svg`, `avatar-dark-512.png` | Same on the ink ground, for platforms that put avatars on black. |
| `wordmark-light.svg`, `wordmark-light-2x.png` | Mark + "Second Shift". Email signature (use the PNG at 160px wide), document headers, invoices. |
| `wordmark-dark.svg`, `wordmark-dark-2x.png` | Same for dark contexts. |
| `favicon.svg` | The tab icon: the mark alone, scaled to the edges, flips to paper on dark tab strips. Referenced in `<head>`. Source for the raster icons below. |
| `favicon.ico` | Legacy favicon (16/32/48). Referenced in `<head>`. |
| `icon-16.png`, `icon-32.png` | PNG favicons. `icon-32` is referenced in `<head>`. |
| `icon-192.png`, `icon-512.png` | Android / PWA icons if a web manifest is ever added. |
| `apple-touch-icon.png` | iOS home-screen icon (180px). Referenced in `<head>`. |
| `og-image.png` | 1200×630 link preview for iMessage, LinkedIn, Slack, Teams. Referenced in `<head>`. Regenerate if the hero headline changes. |

Rules: never redraw the mark, recolor it beyond the two versions, rotate it, or put it inside another shape. The amber dot is `#F2B35C` everywhere and appears nowhere else on the site.

## Colors and type, in short

| Token | Value | Use |
|---|---|---|
| paper | `#F5F1EA` | page ground |
| ink | `#1C1A17` | text, wordmark, primary button, the inverse band |
| muted | `#4A463F` | body copy, captions |
| rule | `#C9C2B6` | hairlines between rows |
| accent | `#2F4F3E` | one italic word in the headline, links, step numerals, hover |
| amber | `#F2B35C` | the dot in the mark only |

Full tokens, type scale, spacing, components and the brand book are in `design-system/` (a copy of the Second Shift design system artifact, which is the live version); this table is the subset the site uses.

## License

Copyright 2026 Second Shift Automation, LLC. All rights reserved.

There is deliberately no `LICENSE` file. A public repo without one is all-rights-reserved by
default, which is what this repo needs: it holds the mark, the wordmark, the brand book and the
site copy, and an MIT or Apache file would grant strangers the right to reuse all of it. This
section states that intent rather than leaving it implied. Don't add an open-source license
here without deciding what it would give away.

The fonts are the one exception. Everything in `fonts/` and `design-system/fonts/` is separately
licensed under the SIL Open Font License 1.1, and those terms are unaffected by the line above.
See the Fonts section.
