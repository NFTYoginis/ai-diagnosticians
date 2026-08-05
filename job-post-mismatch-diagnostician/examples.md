# Examples

Three worked cases. They show the reasoning, not just the conclusion.

The cases are constructed for teaching, with figures chosen to make each discriminator legible.
They are not client files, and no case contains an application, a résumé, or a candidate. Every
figure at Stage 4 is an aggregate count the employer's own screening produced.

Between them they also show the three possible verdicts on a prior compensation change: one
qualifying raise that returned a positive result at one stage and a negative at another, one case
with no change to read, and one non-qualifying change that is treated as no evidence at all.

---

## Case 1 — Break at Stage 4

**Input:** Senior data engineer, hybrid, one metro, posted range $155,000 to $175,000. 44 days
open, raised from $145,000–$165,000 and republished on day 19. Comparison set of seven open
requisitions at the same company. Channel-level funnel data and by-channel screening counts.

### Failure observed

Qualified submissions at 1.7 per week against a comparison range of 5.9 to 11.4. Days open at 44
against a comparison range of 16 to 38, with five of seven filled. Below the range on both
measures. Failure confirmed.

The funnel below is computed on the **25 days since the day-19 change**, not on the full 44. The
raise crossed a filter floor and lifted reach 30% within a range it already sat inside, which
creates two regimes. Pooling them would average a resolved constraint into an unresolved one and
hide both.

Eleven candidates who reached first contact through referral were routed out before any rate was
computed.

### Comparison set

Seven open requisitions at the same company, same window, adjacent level, all hybrid in the same
metro, bands between $150,000 and $185,000, all running on the same three channels at comparable
sponsorship spend: senior backend, senior platform, staff analytics, senior SRE, senior
full-stack, data scientist, senior ML.

Requirement structure varies freely across the set, which is required rather than tolerated: a set
matched on requirement structure could not detect a requirement problem.

### Comparison-set integrity

**Usable.** Role family, seniority, band, location, work model, window, channel mix, spend, and
employer exposure all match. One limitation, named and handled: data scientist is a different role
family drawing a different population. It is retained for the reach and consideration baselines,
where channel behaviour is what matters, and excluded from the screening-pass baseline. That
baseline is computed from six. Removing any single one of the six leaves the pass range at 24% to
39% and does not change the finding. No single requisition carries the baseline.

### Funnel reconstruction

| Stage | Subject | Comparison range | Read |
|---|---|---|---|
| 1. Reach | 18,400 impressions per week | 12,900 to 21,600 | At baseline since day 19 |
| 2. Consideration | 4.1% view rate, 11% apply-start rate | 3.4–4.8%, 9–14% | At baseline |
| 3. Application | 68% of apply-starts submitted | 61% to 79% | At baseline |
| 4. Screening pass | 6% of 231 submissions met all stated must-haves | 24% to 41% | **Clearly below** |
| 5. Interview conversion | 9 of 14 screened-in scheduled | insufficient volume | Not assessable |

By channel, the figure the discriminator runs on:

| Channel | Submissions | Met all must-haves | Pass rate |
|---|---|---|---|
| General board | 141 | 8 | 5.7% |
| Niche board | 74 | 5 | 6.8% |
| Careers page | 16 | 1 | 6.3% |

### Primary constraint

**Stage 4, screening pass.** The requisition is served, opened, and completed at baseline. Volume
is not the problem: 231 submissions in 25 days sits inside the comparison range. Six percent met
the stated must-haves, against a comparison range of 24 to 41 percent.

Stages 1 through 3 are not the diagnosis site, and no conclusion is drawn about the title, the
listing card, the stated range's competitiveness, or the application form. Those demonstrably
worked. Stage 5 has fourteen screened-in candidates, which is not a readable sample, and nothing
is concluded from it.

### Primary cause

**Requirement signaling.** The stated requirements read as a different job than the one being
hired for.

### Mechanism

