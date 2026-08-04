# Examples

Three worked cases. They show the reasoning, not just the conclusion.

The cases are constructed for teaching, with figures chosen to make each discriminator
legible. They are not customer files. The third one produces no defect, which is the outcome
most documentation audits cannot reach and the one that saves the most time.

Between them they also show the three possible verdicts on a prior documentation change: one
qualifying change that returned a negative result, one case with no change to read, and one
non-qualifying change that is treated as no evidence at all.

---

## Case 1 — Break at Stage 5

**Input:** Scheduled CSV export in a B2B analytics product. Eight-week window, 61 tickets,
1,240 active users of the feature. Comparison set of seven documented topics in the same
product over the same weeks. Full threads, search logs, pageviews, release notes, and an
article rewrite on day 22.

### Failure observed

61 tickets against 1,240 active users is 4.9 per hundred over the window. The comparison set
ranges 0.65 to 1.24 per hundred. The subject sits at roughly four times the highest topic in
the set. Failure confirmed.

Nine contacts were routed out before this figure was computed: four feature requests for
export formats the product does not offer, three billing questions attached to an export
ticket, and two contacts from accounts with a named contact who ask by policy rather than
after a self-service attempt.

### Comparison set

Seven documented topics, same product, same eight weeks, each with an active-user denominator:
saved views, team invitations, dashboard sharing, alert rules, data source connection, API
keys, billing contacts. All mature adoption, all with articles over a year old.

### Comparison-set integrity

**Usable.** Product, window, documentation maturity, and denominator availability match across
all seven. Thread-derived figures for Stages 3 through 5 were computed on full threads for the
subject and for all seven comparison topics, so the per-stage comparison rests on the same
measure throughout.

One limitation, named and handled: billing contacts sits in a different consequence tier,
because users escalate faster when money is involved. It is retained for the rate range and
excluded from the per-stage thread baselines. Removing it leaves the rate range at 0.65 to
1.23 and does not change the finding. No single topic is carrying the baseline.

### Funnel reconstruction

| Stage | Subject | Comparison range | Read |
|---|---|---|---|
| 1. Reach | 38 pageviews per 100 active users | 21 to 44 | At baseline |
| 2. Retrieval | 81% of topic queries opened the article | 62% to 88% | At baseline |
| 3. Comprehension | 84% of threads quote or paraphrase the article accurately | 55% to 79% | At baseline, in fact above it |
| 4. Execution | 92% of threads describe an action taken | 60% to 85% | At baseline |
| 5. Resolution | 9% of attempts produced the documented outcome | 71% to 94% | **Clearly below** |

### Primary constraint

**Stage 5, resolution.** The topic performed at or above baseline through execution. Users
found the article, opened it, understood it, and carried out the procedure at a normal rate.
Nine percent of attempts produced what the article says they will produce, against a
comparison range of 71 to 94 percent.

Stages 1 through 4 are not the diagnosis site, and no conclusion is drawn about the article's
findability, its title, its vocabulary on the page, or the clarity of its steps. Those
demonstrably worked.

### Primary cause

**Undocumented branch condition.** The article documents one path through a procedure the
product branches on.

### Mechanism

Step 4 of the article says the scheduled export will deliver to the connected storage
destination. Since a release on day 6 of the window, a workspace with more than one connected
destination requires the schedule to name which one, and a schedule saved without naming one
is created successfully and delivers nothing. No error is surfaced. The article describes the
single-destination case and does not mention the selector. Readers follow the procedure
exactly, get silence, and write in from that point — which is why their threads read as
confusion about the export and resolve as a report of an absent file.

### Evidence for this cause and against the alternatives

The sorting is the discriminating evidence. Threads reporting a delivered file and threads
reporting nothing split cleanly on whether the workspace has one connected destination or more
than one: 4 of 47 multi-destination threads report delivery, against 9 of 11 single-destination
threads. Confusion does not respect a threshold. A cause that produces success on one side of
a configuration line and failure on the other is doing something no comprehension failure can
do.

The threads themselves point past comprehension in the same direction. 84% quote or paraphrase
the article accurately, and most quote step 4 specifically before describing what they did.
These users read it and did what it said.

