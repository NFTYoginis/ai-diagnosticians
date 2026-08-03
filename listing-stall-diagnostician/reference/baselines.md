# Baselines

The comparison set is what turns an opinion into a diagnosis. This file covers how to
build it and how to decide what counts as underperformance.

There are no national benchmark numbers here on purpose. Showing rates, view counts, and
normal days on market vary enormously by market, price band, season, and portal. Any
figure quoted as an industry average would be wrong in most markets and would be treated
as authoritative anyway. **Every baseline in a diagnosis is computed from that case's own
comparison set.**

---

## Building the comparison set

Match on the axes buyers actually use when they search:

- **Geography** — the area buyers search, which is often a school zone or a named
  neighborhood rather than a radius or a zip code.
- **Price band** — overlapping, not identical. A house competes with everything a buyer
  sees inside their filter range.
- **Property type and size** — same type, similar bed and bath count, square footage
  within a range that would appear in the same search.
- **Window** — listed or sold inside the subject's active period. A comp that sold eight
  months ago describes a different market.

Four is the floor. Six to ten is a usable set. Below four, state that the range is not
established and cap confidence at Provisional.

**Include actives, not just solds.** Sold comps tell you what the market cleared. Active
comps tell you what this listing is competing against on a buyer's screen right now, and
that is what determines whether it gets a click and a showing.

---

## Establishing the DOM range

Take days on market for every comp. You need the spread, not the average.

The subject is underperforming when its DOM sits **at or beyond the top of the comp
range**, not when it exceeds the mean. Half of all listings exceed the mean by
definition, and treating the mean as a target manufactures failures that do not exist.

Then check whether the range itself moved. If comps listed early in the window sold in
two weeks and comps listed late are still sitting, the market changed mid-listing and
the null model is live before you look at anything else.

---

## Per-stage baselines

For each funnel stage, compute the comp set's figures and compare.

**Views.** Portal view counts across comps, normalized for time on market, since a
listing live for 60 days accumulates more views than one live for 14. Compare views per
week, not views total. This normalization is the most common error in agent-run
comparisons.

**Inquiries and saves.** Absolute counts are noisy. The useful figure is the ratio to
views, which tells you whether the listing converts attention into interest.

**Showings.** Showings per week against the comp set. Also compute showings as a
proportion of views, which separates "nobody saw it" from "people saw it and passed."

**Second showings.** As a proportion of first showings. This is the most diagnostic
figure available at Stage 4 and it is frequently sitting unused in the showing platform.

**Offers.** Count and timing relative to showing volume.

---

## What counts as "materially below"

Judgment, stated explicitly in the report rather than applied silently.

- **Clearly below** — subject is under the lowest comp in the set on that stage. Treat
  as a located break.
- **Ambiguous** — subject sits inside the comp range but in the bottom quarter. Note it,
  do not treat it as the break unless a later stage is clearly below.
- **At baseline** — subject sits inside the comp range. This stage is not the break.
  Move to the next stage.

If no stage is clearly below, the funnel is performing at market and the null is likely
the answer. Do not manufacture a break by lowering the bar until one appears.

---

## The reduction test

The single most useful piece of history in any case file.

If the listing has already taken a price reduction, compare activity for the two weeks
before and the four weeks after.

- **Activity rose materially** — price was a real constraint at the stage where activity
  rose. Note which stage responded, because that identifies the mechanism.
- **Activity unchanged** — **price is falsified as the primary constraint.** The market
  was given the number it supposedly wanted and did not respond. State this directly.
- **Views rose but showings did not** — the reduction crossed a search threshold and
  fixed a visibility problem, exposing a second constraint underneath.

Agents routinely read an unresponsive reduction as evidence that the cut was too small.
Read it the other way. It is a completed experiment with a clean result.

---

## Seasonality and rate moves

Before attributing a slowdown to the listing, check whether the window contains a
seasonal turn or a rate move that affected the whole band. If the comparison set is
matched on window, this is already controlled for, which is why the window match matters
more than most agents assume.

A subject listed in a strong month and compared against comps listed in a weak month
will look artificially bad, and vice versa. When windows cannot be matched, say so and
treat the comparison as weakened.