The requirement block opens with six named tools and three reporting and dashboard
responsibilities, and the two attributes that actually define the role — ownership of a production
streaming pipeline, and five years in data engineering — appear at positions 12 and 17 of 19 in a
single undifferentiated list. The tools named are the tools an analytics-engineering team uses.
Candidates read the block, price the post as an analytics or BI role, and a different and
generally more junior population self-selects in. The pass failures are not spread across the
list: 214 of the 217 failures miss on the same single must-have, production pipeline ownership.

### Evidence for this cause and against the alternatives

The by-channel spread is the discriminating figure. Pass rate is 5.7%, 6.8%, and 6.3% across three
channels with materially different populations — a general board, a specialist board, and direct
traffic to the careers page. A channel-population problem concentrates: one channel would supply
most of the volume and almost none of the passes while the others sat near the comparison range of
24 to 41 percent. A signaling problem is uniform, because the post says the same thing everywhere.
The spread here is 1.1 points.

The concentration of failures is the second measure. 214 of 217 failures miss on one requirement.
A pile drawn from the wrong population fails on many things at once. A pile drawn by a signal that
describes a neighbouring job fails on the one attribute that distinguishes the two.

Volume at baseline is what makes this a Stage 4 finding rather than a Stage 1 or 2 one. The post is
reaching people and they are applying at a normal rate. They are the wrong people.

### Alternatives, and why they are demoted

**Compensation.** Not supported, and the day-19 raise is readable here. It moved the lower bound
from $145,000 to $155,000, crossing the $150,000 increment both general channels index on, and the
post was republished rather than edited in place, so the market re-saw it. Nothing else changed:
no title edit, no requirement change, no new channel, no spend change. Twenty-five days of
observation follow it, against a comparison-set median time to first qualified slate of 18 days.
The market held.

**That is a qualifying change, and it tested the floor and comparison mechanisms.** Impressions
rose from 14,200 per week to 18,400. At 14,200 the post was already inside the comparison range of 12,900 to 21,600, in its bottom quarter.
**Positive at Stage 1.** The screening pass rate did not move: 6% before, 6% after. **Negative at
Stage 4.** Two findings, not one. The raise solved a real distribution constraint and exposed the
one underneath it, which was there the whole time.

It says nothing about post-conversation value judgment, which is not in evidence because Stage 5
has insufficient volume.

**Channel-population mismatch.** Ruled out by the by-channel spread above.

**Must-haves not marked as must-haves.** Live, and not separable from requirement signaling on
this evidence, because the post does both: the list is undifferentiated *and* it foregrounds a
neighbouring job family's attributes. The concentration of failures on a single stated requirement
favours signaling, since an unmarked-must-have problem tends to spread failures across whichever
items sit lowest in the list. This is a lean, not a separation, and the single input that would
settle it is a variant of the post with required and preferred split and the ordering unchanged.

**Screening rule and post disagree.** Checked and ruled out. Every criterion in the written
screening rules appears in the published post. The requirement the failures concentrate on is
stated — at position 17 of 19, which is a signaling finding rather than a screening finding.

**Application friction.** Not supported. Stage 3 at baseline.

### Null model

Rejected. Six of seven comparison requisitions in the same window, at the same band, metro, and
work model, produced pass rates of 24% to 41% on comparable submission volumes. The population
exists and it is applying to this company. It is not applying to this post as qualified.

### Confidence

**Provisional.** Comparison set is Usable, the constraint is located by both level and
pass-through, and the null was tested and rejected. The by-channel spread separates requirement
signaling from channel-population mismatch cleanly.

It does not separate requirement signaling from unmarked must-haves, and that is what holds the
grade. Both are live at the break stage, both are properties of the same requirement block, and
the lean toward the former rests on the shape of the failure distribution rather than on a
discriminator. The contract gives Supported only when the discriminators separate the live
causes, and here one pair is unseparated with the separating input named as missing. A lean is
not a separation, and the grade has to say so rather than the alternatives section saying it
while the confidence line claims otherwise.

The stage-level finding does not depend on the split. Both causes sit at Stage 4 and both are
fixed by looking at the requirement block. What is not established is which of the two is doing
the work, and a recruiter is better served knowing that than being told the question is closed.

