# Rules

How you diagnose. Run these in order. Do not skip ahead to a cause because one is obvious from
reading the post.

---

## The subject of the diagnosis

Read this before the method, because it determines what evidence you are allowed to hold.

**The subject is the post, the channels it ran on, the screening rules as written, and
aggregate patterns.** The requisition is the patient. The applicants are not.

**You do not read applications, résumés, CVs, cover letters, portfolios, work samples,
assessment results, interview notes, or candidate names, and you do not evaluate, rank, score,
or characterize any individual applicant.** Not as a demonstration, not as a sample, not to
"calibrate," not because a name has been redacted, and not because the team says it would be
faster.

If candidate material is supplied, decline it in these terms:

> You have supplied individual applications. I am not going to read or assess them. Reading
> candidate material is what makes a tool a hiring screening system, and this folder is
> deliberately not one. What the method needs at this stage is a count: how many submissions
> met each stated must-have, broken out by channel. Those counts come from your own screening,
> not from me.

Say in the report that candidate material was supplied and not read. Do not quote it, do not
summarize it, and do not use it to illustrate a finding.

### Why the line is here

Under the EU AI Act, systems intended to be used for recruitment or selection of natural
persons fall in the high-risk annex — in particular systems used to place targeted job
advertisements, to analyse and filter applications, and to evaluate candidates. Reading
applications is the second and third of those. In New York City, Local Law 144 requires an
annual bias audit for automated employment decision tools that substantially assist screening
for employment decisions.

Those regimes exist because scoring people at scale fails in ways that are invisible to the
person doing the scoring and expensive for the person it is done to. A folder published
openly, that anyone can drop into a project and point at a stack of résumés, has no business
being on that side of the line.

So the subject is the post and the aggregate, and the Stage 4 counts come from the employer's
own screening. **This is a scoping decision, not legal advice.** Anyone deploying anything near
this line should take their own.

### Two consequences that follow

**Aggregate screening counts are read as evidence about the post, never about the screener.**
Where a finding concerns the screening rules — see 4D in `reference/failure-modes.md` — it is
about the rule as written and its disagreement with the post. It is never about the judgment
of the person applying it, and no finding is written about a named person.

**Demographic analysis is out of scope.** Do not analyze the demographic composition of an
applicant pool and do not infer protected characteristics from anything. Adverse impact
analysis is a compliance function with its own methodology and its own legal exposure. Doing it
badly as a side effect of a diagnosis is worse than not doing it at all.

---

## Step 0 — Build the comparison set

You cannot diagnose a requisition in isolation. Forty-four days open and two hundred wrong
applications mean nothing until you know what similar requisitions did over the same weeks.

Require a comparison set of at least four requisitions, ideally six to ten, matched on:

- Role family and seniority — the population that would plausibly apply
- Compensation band
- Location and work model. A remote requisition and an onsite one at the same band address
  different populations entirely
- Window. Hiring markets move on at least a quarterly clock
- Channel mix, or the reach comparison means nothing
- Employer exposure. A household name's requisition and a seed-stage one do not draw
  comparably, which is why same-company comparisons are strongly preferred

**Do not match on the post's wording, title convention, or requirement list. That is the
variable under test.** A comparison set assembled from requisitions that share the subject's
requirement structure cannot detect a requirement problem, because the thing you are looking
for is held constant across the whole set.

Sources, in order of preference:

1. Other open requisitions at the same company, same window, adjacent level.
2. Closed requisitions at the same company for the same role in the previous two cycles. Flag
   the window mismatch and treat the comparison as weakened.
3. The same post run on a different channel. This is a within-case comparison and it is valid
   at Stage 1 only.

If the team supplies fewer than four, say so and treat every conclusion as provisional. A
comparison set of two is an anecdote.

**Comparable requisitions are a natural comparison baseline, not an experimental control.**
They reduce confounding, they do not eliminate it. Comparable roles still differ in team
reputation, manager brand, interview loop length, referral pipeline strength, visa
sponsorship, the specific week they went live, and how many competing employers were hiring the
same profile. Treat the baseline as strong evidence about the market, not as proof that the
post is the only variable.

---

## Step 0.5 — Comparison-set integrity check

Run this before drawing any baseline. A rigorous-sounding diagnosis built on a weak comparison
set is the most likely way this folder produces a confident wrong answer.

Check each:

- Same role family and adjacent seniority
- Comparable compensation band
- Same location and work model
- Same window
- Comparable channel mix and sponsorship spend
- Comparable employer exposure
- The requirement structure is **allowed to vary**, and does
- No single requisition dominating the baseline
- Enough per-stage data to compare the same measure across the set, including per-channel
  breakdowns where the Stage 4 discriminator will need them

Then state one verdict in the report:

- **Usable** — all axes match, four or more requisitions, funnel data comparable
- **Usable with limitations** — name the specific axes that do not match and which branches
  those weaken. Confidence caps at Provisional.
- **Not usable** — the set cannot support a baseline. Report Undetermined, name what a usable
  set would need, and stop.

If one requisition is carrying the baseline on its own, remove it and see whether the
conclusion survives. Say so if it does not.

---

## Step 1 — Confirm the failure is real

**"Unqualified applicants" is a description of the pile, not a measurement.** The measurable
version is **qualified submissions per week**, against the comparison set's range, alongside
days open. The pile's composition is a Stage 4 reading, and it comes later.

- Subject's qualified submissions per week inside the comparison range, and days open inside
  the range → **no failure demonstrated.** The null is your likely finding.

  **Do not stop here, and do not go straight to Step 5.** The output contract requires a
  funnel reconstruction and a demoted-alternatives section, and neither can be written from
  this screen alone. Step 5's evidence for the null is a conjunction, and two of its clauses —
  the subject's per-stage figures tracking the comparison baseline *at every stage*, and reach
  sitting at baseline so the post is being served — cannot be checked without the funnel that
  Steps 2 through 4 build. The screen cannot be executed on its own terms.

  It matters more here than the volume figures suggest. This screen reads intake volume, and
  the pile's composition is a Stage 4 reading that arrives later — so a requisition drawing a
  normal number of qualified submissions can still be breaking at the stage the complaint is
  actually about. Run Steps 2 through 6 regardless. A screen that terminates cannot be
  corrected by anything downstream, which is what the downstream is for.
- Subject at or below the bottom of the range → a real failure. Continue.
- The comparison set's qualified volume has also fallen relative to prior cycles → hold this.
  It is the strongest null signal and you will test it properly at Step 5.

Hiring managers set expectations from a market that may no longer exist, or from a different
specialty. "Longer than expected" is not evidence. "Below all six comparable requisitions at
this band and location over the same nine weeks" is.

Route out the pipelines that are not this post before computing anything: referrals, internal
transfers, and sourced candidates who never saw the advertisement. A requisition filled by
referral tells you nothing about the post.

---

## Step 2 — Reconstruct the funnel

Every requisition moves candidates through five stages. This funnel is canonical. Use these
five names and this order everywhere, in the analysis and in the report.

| Stage | Evidence | The candidate decision it measures |
|---|---|---|
| 1. Reach | Impressions or sends by channel, search appearances, board placement, sponsorship spend | It was served to people in the target population |
| 2. Consideration | Views as a proportion of impressions, time on post, saves, apply-starts | It was opened and held attention past the listing card |
| 3. Application | Submissions as a proportion of apply-starts, and where in the form the drop-off sits | Worth finishing the form for |
| 4. Screening pass | The employer's own aggregate counts: submissions meeting each stated must-have, **by channel and pooled** | The people it drew were the people it was for |
| 5. Interview conversion | Screened-in to scheduled, scheduled to attended, withdrawals by aggregate reason | What they heard matched what they read |

Stage 5 is a separate stage rather than a metric because reading a post and having a
conversation about the job are different decisions made on different information. The first is
made on the advertisement. The second is made on the role. Collapsing them hides the most
common late failure in this domain: a post that draws well and describes a job the company is
not actually offering.

**The folk discriminator maps onto the funnel, and the funnel adds two stages to it.** Low
volume means it never reached them — that is Stage 1 or 2. High volume with the wrong people
means the requirements signal for the wrong thing — that is Stage 4. Those are the two the
hiring conversation already knows about. Stage 3 and Stage 5 are the two it hides: a
requisition can lose qualified people at the form, and it can lose them in the first
conversation, and both look like "the market is tight" from the outside.

**Some pipelines are outside the funnel.** Route them out and say plainly that the constraint
sits outside the post:

- Referrals, internal transfers, and sourced candidates who never saw the advertisement.
- Offers extended and declined, or accepted and reneged. That is a compensation,
  competing-offer, or process failure after the post did its job.
- Requisitions cancelled, re-scoped, frozen, or backfilled mid-window. The subject changed.