Article and release dates place the divergence: the article's last substantive edit predates
the day-6 release, and the release notes describe the destination selector as intended
behavior for ambiguous configurations.

### Alternatives, and why they are demoted

**Comprehension.** Not supported, and the day-22 rewrite is readable here. The rewrite
shortened the sentences, numbered the steps, and added a screenshot. It changed the clarity of
the page and nothing else: no product release, no navigation change, no re-index, and no macro
change landed in the same window. Thirty-eight days of observation follow it, against a task
users perform weekly, so multiple attempt cycles are covered. Active users were flat at 1,190
before and 1,240 after. **That is a qualifying change, and it tested comprehension.**

It worked. Accurate quotation of the article rose from 71% to 84%. The ticket rate did not
move at all. **Positive at Stage 3, and no movement in the outcome** — which is two findings
rather than one. The rewrite improved a stage that was never the constraint, and the fact that
it improved measurably and changed nothing downstream is strong evidence against comprehension
as the cause here.

**Discoverability.** Not supported. Reach and retrieval both sit at baseline. Readers are
finding the page.

**"Users do not read."** Not supported and directly contradicted by the record. 84% of threads
quote the article, most of them at step 4, and 92% describe an action taken. The evidence is
that they read it and followed it.

**A product defect, outside the funnel.** Considered and rejected. The behavior is intended:
the release notes describe requiring a destination selection for ambiguous configurations as
the design. The product is doing what it was built to do and the article describes something
else, which places this inside the funnel as divergence rather than outside it as a defect.
The record that decides this is the product's stated intent, not the users' expectation.

### Null model

Rejected. Active users were flat across the window, 1,190 to 1,240, while tickets on the topic
rose from 3 in week one to 14 in week eight. The comparison set's rates held steady across the
same weeks. Adoption did not move and the rate did.

### Confidence

**Supported.** Comparison set is Usable, the constraint is located by both level and
pass-through, the configuration split separates the live branches, and the null was tested and
rejected.

### Missing evidence

Product telemetry for schedule creation with and without a named destination was not supplied.
It would confirm the branch condition directly rather than by inference from how the threads
sort. No locale breakdown was available, so a coverage contribution cannot be ruled out,
though reach at baseline makes it unlikely.

### What would prove this wrong

Threads from multi-destination workspaces reporting the export delivering correctly, at any
volume. That breaks the sorting variable and moves the diagnosis back toward comprehension. So
would a record showing the destination selector was not intended behavior, which would move
this outside the funnel entirely and make it a defect.

---

## Case 2 — Break at Stage 2

**Input:** Transferring a project to another workspace. Six-week window, 34 tickets, 610
active users of the feature. Comparison set of seven. Full threads and help-center search logs.

### Failure observed

34 tickets against 610 active users is 5.6 per hundred. The comparison set ranges 0.7 to 1.9.
Beyond the range. Confirmed.

### Comparison set

Seven documented topics, same product, same six weeks, denominators available for all.

### Comparison-set integrity

**Usable with limitations.** Six of seven match on product, denominator, maturity, window, and
consequence tier. The seventh, billing contacts, sits in a different consequence tier and is
retained for the rate range and excluded from per-stage baselines.

The binding limitation is elsewhere: help-center search logs exist for only five of the seven
topics, so the Stage 2 retrieval baseline is drawn from five rather than seven. The Stage 2
finding depends on that baseline. Confidence caps at Provisional.

### Funnel reconstruction

| Stage | Subject | Comparison range | Read |
|---|---|---|---|
| 1. Reach | 44 help-center sessions per 100 active users | 26 to 51 | At baseline |
| 2. Retrieval | 12% of topic queries opened the article | 58% to 86% (five topics) | **Clearly below** |
| 3. Comprehension | 4 of 34 threads reference the article | insufficient volume | Not assessable |
| 4. Execution | — | — | Starved |
| 5. Resolution | — | — | Starved |

### Primary constraint

**Stage 2, retrieval.** They came looking. 44 help-center sessions per hundred active users
sits squarely inside the comparison range, so the documentation surface was reached at a normal
rate. Twelve percent of queries on this topic ended with the article opening, against a
comparison range of 58 to 86 percent.