### Missing evidence

Withdrawal reasons for the five screened-in candidates who did not schedule. Fourteen is too few to
read and no attempt is made. No channel supplied reach composition, so whether the impressions
landed on the target population is inferred from the comparison requisitions' performance on the
same channels rather than measured.

### What would prove this wrong

By-channel pass rates diverging sharply once the two lower-volume channels accumulate more
submissions, which would move this to channel-population mismatch. Or written screening rules
containing a criterion absent from the post, which would move the finding from the post to the
screen and change its owner.

---

## Case 2 — Break at Stage 1

**Input:** Mid-level QA automation engineer, fully remote within one country, posted range $92,000
to $104,000. 38 days open, no edits of any kind. Comparison set of five. Channel-level funnel data.

### Failure observed

19 submissions in 38 days, against a comparison range of 140 to 310 over comparable periods. Days
open at 38 against a comparison range of 14 to 31. Below the range on both. Confirmed.

### Comparison set

Five open requisitions at the same company, same window, same three channels, all fully remote in
the same country, adjacent level, bands between $92,000 and $115,000.

### Comparison-set integrity

**Usable with limitations.** Four of five match on band, location, work model, window, channel
mix, and sponsorship spend. The fifth ran at roughly triple the sponsorship spend of the others, so
its impression figures are not comparable at any normalization this data supports. It is retained
for the consideration and application baselines, which are rate-based and spend-insensitive, and
excluded from the reach baseline.

That leaves the reach baseline drawn from four, which is the floor. The Stage 1 finding depends on
it. Confidence caps at Provisional.

### Funnel reconstruction

| Stage | Subject | Comparison range | Read |
|---|---|---|---|
| 1. Reach | 2,900 impressions per week | 11,400 to 19,800 (four) | **Clearly below** |
| 2. Consideration | 3.8% view rate | 3.2% to 5.1% | Rate at baseline, volume starved |
| 3. Application | 19 submissions total | 140 to 310 | Below, starved |
| 4. Screening pass | 2 of 19 | 21% to 38% | Insufficient volume, not assessable |
| 5. Interview conversion | 1 of 2 | insufficient | Not assessable |

Impressions by channel:

| Channel | Subject per week | Comparison range per week | Salary floor filter |
|---|---|---|---|
| Board A | 1,100 | 6,800 to 12,400 | yes |
| Board B | 1,510 | 4,100 to 7,900 | yes |
| Careers page | 290 | 210 to 460 | no |

### Primary constraint

**Stage 1, reach.** Under a quarter of the lowest comparison requisition. Every subsequent stage is
starved.

Nothing is concluded about the requirement list, the body copy, or who this post attracts.
Nineteen submissions is not a readable sample and the two that passed screening are not evidence
about anything.

### Primary cause

**Compensation filter floor.**

### Mechanism

The range is posted as $92,000 to $104,000. **The team supplied both boards' published filter
documentation with the case:** each indexes a posted range on its **lower** bound and offers
candidate-set minimums in $10,000 increments. Indexed at $92,000, the post is absent from every
search floored at $100,000 — the recruiter supplied both boards' published filter documentation with the case, establishing lower-bound indexing in $10,000 increments. What share of searches use any given floor was not supplied and is not assumed. Its
actual top of $104,000 would clear that floor comfortably. The role is not underpaid. In the
searches that matter, it is not present.

*Note on why that attribution is written out.* A channel's indexing rule is a fact about that
channel, not something derivable from the funnel data. Asserting one you were not given is
inference dressed as evidence, which `reference/intake.md` prohibits. If the documentation had not
been supplied, floor exclusion could not be confirmed and would stay tied with the other live Stage
1 causes. Name the missing input instead of inventing the behaviour.

### Evidence for this cause and against the alternatives

**The deficit is confined to the two channels that expose a salary floor filter.** The channel
without one performs inside its comparison range. That pattern is what separates floor exclusion
from a title, budget, or placement cause: all three of those would depress the boards *and* leave
the careers page alone, or would concentrate on one board rather than both.