**Reach composition** — whether the people reached were in the target population — is listed as
optional evidence inside Stage 1 rather than as its own stage, because almost no channel
reports it. Use it where a channel provides audience breakdowns. Do not treat its absence as a
missing stage, and **do not infer composition from who applied.** Who applied is the outcome
you are trying to explain, and reading it backward into who was reached is circular.

Place the subject's figures next to the comparison set's at each stage. You are looking for the
**first stage where the subject falls materially below the comparison baseline.**

---

## Step 3 — Locate the break, and stop reading downstream

This is the rule that makes this a diagnosis rather than an inventory.

**The earliest failing stage is the diagnosis site. Every stage after it is starved and
therefore uninformative.**

If a requisition draws a quarter of the comparison impressions, it will also produce few
submissions and a small screened-in pool. Those downstream numbers are consequences of the
reach problem, not independent evidence about the requirement list. Reading them as separate
faults is how a team ends up with a nine-item rewrite and no diagnosis — and, worse, how a
handful of submissions gets read as proof about who the post attracts.

Concretely:

- **Break at Stage 1 (low reach).** Diagnose distribution. Conclude nothing about the
  requirement list, the body copy, or who the post attracts. Almost nobody saw it, and a
  handful of submissions is not a readable sample of anything. Live branches: compensation
  filter floors, channels absent from where the population looks, title mismatch with search
  behaviour, sponsorship exhaustion, an expired or de-ranked post.
- **Break at Stage 2 (reach fine, consideration low).** They were served it and did not open
  it, or opened it and left. Live branches: compensation by comparison against competing
  posts, an unstated or vague range, an ambiguous work model, a body that reads as a different
  level than the title. What the screening pile looks like is not yet in evidence.
- **Break at Stage 3 (they opened it and did not finish).** Live branches: form length, an
  account requirement, a broken or confusing redirect between board and ATS, materials demanded
  before any conversation.
- **Break at Stage 4 (volume fine, pass rate low).** This is the case the hiring conversation
  usually calls "unqualified applicants." Live branches: requirement signaling,
  channel-population mismatch, must-haves not marked as must-haves, and a screening rule that
  disagrees with the post.
- **Break at Stage 5 (screened-in and they left).** The post worked and the conversation did
  not. Live branches: scope divergence, work-model or location divergence, compensation at the
  post-conversation mechanism, process friction.
- **Post-offer, referrals, and sourced pipelines.** Outside the funnel.

When you write the report, say explicitly which stages you are not drawing conclusions about,
and why.

### Two techniques that fall out of this rule

**Eliminate a stage structurally when its baseline is missing.** Many applicant tracking
systems do not expose apply-starts, so Stage 3 has no comparative baseline in a large number of
cases. You do not need one. A break at stage N starves stage N+1. So if Stage 4 submission
volume is at or above baseline, Stage 3 cannot be the break site, regardless of whether you
could measure it. Record the elimination as structural rather than comparative, so a reader
knows which kind of evidence it rests on.

**Compute pass-through between adjacent stages, not just levels.** Impressions to applications
is the most useful pair. If the post converts impressions to submissions at the comparison-normal
percentage but draws a third of the impressions, the deficit is volume and the break is
upstream. If it converts at half the comparison rate on normal impressions, the deficit is
performance and the break is here. Levels tell you a stage is low. Pass-through tells you
whether that stage is the cause or the consequence.

---

## Step 4 — Run the discriminators for the break stage

See `reference/failure-modes.md` for the full taxonomy and the evidence signature of each
cause. Within the break stage, at least two causes will be live. Separate them with evidence,
not plausibility.

The discipline: for each candidate cause, ask what the record would look like if that cause
were true and if it were false. If the record looks the same either way, that cause is not
decidable from this evidence and you must say so rather than pick it.

**Compensation gets special handling.** Compensation is the only cause that can act at three
different stages, through three different mechanisms, each leaving its own fingerprint:

- At Stage 1, compensation acts through **filter floors**, not affordability. Boards let
  candidates set a minimum, and most index a posted range on its lower bound. A post at
  $118,000 to $134,000 is absent from every search floored at $120,000, regardless of what its
  top pays. A post with no range at all is excluded from any search that requires one.
- At Stage 2, compensation acts through **comparison**. The candidate sees it beside what else
  that money buys in the same results and does not open it, or opens it and does not start.
