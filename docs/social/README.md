# Social cards

One 1280×640 PNG per diagnostician. The same file serves both surfaces: the GitHub
Pages `og:image` and the repo's Social preview.

| File | Card |
|---|---|
| `card.html` | The template. Everything below is baked into it. |
| `og-listing-stall.png` | 1 · *Before you tell them to drop the price.* |

This folder is not part of installing a diagnostician. Nothing here runs at use time and
nothing here is a dependency — it is the tooling that produced the images.

---

## Making the next card

Two ways. Both produce an identical result.

**Edit one line.** Open `card.html`, find the block marked `SWAP THIS ONE LINE`, replace
the text inside `<h1>`. Nothing else in the file changes.

**Or pass it in the URL,** leaving the file untouched:

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
  --headless --disable-gpu --hide-scrollbars \
  --force-device-scale-factor=2 --window-size=1280,640 --virtual-time-budget=2000 \
  --enable-logging=stderr --v=0 \
  --screenshot=_tmp@2x.png "file://$PWD/card.html?line=Before%20you%20blame%20the%20brief."

sips --resampleWidth 1280 _tmp@2x.png --out og-<name>.png && rm _tmp@2x.png
```

Chrome and `sips` both ship with macOS. There is nothing to install.

Render at 2× and downsample. At 1× the 16px mono wordmark and the 1px rules break up.

The console line it prints is the receipt — check it:

```
[card] headline=104px lines=2 avail=376px fits=yes serif=Iowan Old Style
```

`fits=yes` and `serif=Iowan Old Style` both have to be true. See *Guards* below.

---

## Locked decisions

Settled once, on card 1. The next four inherit them so the layout is not re-argued each
time — that consistency is most of what makes five cards read as one family.

### Canvas · 1280×640

The only size that satisfies both targets without a second asset. GitHub's repo Social
preview is 1280×640, and 2:1 is inside the ratio band LinkedIn, X, Slack and Discord
unfurl without cropping.

### Safe area · 1150×510, a uniform 65px inset

`(1280−1150)/2 = 65`, `(640−510)/2 = 65`. Every mark of ink lives inside it.

Outside the inset is bare paper on purpose. The card is cropped and corner-rounded
differently by every surface that renders it, so there is deliberately nothing out there
to lose. No border, no edge rule, no corner ornament — those are the first things a
rounded crop eats.

`card.html` enforces this rather than trusting it. The grid row holding the headline is
`minmax(0,1fr)`, not `1fr`. Plain `1fr` floors at the content's own height, so a long
headline silently pushes the row past 510px and out of the safe area, and — worse — the
fitter then measures the expanded box, concludes it has room, and stops shrinking. With
`minmax(0,1fr)` the row holds 510px and the fitter sees the truth.

### Three tiers, sized for the two viewing distances

The card has to work at ~600px in a feed unfurl and survive as a thumbnail. Those are
different jobs, so the card carries three tiers that fail gracefully in order.

| Tier | Element | Type | At ~600px | At thumbnail |
|---|---|---|---|---|
| 1 | Headline | serif, auto-fit to ~104px | reads | **still reads** |
| 2 | Footnote | sans 19px | reads | drops to texture |
| 3 | Mark + wordmark | mono 16px | reads | drops to texture |

Tiers 2 and 3 becoming texture at small size is the intended behaviour, not a
compromise. Only the line has to survive the thumbnail. In both target contexts the
surrounding chrome already supplies the name — GitHub prints the repo title beside the
preview, and an unfurl prints `og:title` beneath the image — so the card does not need to
repeat it, and spends the space on the line instead.

### Headline

- Face: `"Iowan Old Style", "Palatino Linotype", Palatino, "Book Antiqua", Georgia, serif` —
  the same stack `docs/index.html` uses for `h1`, so the card and the page it unfurls to
  are set in one voice.
- Weight 600 · line-height 1.06 · letter-spacing −0.021em · `text-wrap: balance`.
- Set as the site's own pull-quote: 5px oxblood left rule, 34px gutter. That is
  `.pull` from `docs/index.html` (3px border, 22px padding) scaled to this canvas. The
  card invents no new furniture.
- **Auto-fit: ceiling 104px, floor 60px, 3 lines maximum, 44px of breath.**

104px is the ceiling because it is the largest size at which a ~20-character line still
holds one line inside the 1111px of available text width. 60px is the floor because below
it the headline stops out-shouting the footnote at thumbnail size, which is the entire
job. Three lines is the ceiling on lines because a four-line headline on a 2:1 card reads
as a paragraph.

Measured on this template — no need to re-derive:

| Headline | Resolves to | Lines |
|---|---|---|
| 27 chars | 104px | 2 |
| 39 chars — *card 1* | 104px | 2 |
| 47 chars | 104px | 3 |
| 72 chars | 91px | 3 |
| 89 chars | 70px | 3 |

**Write to roughly 55 characters or fewer.** That keeps the card at or near the 104px
ceiling, which is where the thumbnail still works. Past about 75 characters the fitter
protects the layout but the line gets quiet, and a quiet line on this card has nothing
else to fall back on.

If a headline hits the 60px floor and still does not fit, the template says so
(`fits=NO`). Cut the line. Do not lower the floor.

Manual line breaks are available — put a `<br>` in the `<h1>` and the fitter respects it.
`text-wrap: balance` has handled every case so far.

### Wordmark and mark

`AI DIAGNOSTICIANS` in mono, 16px, 0.155em tracking, uppercase, `--muted`. Subordinate to
the line by a wide margin, which is the point: the line does the clicking.

The mark is a baseline carrying four stations with the third fallen below it — the one
rule every diagnostician in the family runs on. It is drawn as displacement rather than
as a hanging object: the dropped station is nearly the same size as the ones on the line,
joined by a hairline. An earlier draft made it large on a thick stem and it read as a
plumb bob. It carries no domain in it, so it survives whatever the remaining four turn
out to diagnose.

### Footnote

Constant on every card in the family. Compressed from the repo README's own sentence, no
new claim introduced:

> Works backward from what already failed. Names one cause. Stops before prescribing.

### Palette · light only

Lifted verbatim from the `:root` light theme in `docs/index.html`:

| Token | Value | Use |
|---|---|---|
| `--paper` | `#faf8f5` | ground |
| `--ink` | `#16130f` | headline |
| `--muted` | `#5f584f` | wordmark, footnote |
| `--line` | `#e2dcd3` | hairline rules |
| `--accent` | `#8a3324` | pull rule, the fallen station |

No dark variant. `og:image` does not respond to `prefers-color-scheme`, so a dark card
would be a second asset to keep in sync for no gain.

No gradient, no glow, no chart mockup, no arrow. The register is a chart, not a launch.

---

## Guards

`card.html` checks two things at render and reports both on the console.

**`serif=`** — Iowan Old Style is a macOS system face. It is **not embedded**: this repo
is MIT and the font is not redistributable, so the template calls it by name and the repo
ships only the rendered PNG. On a machine without it the stack falls through to Palatino
→ Book Antiqua → Georgia, the metrics change, and the card quietly stops matching the
other four. The template prints `serif=FALLBACK` and warns rather than letting that ship.

**`fits=`** — `yes` only if the fitted headline is inside the safe area and within three
lines. Anything else is `fits=NO` plus a console warning.

---

## Wiring

`docs/index.html` points `og:image` at `og-listing-stall.png` by absolute URL, as the
spec requires.

The repo's Social preview is a manual upload and cannot be set from the repo tree:
**Settings → General → Social preview → Upload an image**, same PNG.
