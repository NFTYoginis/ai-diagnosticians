# Baselines

The comparison set is what turns an opinion into a diagnosis. This file covers how to build it
and how to decide what counts as underperformance.

There are no industry benchmark numbers here on purpose. Application rates, pass proportions,
time to fill, and normal impression volume vary enormously by role family, seniority, market,
work model, employer exposure, and season. Any figure quoted as an industry average would be
wrong in most searches and would be treated as authoritative anyway. **Every baseline in a
diagnosis is computed from that case's own comparison set.**

---

## Building the comparison set

Match on the axes that determine which population a requisition addresses:

- **Role family and seniority** — the people who would plausibly apply.
- **Compensation band** — overlapping, not identical.
- **Location and work model** — a remote requisition and an onsite one at the same band address
  different populations entirely, and treating them as comparable is the fastest way to
  manufacture a finding.
- **Window** — the same weeks. Hiring markets move on at least a quarterly clock, and a
  requisition open across a fiscal boundary spans two hiring climates.
- **Channel mix and sponsorship spend** — or the reach comparison means nothing.
- **Employer exposure** — the same company wherever possible. A household name and a seed-stage
  company do not draw comparably on the same channel with the same spend.

**Do not match on the post's wording, title convention, or requirement structure.** That is the
variable under test. This is the one axis where variation is required rather than tolerated: a
set assembled from requisitions that share the subject's requirement block cannot detect a
requirement problem, because the suspected cause is held constant across every member of the
set.

Four is the floor. Six to ten is a usable set. Below four, state that the range is not
established and cap confidence at Provisional.

### Where to get four

In order of preference:

1. **Other open requisitions at the same company**, same window, adjacent level. This is the
   strongest form, because employer exposure, channel access, brand, and process are all held
   constant.
2. **Closed requisitions at the same company** for the same role in the previous two cycles.
   Flag the window mismatch explicitly and treat the comparison as weakened — the market moved
   and you are now comparing across it.
3. **The same post run on a different channel.** A genuine within-case comparison, and valid at
   Stage 1 only. It tells you about distribution and nothing about the post.

---

## Establishing the range

Take **qualified submissions per week** and **days open** for every requisition in the set. You
need the spread, not the average.

The subject is underperforming when its qualified volume sits **at or below the bottom of the
comparison range**, not when it falls short of the mean. Half of all requisitions fall short of
the mean by definition, and treating the mean as a target manufactures failures that do not
exist.

Then check whether the range itself moved. If requisitions opened early in the window filled in
three weeks and requisitions opened late are still open, the market changed mid-requisition and
the null model is live before you look at anything else.

**Route out the pipelines that are not this post first.** Referrals, internal transfers, and
sourced candidates who never saw the advertisement inflate the numerator and do not distribute
evenly across a comparison set. A requisition that filled by referral tells you nothing about
its post.

---

## Per-stage baselines

Compute the comparison set's figures for each of the five canonical stages and compare:
**Reach, Consideration, Application, Screening pass, Interview conversion.**

**Reach.** Impressions per week by channel, normalized for time open **and for sponsorship
spend**. Comparing raw impression totals across requisitions with different spend is the most
common error in team-run comparisons — it is this domain's version of comparing view totals
across listings that have been live for different lengths of time. Where spend differs, compare
impressions per unit of spend on the sponsored channels and raw on the organic ones, and say in
the report which you did.

**Consideration.** Views as a proportion of impressions, and apply-starts as a proportion of
views. Absolute view counts are noisy and track spend rather than performance.

**Application.** Submissions as a proportion of apply-starts, and where in the form the drop-off
concentrates. Where apply-starts are not exposed by the applicant tracking system, this stage has
no comparative baseline and must be handled by structural elimination.

**Screening pass.** Submissions meeting the stated must-haves as a proportion of submissions,
**computed by channel as well as pooled**. The pooled figure gives you the level. The by-channel
spread is the discriminator, and without it the two live causes at this stage cannot be
separated. Ask for it explicitly; every applicant tracking system captures source.

**Interview conversion.** Screened-in to scheduled, scheduled to attended, and withdrawals
grouped by aggregate reason. Reasons are read as patterns about the post and the process, never
as evaluations of the people who withdrew.

---

## What the comparison set is, and is not

The comparison set is a natural comparison baseline. It is not an experimental control.

Matching on role family, band, location, work model, window, channel, and employer exposure
removes a great deal of confounding, which is why the method works at all. It does not hold
everything constant. Comparable requisitions still differ in team reputation, manager brand,
interview loop length, referral pipeline strength, visa sponsorship, the specific week they went
live, and how many competing employers were hiring the same profile that month.

Write conclusions accordingly. "The subject falls below its comparison baseline at Stage 4" is
supportable. "The only variable is the post" is not, and it is the phrasing that turns a good
baseline into a false proof.

### The set cannot detect a cause it is matched on

Matching is what makes a comparison work and it is also what makes a comparison blind. Every
axis you match on becomes invisible: if all six comparison requisitions are onsite, the set
cannot tell you anything about work model, because work model does not vary across it.

