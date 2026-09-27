# Second Shift

Second Shift Automation, LLC builds sturdy automations for firms in the Dallas area: intake, document generation, client updates, folder and calendar setup, on the software the firm already owns. The name is literal: the work happens after hours, on the second shift, and the mark is a circle with its second half filled.

This system is the single reference for everything that carries the brand: the website at 2shifts.com, the cold email signature, the cal.com booking page, invoices, the pilot handoff guide, and any deck or one-pager that follows. Start here, take the tokens and the marks from here, and update here when something changes.

## Voice

- Plain, specific, unhurried. Say what the automation does in the words a paralegal would use ("the form becomes a contact, a conflict check, an open matter"), never in vendor words ("leverage AI-powered workflows").
- First person singular. It's one person doing the work, and the copy says so: "I'd rather earn the first few references than charge for them." The exception is anything that states a commitment: the confidentiality page, the pilot scope, the engagement letter, invoices. Those carry no first person, because a commitment binds the company and should read that way to someone who reads contracts for a living.
- No superlatives, no urgency theater, no exclamation marks. The word "free" doesn't appear; the pilot is "on me" or "no invoice." Neither "small" nor "law" describes the client; say "firms" and let the work describe the size and the sector. The scarcity line ("two pilot firms this quarter") is a fact, stated once, in caption size.
- Legal readers are the first audience, so nothing legal in the styling: no scales, no columns, no navy-and-gold, no Times New Roman. Nothing anti-legal either: no neon, no startup gradients, no emoji.
- Punctuation: a true em dash (—), unspaced, where a dash belongs in site and document copy. Sentence case for headings. Uppercase only via CSS on the kicker style.
- US English. Numbers as numerals in copy ("30 days", "20 minutes per matter").

## Visual foundations

**Paper and ink.** The page is warm off-white `surface` (#f5f1ea), the type is near-black `ink` (#1c1a17). Neither is ever pure white or pure black. One band per page inverts (`surface-inverse`) to carry the pilot terms; everything else stays on paper. The Night theme swaps the two and is used only for dark contexts (a dark-mode email client, the dark avatar), never as a second look for the site.

**Rules, not boxes.** Content is separated by 1px hairlines in `rule`, with a heavier `rule-strong` line opening and closing a section. There are no cards with borders, no drop shadows, no filled panels. If something needs containment, it gets a rule above and below it.

**Two shapes.** Square edges for everything editorial (rows, tables, images, sections). Full pills (`radius-pill`) for anything pressable. The 24px `radius-tile` exists only for the avatar tile in a gallery. Nothing in between.

**One accent, one signal.** `accent` (#2f4f3e, deep green) appears once per screen: an italic word in the headline, the numerals in a step list, a link, a button hover. `signal` (#f2b35c, amber) is the dot in the mark and appears nowhere else in the interface. It's the light left on, not a UI color.

**Type.** Libre Baskerville (serif) for anything that names or declares: the wordmark, headlines, section titles, row labels. It ships in 400 and 700 only; headlines are 400, and 700 is reserved for the rare bold word inside body copy set in the serif. Open Sans for anything you read: paragraphs, lists, buttons, captions. Both are open-source and the files ship with this system; the stacks fall back to Georgia and system sans. Display sizes are set with `clamp()` between the mobile and desktop values in the type scale; 17px is the floor for running text. Libre Baskerville is a wide face, so headlines stay to two or three lines and the hero tops out at 72px.

**Layout.** One content column at `page` (1120px), margins of 24px on small screens. Hero: 3:1 split, headline left, a one-line status note right sitting on a hairline. Services: a three-column ledger (label 220px, body fluid, fit-note 260px) that collapses to one column under 860px. Sections breathe at `space-16` on desktop and 56px on mobile.

## Iconography and marks

The mark is a circle with its second half filled and an amber dot at the center. Two versions, same geometry:

- `mark-light.svg` -- ink on a transparent ground, for paper backgrounds (the site header, invoices, light email).
- `mark-dark.svg` -- paper on a transparent ground, for ink backgrounds (the inverse band, dark-mode contexts).
- `avatar-light-512.png` / `avatar-dark-512.png` -- the mark on its own ground, square, for profile photos (cal.com, Google Workspace, LinkedIn). Use light by default.
- `wordmark-light.svg` / `wordmark-dark.svg` -- mark plus "Second Shift" in Libre Baskerville 400, for email signatures and document headers.

Rules: the mark always sits to the left of the wordmark with a `space-3` gap, and the wordmark is the type style `wordmark`, never a rasterized image of it. Minimum size 24px; at 16px (favicon) the dot may be dropped but the half circle stays. Never rotate, recolor beyond the two versions, add a gradient, or put the mark inside another shape. The geometry in the SVGs is the source; do not redraw it.

There is no icon set. Interface icons, when needed, are 1.5px-stroke line icons in `ink` or `muted` at 20px, from a single open set (Lucide), and are used only where a word would be worse.

## Motion

One animation, on the mark, once per page load: the filled half sweeps clockwise from twelve o'clock over 900ms (the second shift coming on), then the amber dot lights over 400ms. Nothing else on the site moves apart from hover states and smooth anchor scrolling. Under `prefers-reduced-motion` the sweep still plays but in a third of the time, and the page scrolls instantly. The sweep is a stroke-dashoffset on a 40-unit stroke circle of radius 20 inside the 100-unit viewBox; the geometry is in the site header and should be copied, not re-derived.

## Components

The site is built from four pieces, documented under Components: the pill button in its two weights, the ledger row that lists a service, the numbered step list that states the pilot terms, and the header/footer band. Anything new should be composed from these and the rules above before a new component is added.

## Where this applies

- Footer carries © [year] Second Shift Automation, LLC on its own line, then city and email.
- Website: 2shifts.com, static HTML, the tokens above as CSS custom properties on `:root`.
- Email: plain text preferred for outreach. Signature: wordmark-light at 160px wide, name, "Second Shift Automation, LLC", dustin@2shifts.com, 2shifts.com.
- cal.com: avatar-light-512.png as the profile image; the booking page description in the voice above.
- Documents (pilot scope, handoff guide, invoices): Libre Baskerville headings, Open Sans body, paper ground when printed to PDF, `rule` hairlines for tables.