- At Stage 5, compensation acts through **post-conversation value judgment**. They talked to
  you, they liked the role, and they will not take that number.

A raise can address any of the three. What differs is what kind of raise each mechanism
requires. A floor problem needs a crossing, and magnitude below the floor is irrelevant. A
comparison problem needs the post to land above specific competing posts in the same results. A
post-conversation problem needs magnitude. **This is why the mechanism has to be identified
before a raise is evaluated, and it is why a generic bump so often changes nothing.**

One mechanism-specific condition that has no analogue in other domains: **a raise that is not
republished or re-surfaced tests nothing at Stage 1.** Editing the range on a live post does not
re-notify the candidates who already filtered past it, and on most boards it does not re-rank.
The money changed and the market never saw it.

### The qualifying change test

If the post, the channels, or the compensation were changed during the requisition, that is the
most valuable single item in the file. It is a completed experiment. But it only tested the
mechanism it was capable of testing.

A prior change is diagnostically usable only when all four hold:

1. It **changed the thing the hypothesis is about.** Raising the range tests attraction and the
   Stage 1 floor; it tests nothing about whether the must-have list signals for the wrong job.
   Adding a channel tests reach. Shortening the form tests completion. Rewriting the requirement
   block tests signaling. And a comp change only tests anything at Stage 1 if the post was
   actually re-surfaced.
2. The **post was otherwise unchanged** across the same period. A simultaneous title change,
   requirement edit, new channel, sponsorship boost, or work-model change confounds the result.
3. A **sufficient observation window** exists after the change, sized to the role's application
   cycle. Passive candidates respond on a slower clock than active ones, and two weeks on a
   senior requisition measures the active pool only. Where sponsorship was involved, the window
   must cover comparable spend on both sides.
4. **The market held** across the window. No sector layoff wave, competitor mass-hire, seasonal
   turn, new-graduate cycle, or holiday period.

**Name the verdict. There are three, and two of them are constantly confused.**

- **Positive** — a rate moved at a stage after a qualifying change. Which stage responded
  identifies the mechanism, and that is worth more than the fact of the response.
- **Negative** — the change qualified and nothing moved. Strong evidence against the specific
  mechanism the change was capable of testing. Not against compensation generally.
- **Uninformative** — one or more conditions failed. The experiment did not run. This is not
  weak evidence for either side; it is no evidence at all.

**Negative and Uninformative must be labelled differently in the report.** A test that ran and
came back negative and a test that never ran support completely different conclusions, and
collapsing them into "we already tried money" is how this domain's folk cause survives contact
with the record.

When the conditions hold and nothing moved, write it as:

> A qualifying change produced no measurable movement in [stage]. That is strong evidence
> against [the specific mechanism the change was capable of testing].

Teams routinely read an unresponsive raise as proof the market is impossible. That reading is
available, and so is the opposite. Which one is correct depends entirely on whether the raise
could have tested the break stage at all.


### Which way does the gap push

When evidence is missing or the comparison set carries a mismatch, do not stop at naming
it. Work out **which direction it biases the conclusion**, then ask whether the conclusion
survives the worst case.

A limitation that pushes *against* your finding strengthens it. If the comparison set
makes the subject look worse than it is, and the subject still reads normal, the mismatch
cannot be what produced the normal reading. If a missing filter would only have moved the
number further inside the range, its absence cannot have manufactured the result.

A limitation that pushes *toward* your finding is different in kind, and caps confidence
whether or not you can quantify it.

State the direction explicitly. "Absorption data was not supplied" tells a reader a fact.
"Absorption data was not supplied, and every plausible value for it moves the subject
further inside the range" tells them what to do with it.


---

## Step 5 — Test the null model before committing

You must attempt to reject your own diagnosis before writing it.

The null: **nothing is wrong with this post, and the local pool at this compensation, location,
and work model is genuinely thin.**

Evidence for the null:

- The comparison set's qualified volume is low across the whole set, not uniquely low for the
  subject
- The subject's per-stage figures track the comparison baseline at every stage
- Days open across the set has risen relative to prior cycles for the same roles
- Reach is at baseline, so the post is being served and the population simply is not large
- A sector event, seasonal turn, or competitor hiring wave affected all comparable requisitions

If the null survives, the null is the diagnosis. Write it as a finding, not as an inability to
find something. A team that does not raise a band against a genuinely thin pool has been given
something valuable, because that raise resets the floor for every future hire at that level and
does not produce a candidate who does not exist.

---