Nothing is concluded about whether the article's instructions are clear, complete, or correct.
Four of 34 threads show any contact with it, which is not a readable sample, and no meaningful
number of users reached the procedure.

### Primary cause

**Vocabulary mismatch in the index.**

### Mechanism

The article is titled "Moving projects between workspaces" and uses *move* and *workspace*
throughout. The product's own control is labelled **Transfer**, and has been since a rename the
article predates. Search logs show 211 queries on the topic in the window, distributed across
"transfer project," "change project owner," "move to another account," and "reassign project."
Twenty-six of those opened the article. Users are typing the word on the button in front of
them, and the index is holding the word the article was written with. The page is not hard to
find because it is buried. It is hard to find because it is filed under a name the product no
longer uses.

### Evidence for this cause and against the alternatives

Reach at baseline is what makes this a retrieval finding rather than a reach finding. These
users opened the help center at a normal rate. The failure is between arriving and landing.

The article returns at position one for its own exact title and for "move project between
workspaces," which rules out an indexing defect. The index works. It is the words.

The query distribution is the direct evidence. The four highest-volume phrasings in the window
share no content word with the article's title, and the two phrasings that do share one both
returned and opened it.

Comparison topics that perform well share vocabulary with the queries that reach them: the
five with search logs all carry the product's current control name in their titles.

### Alternatives, and why they are demoted

**No in-product entry point.** Ruled out by reach at baseline. They came looking and arrived.

**Search or indexing defect.** Ruled out. The article returns for its own title and for a
close paraphrase, both at position one.

**Near-duplicate articles splitting the click.** Not supported. One article covers the topic.

**Comprehension.** Not supported at this stage, and untested. Only 4 of 34 threads show any
article contact.

**Naming drift at Stage 5.** Live in principle and not in evidence. The same stale noun that
breaks retrieval here would also be live inside the procedure if readers reached it, since the
article's step 3 names a control the product has renamed. Whether it also breaks there is
starved and is not concluded.

**Prior documentation change.** None in the window. There is no completed experiment to read
here, which is worth stating rather than leaving as an absence.

### Null model

Rejected. Active users were flat across the window, 598 to 610, while tickets rose. The
comparison set's rates held steady over the same six weeks. Nothing product-wide moved.

### Confidence

**Provisional.** The constraint is located cleanly and the mechanism is well supported, but the
retrieval baseline rests on five of seven comparison topics, and that is the baseline the
finding depends on.

### Missing evidence

In-product search logs, which would show whether users are typing the question into the product
before ever reaching the help center. Search-log coverage for the two comparison topics that
lack it, which would firm up the baseline the finding rests on.

### What would prove this wrong

Search logs showing the article is returned and opened at comparison rates for the phrasings
users actually type. That moves the diagnosis to comprehension and inverts the conclusion.

---

## Case 3 — Null

**Input:** Bulk import. Ten-week window, 147 tickets against 43 the prior quarter, a 240% rise.
Comparison set of eight. The team is requesting a diagnosis of where the article is failing.

### Failure observed

147 tickets over ten weeks, up from 43 in the prior quarter. Active users of the feature over
the window: 3,900, up from 1,150. The feature left beta at week two and reached all plans by
week six.

The rate is 3.8 tickets per hundred active users, against 3.7 in the prior quarter and a
comparison range of 2.9 to 4.6. Inside the range, and inside its own history.

### Comparison set

Eight documented topics, same product, same ten weeks, matched on complexity and consequence
tier: migrations, integrations, and bulk operations. Denominators available for all eight.

### Comparison-set integrity

**Usable.** All eight match on product, window, maturity, denominator, segment mix, and
complexity tier. No single topic dominates: removing the highest and lowest leaves a range of
3.1 to 4.4 and does not change the finding.

The set's rates sit well above this product's overall average because it is matched on
complexity tier. That matching is what makes the comparison valid. A set drawn from the
product's easy topics would place this one far outside a range it has no business being
compared against, which is the most common way a false positive is manufactured in this domain.

