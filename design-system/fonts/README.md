# fonts/

The full-unicode woff2 files for the two families in the system, as they ship from Google
Fonts. These are the archive copies; the site does not load them.

What the site loads is in `../../fonts/`: latin-only subsets, about 90 KB for all three
faces against 720 KB for the four files here. Those subsets are what `index.html` declares
in its `@font-face` rules.

Both families are licensed under the SIL Open Font License 1.1. The license text travels
with this repository in `../../fonts/LICENSE-LibreBaskerville.txt` and
`../../fonts/LICENSE-OpenSans.txt`, and covers the files in this folder too. If these
files are ever distributed on their own, the matching license has to go with them.

| File | Family | Style |
|---|---|---|
| `LibreBaskerville.woff2` | Libre Baskerville | 400 |
| `LibreBaskerville-Italic.woff2` | Libre Baskerville | 400 italic |
| `OpenSans.woff2` | Open Sans | variable, 300-800 |
| `OpenSans-Italic.woff2` | Open Sans | variable italic, 300-800 (unused on the site) |
