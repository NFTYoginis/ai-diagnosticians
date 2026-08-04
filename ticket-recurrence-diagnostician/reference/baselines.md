# Baselines

The comparison set is what turns an opinion into a diagnosis. This file covers how to build
it and how to decide what counts as underperformance.

There are no industry benchmark numbers here on purpose. Ticket rates, deflection rates, and
normal help-center behavior vary enormously by product, segment, price point, and how much a
failure costs the user. Any figure quoted as an industry average would be wrong for most
products and would be treated as authoritative anyway. **Every baseline in a diagnosis is
computed from that case's own comparison set.**

---

## Building the comparison set

Match on the axes that determine how many tickets a working topic produces:

- **Same product and help center** — a different product's docs are a different information
  architecture, a different search index, and a different user base.
- **An active-user denominator** for every topic in the set. This is not optional. Without it
  you are comparing counts, and counts are what produced the false alarm you were called in
  to check.
- **Documentation maturity** — an article exists, of comparable age and depth. A topic with a
  three-paragraph stub and a topic with a twelve-section guide are not comparable, and neither
  is a topic documented last week against one documented two years ago.
- **Window** — the same weeks. A release, a migration, or a seasonal peak inside one window
  and not the other invalidates the comparison.
- **Segment mix and locale coverage** — the population attempting the task.
- **Complexity and consequence tier** — a billing task and a theming task do not produce
  tickets at the same rate for the same amount of confusion, because people escalate faster
  when money is at stake and abandon quietly when it is not.

Four is the floor. Six to ten is a usable set. Below four, state that the range is not
established and cap confidence at Provisional.

**Include topics in the subject's adoption phase, not only settled ones.** A topic mid-rollout
carries a naturally higher rate because every user meets it for the first time inside the
same few weeks. A comparison set made entirely of mature topics will make any ramping topic
look broken, and that error produces the exact false positive the null model exists to catch.

---

## Establishing the rate range

Take **tickets per hundred active users of the feature** for every topic in the set, over the
window. You need the spread, not the average.

The subject is underperforming when its rate sits **at or beyond the top of the comparison
range**, not when it exceeds the mean. Half of all topics exceed the mean by definition, and
treating the mean as a target manufactures failures that do not exist.

Then check whether the range itself moved. If the comparison set's rates rose across the same
weeks, something product-wide happened and the null is live before you look at anything else.

**Route out the non-documentation contacts first.** Defects, feature requests, channel-preference
contacts, and account-specific asks inflate the numerator, and they do not distribute evenly
across topics. See the boundary in `failure-modes.md`.

---

## Per-stage baselines

Compute the comparison set's figures for each of the five canonical stages and compare:
**Reach, Retrieval, Comprehension, Execution, Resolution.**

**Reach.** Article pageviews per hundred active users of the feature, over the window.
Normalizing on active users rather than on total customers is the equivalent of measuring per
week rather than per listing: a feature used by 400 people and one used by 40,000 do not
produce comparable pageviews, and comparing raw totals is the most common error in
team-run comparisons.

**Retrieval.** Queries on the topic that ended with the article opening, as a proportion of
queries on the topic. Absolute query counts are noisy. Where search logs do not exist, this
stage has no comparative baseline and must be handled by structural elimination — see below.

**Comprehension.** The proportion of readers who did not subsequently contact, where
reader-to-ticket attribution exists. Where it does not, use the proportion of tickets on the
topic whose threads show article contact. A high proportion means readers are reaching the
page and failing on it. A low proportion means they are not reaching it, which is a Stage 1 or
2 finding wearing a Stage 3 costume.

**Execution.** Where product telemetry exists, attempts as a proportion of readers. Where it
does not, the proportion of threads describing an action actually taken.

**Resolution.** Completions as a proportion of attempts. Where telemetry does not exist, the
proportion of threads reporting a wrong outcome rather than a block. A blocked reader and a
reader holding a wrong result write different sentences, and that difference is the whole
Stage 4 versus Stage 5 split.

The last three are thread-derived in most teams, which is why whole threads are a required
input rather than a nice-to-have. If they were computed on the subject and not on the
comparison topics, the comparison is not established and the integrity check must say so.

---

## What the comparison set is, and is not

The comparison set is a natural comparison baseline. It is not an experimental control.

Matching on product, denominator, maturity, window, segment, and complexity removes a great
deal of confounding, which is why the method works at all. It does not hold everything
constant. Comparable topics still differ in how consequential failure is, in which segment
adopts first, in whether the task is reachable from a high-traffic surface, in plan-tier
gating, and in whether the affected accounts have a named contact who invites questions.