This bites hardest in this domain, because the axes you must match on to make the comparison
valid — band, location, work model — are also live hypotheses. Name the matched axis in the
report as a live alternative that this comparison set is structurally unable to test, and name
what would test it: usually a second set that varies on that axis and holds the rest. Do not
report it as ruled out. A variable held constant has not been examined.

---

## What counts as "materially below"

Judgment, stated explicitly in the report rather than applied silently.

- **Clearly below** — subject is under the lowest requisition in the set on that stage. Treat as
  a located break.
- **Ambiguous** — subject sits inside the comparison range but in the bottom quarter. Note it,
  do not treat it as the break unless a later stage is clearly below.
- **At baseline** — subject sits inside the comparison range. This stage is not the break. Move
  to the next stage.

**Insufficient volume is a fourth reading and not a synonym for any of the three.** A pass rate
computed on nineteen submissions is not a low pass rate; it is not a pass rate. Say so, and do
not let a handful of submissions become evidence about who the post attracts.

If no stage is clearly below, the requisition is performing at market and the null is likely the
answer. Do not manufacture a break by lowering the bar until one appears.

---

## The qualifying change test

The single most useful piece of history in any case file, and the easiest one to over-read.

A change made to the post, the channels, or the compensation during the requisition is a
completed experiment. But an experiment only tests what it was capable of testing, and most
hiring changes are not capable of testing most mechanisms.

### Step 1: does the change qualify

All four must hold before the result means anything.

| Condition | Why it matters | Fails when |
|---|---|---|
| **Changed the thing under test** | A change only tests the mechanism it acted on. Compensation acts at floors, comparison, and post-conversation value; channels act at reach; the form acts at completion; the requirement block acts at signaling | A raise offered as evidence about the requirement list. Or a raise made in place on a live post, which is invisible to everyone who already filtered past it |
| **Otherwise unchanged** | Simultaneous changes confound the result | A title change, requirement edit, new channel, sponsorship boost, or work-model change landed in the same window |
| **Sufficient window, sized to the application cycle** | Passive candidates respond on a slower clock than active ones | Two weeks of observation on a senior requisition. That measures the active pool and nothing else. Where sponsorship was involved, spend must be comparable on both sides |
| **Market held** | The comparison must survive | A sector layoff wave, competitor mass-hire, new-graduate cycle, seasonal turn, or holiday period fell inside the window |

If any condition fails, the change is **Uninformative**. Say which condition failed and do not
use the change as evidence in either direction. An experiment that did not run is not weak
evidence for the null. It is no evidence.

### Step 2: read a qualifying change

Compare the two weeks before against the four weeks after, or one full application cycle on each
side, whichever is longer. Stage by stage, on rates rather than counts.

- **A rate moved at a stage** — that mechanism was a real constraint. Which stage responded
  identifies it, and that is more valuable than the fact of the response. Record as **Positive**.
- **Impressions rose, pass rate did not** — the raise crossed a filter floor and solved a
  distribution problem, exposing a second constraint underneath it. **Two findings, not one**,
  and the second is the one that was holding the hire.
- **Nothing moved** — strong evidence against **the specific mechanism this change was capable
  of testing**. Name that mechanism explicitly. A raise that stayed under the same filter
  increment says nothing about floor exclusion, and a raise on a post that was never re-surfaced
  says nothing about anything. Record as **Negative**.

**Negative and Uninformative are different verdicts and must be labelled differently.** One means
the test ran and the hypothesis lost. The other means no test occurred. Teams read an
unresponsive raise as proof the market is impossible; that reading is available, and so is the
opposite, and which one is correct depends entirely on whether the raise could have tested the
break stage at all.

### The re-surfacing condition

Specific to this domain and routinely missed. Editing a compensation range on a live post does
not re-notify candidates who already filtered past it, and on most boards it does not re-rank the
listing. The money changed and the market never saw it. Before reading any compensation change,
establish whether the post was republished or re-surfaced. If it was not, the change is
Uninformative at Stage 1 regardless of its size.

---

## Seasonality and market moves

Before attributing a shortfall to the post, check whether the window contains a seasonal turn, a
new-graduate cycle, a fiscal-year freeze, a sector layoff event, or a competitor hiring wave that
affected the whole population. If the comparison set is matched on window, this is already
controlled for, which is why the window match matters more than most teams assume.

A requisition opened in a strong month and compared against requisitions opened in a weak one
will look artificially bad, and vice versa. When windows cannot be matched, say so and treat the
comparison as weakened.

Two patterns specific to this domain:

**A requisition open across a quarter boundary spans two climates.** Budget cycles move both
candidate supply and competitor demand, and pooling the funnel across the boundary averages them.

**A layoff event in the same sector inflates volume and depresses pass rate simultaneously.**
That combination is the exact fingerprint of requirement signaling, and it is not requirement
signaling. Check the window for one before naming Stage 4.