The view rate is the second measure, and it points the same way. The subject converts impressions
to views at 3.8%, inside the comparison range of 3.2 to 5.1. **The deficit is volume, not
performance.** A post that is served and skipped shows a depressed conversion rate. This one is
converting normally on a quarter of the servings, which means it is not being served.

The magnitude also rules out presentation. A weak title or listing card depresses click-through on
impressions that still occur. It does not remove a post from the results grid.

### Alternatives, and why they are demoted

**Title mismatch.** Ruled out. Three of the five comparison requisitions carry titles in the same
family on the same channels and show baseline impressions.

**Sponsorship exhaustion, expiry, or de-ranking.** Ruled out. Spend was equal across the subject and
four of five comparison requisitions, the impression series is flat rather than a cliff, and both
boards show the post live and in-index for all 38 days.

**No range posted.** Not applicable. A range is posted.

**Channel absent from where the population looks.** Not supported. The channel mix matches the
comparison set, and the set filled from it.

**Requirement signaling.** Not supported at this stage, and untested. It remains live as a
secondary factor once visibility is resolved. Nineteen submissions is not a readable sample and no
conclusion is drawn from the two that passed.

**Prior change.** None. There is no completed experiment to read here, which is worth stating rather
than leaving as an absence.

### Null model

Rejected. Four of five comparison requisitions at comparable bands on the same channels drew 11,400
to 19,800 impressions per week over the same weeks, and three filled inside 31 days. The population
is being reached for adjacent roles at this company. It is not being reached for this one.

### Confidence

**Provisional.** The constraint is located cleanly and the mechanism is well supported, but the
reach baseline rests on four requisitions after the spend exclusion, and no channel supplied
search-appearance data that would confirm exclusion directly.

### Missing evidence

Search-appearance counts — how often the post was returned for the relevant queries — as distinct
from impressions, on both boards. Those would confirm the mechanism directly rather than by
inference from the channel split.

### What would prove this wrong

Search-appearance data showing the post is returned at comparison rates and simply not clicked.
That moves the diagnosis to the title or the listing card and inverts the conclusion.

---

## Case 3 — Null

**Input:** Senior clinical data manager, onsite, mid-size metro, band $118,000 to $132,000. 61 days
open, one band edit on day 34. Comparison set of six. The team is requesting the case for a band
increase.

### Failure observed

61 days open. Qualified submissions at 0.46 per week.

The comparison set's days open range from 44 to 74, median 58. Qualified submissions per week range
from 0.31 to 0.68. The subject sits inside both.

### Comparison set

Six requisitions at the same company, same window, same metro, all onsite, all regulated-industry
specialist roles at adjacent seniority, bands between $112,000 and $140,000, all on the same two
channels at equal spend. Days open across the six: 44, 52, 58, 67, 71, 74. Four of six remain open, two of them longer than the subject.

### Comparison-set integrity

**Usable.** Role family, seniority, band, location, work model, window, channel mix, spend, and
employer exposure all match. Requirement structure varies across the set. No single requisition
dominates: removing the fastest and slowest leaves a days-open range of 52 to 67 and does not change
the finding.

One structural limitation, named because it binds a conclusion below: **the set is matched on work
model.** All six are onsite. A comparison set cannot detect a cause it is matched on, so this set is
structurally unable to test whether the onsite requirement is itself the constraint.

### Funnel reconstruction

| Stage | Subject | Comparison range | Read |
|---|---|---|---|
| 1. Reach | 4,100 impressions per week | 3,200 to 5,400 | At baseline |
| 2. Consideration | 4.4% view rate, 12% apply-start rate | 3.9–5.2%, 10–15% | At baseline |
| 3. Application | 71% of apply-starts submitted | 64% to 78% | At baseline |
| 4. Screening pass | 4 of 29 submissions, 14% | 9% to 19% | At baseline |
| 5. Interview conversion | 3 of 4 scheduled, 3 attended | not supplied | Not assessable |

### Primary constraint

**None located.** The subject sits inside the comparison range at every stage of the funnel.

### Primary cause