Write conclusions accordingly. "The subject falls below its comparison baseline at Stage 2"
is supportable. "The only variable is the documentation" is not, and it is the phrasing that
turns a good baseline into a false proof.

### The set cannot detect a cause it is matched on

Matching is what makes a comparison work and it is also what makes a comparison blind. Every
axis you match on becomes invisible: if all six comparison topics are English-only, the set
cannot tell you anything about locale, because locale does not vary across it.

This matters most when the matched axis is a live hypothesis. Name it in the report as a live
alternative that this comparison set is structurally unable to test, and name what would test
it — usually a second set that varies on that axis and holds the rest. Do not report it as
ruled out. A variable held constant has not been examined.

---

## What counts as "materially below"

Judgment, stated explicitly in the report rather than applied silently.

For the entry rate, where high is bad:

- **Clearly above** — the subject's tickets per active user exceed the highest topic in the
  set. Treat as a confirmed failure.
- **Ambiguous** — inside the range but in the top quarter. Note it, do not treat it as
  confirmed on its own.
- **At baseline** — inside the range. No failure demonstrated.

For per-stage pass-through figures, where low is bad:

- **Clearly below** — subject is under the lowest topic in the set on that stage. Treat as a
  located break.
- **Ambiguous** — inside the range but in the bottom quarter. Note it, do not treat it as the
  break unless a later stage is clearly below.
- **At baseline** — inside the range. This stage is not the break. Move to the next stage.

If no stage is clearly below, the funnel is performing at product-normal rates and the null is
likely the answer. Do not manufacture a break by lowering the bar until one appears.

---

## The qualifying change test

The single most useful piece of history in any case file, and the easiest one to over-read.

A documentation change made during the window is a completed experiment. But an experiment
only tests what it was capable of testing, and most documentation changes are not capable of
testing most mechanisms.

### Step 1: does the change qualify

All four must hold before the result means anything.

| Condition | Why it matters | Fails when |
|---|---|---|
| **Changed the thing under test** | A change only tests the mechanism it acted on. Clarity acts at comprehension, links act at reach, titles and indexing act at retrieval, reconciliation acts at divergence | A clarity rewrite on a page almost nobody opens, offered as evidence about discoverability |
| **Otherwise unchanged** | Simultaneous changes confound the result | A product release, help-center redesign, navigation change, search re-index, or new support macro landed in the same window |
| **Sufficient window, exceeding the task's period** | Tickets arrive when users next attempt the task | Two weeks of observation on a task users perform monthly. The room was empty, not fixed |
| **Adoption held steady** | Raw counts are uninterpretable when the denominator moves | A rollout expanded the eligible population inside the observation window and only raw counts are available |

If any condition fails, the change is **Uninformative**. Say which condition failed and do not
use the change as evidence in either direction. An experiment that did not run is not weak
evidence for the null. It is no evidence.

### Step 2: read a qualifying change

Compare the four weeks before against the four weeks after, or one full task period on each
side, whichever is longer. Stage by stage, on rates rather than counts.

- **A rate moved at a stage** — that mechanism was a real constraint. Which stage responded
  identifies it, and that is more valuable than the fact of the response. Record as
  **Positive**.
- **Comprehension improved and the ticket rate did not move** — the rewrite worked at what it
  was capable of testing, and it fixed a stage that was never the constraint. Two findings,
  not one, and the second is the more useful.
- **Nothing moved** — strong evidence against **the specific mechanism this change was capable
  of testing**. Name that mechanism explicitly. A clarity pass that left the title and the
  index untouched says nothing about retrieval, and a new in-product link says nothing about
  whether the steps work. Record as **Negative**.

**Negative and Uninformative are different verdicts and must be labelled differently.** One
means the test ran and the hypothesis lost. The other means no test occurred. Teams read an
unresponsive rewrite as proof that users do not read; that reading is available, and so is the
opposite, and which one is correct depends entirely on whether the change could have tested
the break stage at all.

---

## Releases, rollouts, and seasonality

Before attributing a rise to the documentation, check whether the window contains a release, a
rollout, a migration, a pricing or packaging change, or a seasonal peak that affected the
whole product. If the comparison set is matched on window, most of this is already controlled
for, which is why the window match matters more than most teams assume.

Two patterns that are specific to this domain and easy to miss:

**A rollout moves the denominator, not the numerator.** Raw tickets rise, rates hold. That is
the null, and it is the most common correct answer this folder produces.

**A release moves the article without touching it.** Documentation that was accurate on
Monday is divergent on Tuesday and nothing in the article's edit history shows it. Always
check the article's last-edit date against the release dates in the window. A Stage 5 break
with an article older than the release behind it is the signature, and it is invisible if you
only read the article.
