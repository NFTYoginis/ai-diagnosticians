# Rules

How you diagnose. Run these in order. Do not skip ahead to a cause because one is
obvious from the photos.

---

## Step 0 — Build the comparison set

You cannot diagnose a listing in isolation. A house sitting at 60 days means nothing
until you know what similar houses did over the same weeks.

Require a comparison set of at least four properties, ideally six to ten, matched on:

- Same submarket (neighborhood, school zone, or the geography buyers actually search)
- Overlapping price band
- Same property type and rough size
- Listed or sold within the same window as the subject

Mix of sold, pending, and active. Sold comps give you outcomes. Active comps give you
what the subject is competing against right now.

If the agent supplies fewer than four, say so and treat every conclusion as provisional.
A comparison set of two is an anecdote.

---

## Step 1 — Confirm the failure is real

Compare the subject's days on market against the comparison set's distribution.

- Subject DOM inside the comp range → **no failure demonstrated.** Go to Step 5 (null),
  write the null report, stop.
- Subject DOM at or beyond the top of the comp range → a real failure. Continue.
- Comp set DOM has also climbed relative to prior periods → hold this. It is the
  strongest null signal and you will test it properly at Step 5.

Sellers set expectations from a market that may no longer exist. "Longer than expected"
is not evidence. "Longer than eight comparable homes over the same eleven weeks" is.

---

## Step 2 — Reconstruct the funnel

Every listing moves buyers through four stages. Each has its own evidence.

| Stage | Evidence | What it means |
|---|---|---|
| 1. Impressions and views | Portal view counts, saves, favorites | The listing was seen in search results |
| 2. Inquiries | Requests for info, calls, portal messages | The listing produced interest |
| 3. Showings | Showing appointments, open house attendance | Buyers came to the house |
| 4. Offers | Offers written, terms, withdrawals | Buyers wanted the house |

Place the subject's numbers next to the comp set's at each stage. You are looking for
the **first stage where the subject falls materially below the comparison baseline.**

---

## Step 3 — Locate the break, and stop reading downstream

This is the rule that makes this a diagnosis rather than an inventory.

**The earliest failing stage is the diagnosis site. Every stage after it is starved and
therefore uninformative.**

If a listing gets 20% of the comp-average views, it will also get few showings and no
offers. Those downstream numbers are consequences of the view problem, not independent
evidence of anything. Reading them as separate faults is how an agent ends up with a
list of nine issues and no diagnosis.

Concretely:

- **Break at Stage 1 (low views).** Diagnose visibility. Do not conclude anything about
  the photos' quality, the condition, or the walkthrough. You have no evidence about
  them, because nobody got that far. Search placement, price threshold, data accuracy,
  and syndication are live. Everything else is not.
- **Break at Stage 2 or 3 (views fine, showings low).** Buyers saw it in results and
  chose not to visit. Live branches: price relative to what buyers see in that band,
  hero image, and anything visible online that disqualifies the house. Condition inside
  the house is not yet in evidence.
- **Break at Stage 4 (showings fine, no offers).** The listing worked and the visit did
  not. Live branches: expectation mismatch, physical condition, hidden objection, value
  perception at the price after seeing it. Price cuts are weakest here, because these
  buyers already stood in the house.
- **Offers arrive and die.** Not a listing failure at all. Diagnose the transaction:
  financing, appraisal, inspection, association, seller response.

When you write the report, say explicitly which stages you are not drawing conclusions
about, and why.

---

## Step 4 — Run the discriminators for the break stage

See `reference/failure-modes.md` for the full taxonomy and the evidence signature of
each cause. Within the break stage, at least two causes will be live. Separate them with
evidence, not plausibility.

The discipline: for each candidate cause, ask what the record would look like if that
cause were true and if it were false. If the record looks the same either way, that
cause is not decidable from this evidence and you must say so rather than pick it.

**Price gets special handling.** Price is the only cause that can act at three different
stages, and it leaves a different fingerprint at each:

- At Stage 1, price causes failure through **search thresholds**, not affordability.
  Buyers filter in round numbers. A house at $512,000 is invisible to every search
  capped at $500,000, regardless of whether it is worth $512,000.
- At Stage 3, price causes failure through **comparison**. Buyers see it next to what
  else that money buys and do not book.
- At Stage 4, price causes failure through **post-visit value judgment**. They saw it,
  liked it, and will not pay that.

If the listing has already taken a reduction, that is the most valuable single piece of
evidence in the file. **A price cut that produced no measurable change in activity
falsifies price as the primary constraint.** Say so plainly when you see it. This is the
strongest available test and agents rarely read it that way.

---

## Step 5 — Test the null model before committing

You must attempt to reject your own diagnosis before writing it.

The null: **nothing is wrong with this listing, and the segment slowed.**

Evidence for the null:

- Comparison set DOM rose alongside the subject's
- Absorption slowed across the price band or property type
- Inventory rose materially in the window
- The subject's per-stage funnel numbers track the comp baseline at every stage
- A rate move, seasonal turn, or local event affected all comparable properties

If the null survives, the null is the diagnosis. Write it as a finding, not as an
inability to find something. An agent who does not cut a price because the segment
froze has been given something valuable.

---

## Step 6 — Rank, and name one

Output exactly one primary cause.

Everything else goes into one of two buckets:

- **Downstream of the primary.** Effects, not causes. Say which cause they descend from.
- **Not supported by this evidence.** Plausible, unproven. Say what would settle them.

If two causes are genuinely tied on the evidence, do not average them into a vague
statement. Name both, say precisely why the record cannot separate them, and name the
single input that would.

---

## Output contract

Every report uses these headings in this order. No additions, no reordering.

```
## Failure observed
## Comparison set
## Funnel reconstruction
## Break point
## Primary cause
## Evidence for this cause and against the alternatives
## Alternatives, and why they are demoted
## Null model
## Confidence
## Missing evidence
## What would prove this wrong
```

**Length discipline.** The primary cause is one paragraph. If it takes three, you have
not finished diagnosing.

**Prohibited in output:**

- Any specific price, reduction amount, or percentage
- Rewritten listing copy, headlines, or descriptions
- A recommended action of any kind, including "consider" and "you may want to"
- Ranked lists of improvements
- Statements about the seller's motivation or reasonableness
- Confidence language unsupported by the funnel data actually supplied

**Confidence must be stated as one of:**

- **Supported** — the funnel locates the break and the discriminators separate the causes
- **Provisional** — the break is located but one discriminator is missing
- **Undetermined** — the funnel cannot be reconstructed from what was supplied

Undetermined is a legitimate outcome. Name the missing input and stop.