**No post failure is demonstrated.**

### Mechanism

The addressable population at this specialty, band, work model, and metro is small, and every
requisition in the comparison set is drawing from it at the same rate. Pass rates across the set run
9% to 19% on submission volumes of 21 to 44 — a handful of qualified people per requisition, for
every requisition. The subject's 61 days sits inside a range of 44 to 74, three days above the
median, and four of six comparison requisitions remain open after comparable time. The post is
performing normally against a population that is genuinely thin, not against a market that is
rejecting it.

### Evidence for this cause and against the alternatives

A post with a real constraint fails at an identifiable stage. This one does not. It is served at
baseline, opened at baseline, completed at baseline, passes screening at baseline, and converts to
interviews at baseline — which means the people who exist are finding it, reading it, applying to
it, and talking to the company at the rate this market currently produces.

61 days is being read against an expectation rather than a baseline. The expectation is not stated
as a number anywhere in the request, and the comparison set is the only thing that can supply one.
It puts 61 days in the ordinary middle.

The composition of the pile also does not support the folk framing. Fourteen percent of submissions
clear the must-haves, inside a comparison range of 9 to 19 percent. The pile is small because the
pool is small, not because the wrong people are applying.

### Alternatives, and why they are demoted

**Compensation.** Not supported, and the day-34 band edit is **Uninformative** rather than evidence
in either direction. It moved the lower bound from $112,000 to $118,000. Both figures index between
the same two filter increments on both channels, so it crossed nothing. And it was edited in place
on the live postings rather than republished: neither channel re-notified or re-ranked, and the
impression series shows no change of shape at the edit date. It failed the condition that a change
must change the thing the hypothesis is about, and it was therefore never capable of testing a
compensation mechanism at any stage.

Reading the flat impressions afterward as proof that the market does not respond to money, or
reading the absent volume rise as proof the increase was too small, would both be over-readings of
an experiment that did not run.

**Requirement signaling.** Not supported. The screening pass rate sits inside the comparison range,
and the failures do not concentrate on any single stated requirement.

**Distribution.** Not supported. Impressions at baseline on the same channels the comparison
requisitions used, at equal spend.

**Process friction.** Not supported. Time to first contact is inside the comparison range and
withdrawals do not cluster by elapsed time.

**The onsite work model.** Named, live, and **not testable with this comparison set**. Every
requisition in the set is onsite, so the axis does not vary and the set is blind to it. It is not
ruled out; it has not been examined. A second set at the same specialty and band with a different
work model would test it in one line, and none was supplied. This is the reason the confidence
below is not higher.

### Null model

**Accepted. This is the diagnosis.** Every stage tracks the comparison set, qualified volume is low
across the entire set rather than uniquely low for the subject, and four of six comparison
requisitions remain open after comparable time.

### Confidence

**Provisional.** Six comparison requisitions, Usable integrity, and a clean stage-by-stage match —
but the thin-pool reading is inferred from the comparison set's own pattern rather than tested
against any measure of the addressable population, and the set is matched on work model, which
leaves one live alternative structurally undetectable.

### Missing evidence

A count of the addressable population: profiles matching the stated must-haves at this band,
specialty, and metro, which both channels can produce from their own indexes. That would confirm the
reading directly instead of by inference from six requisitions drawing from the same unmeasured
pool. **This is a count about this market, not an industry average — the folder does not use
industry averages and this is not one.**

Also: at least one comparison requisition at the same specialty and band with a different work
model.

### What would prove this wrong

An addressable-population count showing the pool is large. That would mean the comparison set is
drawing badly rather than drawing from a small pool, and the subject's normality would be an
artifact of a comparison group sharing its problem.

---

**Why this case is in the set.** 
The requested output was the case for a band increase. The evidence does not support one. No
constraint specific to this post was located, so an increase does not address anything the
diagnosis identified. What it does is reset the floor for every future hire at this level, in a
market where comparable requisitions at this company are also waiting.

Naming that is the diagnosis. What to do about a thin pool is the hiring team's conversation with
finance, and this folder does not have an opinion about it.