### Funnel reconstruction

| Stage | Subject | Comparison range | Read |
|---|---|---|---|
| 1. Reach | 51 pageviews per 100 active users | 38 to 62 | At baseline |
| 2. Retrieval | 74% of topic queries opened the article | 61% to 85% | At baseline |
| 3. Comprehension | 62% of threads quote or paraphrase accurately | 48% to 71% | At baseline |
| 4. Execution | 77% of threads describe an action taken | 66% to 84% | At baseline |
| 5. Resolution | 81% of attempts produced the documented outcome | 70% to 88% | At baseline |

### Primary constraint

**None located.** The subject sits inside the comparison range at every stage of the funnel.

### Primary cause

**No documentation failure is demonstrated.**

### Mechanism

The eligible population more than tripled inside the window. The feature left beta at week two
and completed its rollout by week six, taking active users from 1,150 to 3,900. Tickets rose
by a similar multiple and the rate did not move: 3.7 per hundred in the prior quarter, 3.8 in
this one, against a comparison range of 2.9 to 4.6. Every user who meets a bulk import feature
meets it for the first time, and a rollout delivers all of those first times at once. The
article is producing the contact rate it has always produced, for more people.

### Evidence for this cause and against the alternatives

Documentation with a real constraint fails at an identifiable stage. This does not. It is
reached at baseline, retrieved at baseline, understood at baseline, acted on at baseline, and
resolves at baseline — which means users are finding it, opening it, following it, and getting
what it promises at the rate this product currently produces on tasks of this weight.

The 240% figure in the request is a count, and the denominator under it moved by a comparable
multiple. A count without its denominator is the specific false alarm this method exists to
catch, and it is the whole of the case being made.

### Alternatives, and why they are demoted

**Comprehension, and the claim that the article is failing.** Not supported. Comprehension sits
at baseline and no stage is below range. The day-31 addition of a "Common errors" section is
**Uninformative** rather than evidence in either direction: the same week it shipped, the
rollout moved from 40% of accounts to all of them, so the eligible population more than doubled
inside the observation window and only window-total denominators are available. It failed the
otherwise-unchanged and steady-adoption conditions and was therefore never capable of testing
anything. Reading the raw rise afterward as proof the section failed, or as proof it made
things worse, would both be over-readings of an experiment that did not run.

**Discoverability.** Not supported. Reach and retrieval both at baseline.

**Product-documentation divergence.** Not supported. Resolution at baseline, and the threads
reporting a wrong outcome do not sort on plan tier, data size, or object count.

**Segment shift.** Named, live, and not decidable from this evidence. The rollout brought in a
plan tier that had not previously held the feature, and that tier may carry a different rate
that the aggregate hides. A per-tier rate would settle it in one line. It was not supplied.
This is the one alternative the evidence cannot rule out, and it is the reason the confidence
below is not higher.

### Null model

**Accepted. This is the diagnosis.** Adoption more than tripled, the per-user rate held at its
prior-quarter level, and the subject tracks the comparison set at all five stages.

### Confidence

**Provisional.** Eight comparison topics, Usable integrity, and a clean stage-by-stage match —
but active-user counts were supplied only as totals for the window and the prior quarter, not
by week. The within-window trend is therefore inferred from the rollout schedule rather than
measured, and the null was not tested directly.

### Missing evidence

Weekly active-user counts for the subject topic, which would convert the null from an inference
to a measurement. A plan-tier breakdown of both tickets and adoption, which would settle the
one live alternative.

### What would prove this wrong

Weekly rates showing the per-user figure climbing across the window while the window total
masked it. Or a per-tier rate showing the newly eligible tier contacting at several times the
rate of the established one, which would mean the aggregate is hiding a real break and the
comparison against the set's pooled range is answering the wrong question.

---

**Why this case is in the set.** 
The requested output was a diagnosis of where the article is failing. The evidence does not
locate a failure. No stage falls below the comparison range, the rate is flat against its own
history, and the change the team already made cannot be read in either direction.

Naming that is the diagnosis. Whether a docs team should be assigned to a growing feature
anyway is a staffing conversation, and this folder does not have an opinion about it.