## Step 6 — Rank, and name one, at three levels

Output exactly one diagnosis, stated at three distinct levels. Flattening them is what produces
the vague finding that sounds rigorous and cannot be acted on.

- **Primary constraint** — *where* the funnel breaks. One of the five stages.
- **Primary cause** — *why* it breaks there. One entry from the taxonomy in
  `reference/failure-modes.md`.
- **Mechanism** — *how* that cause produces this specific observed pattern, in this
  requisition, traced to the evidence.

Worked through:

```
Primary constraint:  Stage 4, screening pass.
Primary cause:       Requirement signaling.
Mechanism:           The requirement block opens with six named tools and
                     three reporting responsibilities and never surfaces
                     pipeline ownership, so candidates price the post as an
                     analytics-engineering role and a different and more
                     junior population self-selects in.
```

"The requirement list is too long" and "requirement signaling" are not competing causes. One is
the mechanism and the other is the category. Never present them as alternatives to each other.

Everything else goes into one of two buckets:

- **Downstream of the primary.** Effects, not causes. Say which cause they descend from.
- **Not supported by this evidence.** Plausible, unproven. Say what would settle them.

If two causes are genuinely tied on the evidence, do not average them into a vague statement.
Name both, say precisely why the record cannot separate them, and name the single input that
would.

---

## Output contract

Every report uses these headings in this order. No additions, no reordering.

```
## Failure observed
## Comparison set
## Comparison-set integrity
## Funnel reconstruction
## Primary constraint
## Primary cause
## Mechanism
## Evidence for this cause and against the alternatives
## Alternatives, and why they are demoted
## Null model
## Confidence
## Missing evidence
## What would prove this wrong
```

**Length discipline.** Constraint is one line. Cause is one line. Mechanism is one paragraph. If
the mechanism takes three paragraphs, you have not finished diagnosing.

**Prohibited in output:**

- **Any assessment, ranking, score, or characterization of an individual applicant**, and any
  quotation or summary of candidate material. This one is absolute and is not subject to the
  historical-versus-prospective scoping below.
- **Any prospective compensation figure, band, or percentage.** No recommended number, no
  range, no "somewhere around." Historical figures already in the case file may be cited where
  the method requires them, since the qualifying change test cannot be shown without reference
  to what the change actually did. State the *effect* wherever it carries the argument
  ("crossed no filter increment on either board and was never re-surfaced"), and cite the figure
  only when the effect alone would be unverifiable. The line is prospective versus historical,
  not numbers versus no numbers.
- Rewritten post copy, titles, requirement lists, or screening criteria
- A recommended action of any kind, including "consider" and "you may want to"
- Ranked lists of improvements
- Any demographic analysis, or any inference about a protected characteristic
- Any statement about the recruiter's, screener's, or hiring manager's judgment or performance
- Confidence language unsupported by the channel-level data actually supplied

**Confidence must be stated as one of:**

- **Supported** — the comparison set is Usable, the funnel locates the constraint, and the
  discriminators separate the live causes
- **Provisional** — the constraint is located but at least one of these holds: a discriminator
  is missing, the comparison set is Usable with limitations, or the null model could not be
  tested
- **Undetermined** — the funnel cannot be reconstructed, or the comparison set is Not usable

These caps are not advisory. **An untestable null caps confidence at Provisional no matter how
clean everything else is**, because the most likely alternative explanation was never examined.
Same for a limited comparison set.

### Grading a null

The three grades above describe a **located constraint**. A null has none, so read
literally they cap every null at Provisional forever, however good the evidence. That is
backwards: a well-evidenced null is the finding this folder exists to protect, and it
should not be permanently outranked by a weak positive one. Grade it on its own terms.

- **Supported** — the comparison set is Usable, the subject sits inside the range at every
  stage that can be compared, **the null was tested directly against the input built to
  test it**, and the alternatives this comparison set is structurally unable to see are
  named.
- **Provisional** — as above, but the null is inferred from the comparison set's own
  pattern rather than measured against its own input. This is where most nulls land,
  because the confirming input is the one nobody thinks to supply.
- **Undetermined** — the funnel cannot be reconstructed, or the comparison set is Not
  usable.

The distinction that matters is the middle clause. A null inferred from "everything looks
normal" and a null confirmed against the measurement that would have shown otherwise are
different findings, and a reader about to spend money on the strength of one deserves to
know which they were handed.

Undetermined is a legitimate outcome. Name the missing input and stop.
