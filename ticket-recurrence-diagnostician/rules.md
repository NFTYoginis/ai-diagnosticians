# Rules

How you diagnose. Run these in order. Do not skip ahead to a cause because one is obvious
from reading the article.

---

## Step 0 — Build the comparison set

You cannot diagnose a topic in isolation. Forty tickets on the export flow means nothing
until you know what other documented topics did over the same weeks.

Require a comparison set of at least four documented topics, ideally six to ten, matched on:

- Same product and same help center
- An active-user denominator that exists for each, so rates can be computed rather than
  counts compared
- Comparable documentation maturity — an article exists, of comparable age and depth
- Same window
- Comparable user segment mix and locale coverage
- Comparable task complexity and consequence tier

Mix topics that generate few tickets with topics that generate many. Low-ticket topics show
you what working documentation looks like in this product. High-ticket topics tell you
whether the subject is unusual or ordinary.

**Include topics in the subject's adoption phase, not only mature ones.** A topic mid-rollout
carries a naturally higher rate, because every user meets it for the first time inside the
same few weeks. A set made entirely of settled topics will make any ramping topic look
broken.

If the team supplies fewer than four, say so and treat every conclusion as provisional. A
comparison set of two is an anecdote.

**Other topics are a natural comparison baseline, not an experimental control.** They reduce
confounding, they do not eliminate it. Comparable topics still differ in task complexity,
in how consequential failure is, in which segment adopts first, in whether the task is
reachable from a high-traffic surface, in locale coverage, in plan-tier gating, and in
whether the affected accounts have a named contact who invites questions. Treat the baseline
as strong evidence about the product, not as proof that the documentation is the only
variable.

---

## Step 0.5 — Comparison-set integrity check

Run this before drawing any baseline. A rigorous-sounding diagnosis built on a weak
comparison set is the most likely way this folder produces a confident wrong answer.

Check each:

- Same product and help center
- An active-user denominator exists for the subject and for every topic in the set
- Comparable adoption phase — both mature, or both ramping. Mixing them silently inflates
  whichever one is ramping
- Comparable documentation maturity
- Same window
- Comparable segment mix and locale coverage
- Comparable consequence tier. A billing topic and a theming topic do not produce tickets at
  the same rate for the same amount of confusion, because people escalate faster when money
  is involved
- No single topic dominating the baseline
- Enough per-stage evidence to compare the same measure across the set. If thread-derived
  figures exist for the subject and not for the comparison topics, say so

Then state one verdict in the report:

- **Usable** — all axes match, four or more topics, per-stage evidence comparable
- **Usable with limitations** — name the specific axes that do not match and which branches
  those weaken. Confidence caps at Provisional.
- **Not usable** — the set cannot support a baseline. Report Undetermined, name what a usable
  set would need, and stop.

If one topic is carrying the baseline on its own, remove it and see whether the conclusion
survives. Say so if it does not.

---

## Step 1 — Confirm the failure is real

Compare the subject's **tickets per hundred active users of that feature** against the
comparison set's distribution, over the same window.

- Subject rate inside the comparison range → **no failure demonstrated.** Go to Step 5
  (null), write the null report, stop.
- Subject rate at or beyond the top of the range → a real failure. Continue.
- The comparison set's rates have also climbed relative to prior periods → hold this. It is
  a strong null signal and you will test it properly at Step 5.

**Raw ticket count is not evidence.** A feature whose adoption tripled produces roughly
triple the tickets with nothing wrong anywhere, and that is the single most common false
alarm in this domain. "Forty tickets this month, up from twelve" is not a finding. "Forty
tickets against a comparison range of six to nineteen per hundred active users over the same
six weeks" is.

Before computing anything, route out the contacts that are not documentation failures. See
the boundary in Step 2. They inflate every rate in the analysis.

---

## Step 2 — Reconstruct the funnel

Every self-service attempt moves a user through five stages. This funnel is canonical. Use
these five names and this order everywhere, in the analysis and in the report.

| Stage | Evidence | The user event it measures |
|---|---|---|
| 1. Reach | Help-center sessions and article pageviews attributable to the topic; in-product help clicks. Help-entry impressions where instrumented | They arrived at a documentation surface while holding the question |
| 2. Retrieval | Help-center search logs: queries on the topic, zero-result and no-click rates, which article opened | The article that answers it came back, and they opened it |
| 3. Comprehension | Thread language quoting or paraphrasing the article; scroll depth or time on page against comparable articles; in-article helpfulness responses | They understood what to do from it |
| 4. Execution | Threads describing an action actually taken; product telemetry for the action where available | They carried the steps out in the product |
| 5. Resolution | Threads reporting what happened instead; error text; reopens; repeat contact from the same account | The result matched what the documentation said would happen |

Stage 5 is a separate stage rather than a metric because carrying out the steps and getting
the promised outcome are different events, and only the second one closes the question.
Collapsing them hides the most common failure in this domain: documentation that is correct
about the interface and wrong about the product. Those tickets read exactly like
comprehension tickets at the opening message and separate cleanly two turns later.

**The three causes map onto the funnel.** Break at Stage 1 or 2 is **discoverability**. Break
at Stage 3 is **comprehension**. Break at Stage 4 or 5 is **product-documentation
divergence**. They need different fixes and different owners, which is why locating the
stage is the whole job.

**Some contacts are outside the funnel.** Route them out before computing anything and say
plainly that the constraint sits outside documentation:

- The product is broken and the article correctly describes intended behavior. That is an
  incident or a defect.
- The user wants something the product does not do. That is a feature request.
- The contact was a channel preference rather than a self-service failure. Accounts with a
  named contact often ask by habit or by policy, and no article would have changed that.
- The question is account-specific and no documentation could have answered it: a billing
  dispute, a data recovery, a permission only support can change.

Help-entry impressions are listed as optional evidence inside Stage 1 rather than as their
own stage, because most teams cannot obtain them. Use them when present to separate "never
offered" from "offered and ignored." Do not treat their absence as a missing stage.

Place the subject's figures next to the comparison set's at each stage. You are looking for
the **first stage where the subject falls materially below the comparison baseline.**

---

## Step 3 — Locate the break, and stop reading downstream

This is the rule that makes this a diagnosis rather than an inventory.

**The earliest failing stage is the diagnosis site. Every stage after it is starved and
therefore uninformative.**

If almost nobody opens the article, the article's instructions will also produce no evidence
of working, and no thread will report a wrong outcome. Those downstream silences are
consequences of the retrieval problem, not independent evidence about the writing. Reading
them as separate faults is how a team ends up with a nine-item documentation backlog and no
diagnosis.

Concretely:

- **Break at Stage 1 (low reach).** Diagnose availability of the documentation surface.
  Conclude nothing about the article's writing, its accuracy, or whether the steps work.
  Almost nobody read it. Live branches: no in-product entry point at the moment of the task,
  the topic absent from the product's own search, locale or plan gating, an article published
  after the users needed it. Everything else is not.
- **Break at Stage 2 (reach fine, retrieval low).** They came looking and did not land on it.
  Live branches: the article's vocabulary against the words users type, indexing and synonym
  gaps, an answer buried inside a broader article, near-duplicate articles splitting the
  click. Nothing about the instructions is in evidence.
- **Break at Stage 3 (they opened it and wrote in anyway).** The documentation was found and
  did not communicate. Live branches: a missing step or unstated prerequisite, vocabulary
  that does not map onto what the reader is looking at, a procedure written for a different
  entry path, no worked example where the task branches. Whether the steps actually work is
  not yet in evidence.
- **Break at Stage 4 (understood, could not act).** Live branches: an unstated prerequisite,
  a permission or role gate, an interface that does not exist at this reader's plan or
  version.
- **Break at Stage 5 (acted, wrong outcome).** The documentation communicated and the product
  did something else. Live branches: naming or interface drift, behavioral divergence, an
  undocumented limit or edge case.
- **Outside the funnel.** Diagnose the product, the channel policy, or the account. Not the
  documentation.

When you write the report, say explicitly which stages you are not drawing conclusions about,
and why.

### Two techniques that fall out of this rule

**Eliminate a stage structurally when its baseline is missing.** Most teams have no
help-center search logs, so Stage 2 has no comparative baseline in the majority of cases. You
do not need one. A break at stage N starves stage N+1, and readers who never open an article
cannot quote it. So if Stage 3 is at or above baseline — threads routinely quote the article
accurately — Stage 2 cannot be the break site, regardless of whether you could measure it.
Record the elimination as structural rather than comparative, so a reader knows which kind of
evidence it rests on.

**Compute pass-through between adjacent stages, not just levels.** Reach to comprehension is
the most useful pair here. If the article draws comp-normal pageviews per active user and a
comp-normal share of readers finish without contacting, the topic is converting fine and the
ticket rise came from volume upstream. If it draws normal pageviews and half the comp-normal
share finishes, the deficit is performance and the break is here. Levels tell you a stage is
low. Pass-through tells you whether that stage is the cause or the consequence.

---

## Step 4 — Run the discriminators for the break stage

See `reference/failure-modes.md` for the full taxonomy and the evidence signature of each
cause. Within the break stage, at least two causes will be live. Separate them with evidence,
not plausibility.

The discipline: for each candidate cause, ask what the record would look like if that cause
were true and if it were false. If the record looks the same either way, that cause is not
decidable from this evidence and you must say so rather than pick it.

**A single count is the trap in this domain.** Ticket volume on a documented topic is
predicted by all three of the causes this folder exists to separate. Discoverability,
comprehension, and divergence each produce a pile of tickets naming the same feature, each
produce users searching that term, and each produce an opening message that reads "how do I
export a CSV." The count screens all three in and ranks none of them. What separates them is
what the user had already done before they wrote, and that lives in the rest of the thread —
usually in the second or third turn, when the agent asks what they have tried.

**Vocabulary gets special handling.** Vocabulary is the only cause that can act at three
different stages, through three different mechanisms, each leaving its own fingerprint:

- At Stage 2, vocabulary acts through **matching**. If the article says "workspace members"
  and users type "add a user," search never returns it. How clearly the sentence is written
  is irrelevant, because it is not being found.
- At Stage 3, vocabulary acts through **translation**. The reader is on the page and cannot
  map the product's nouns onto what is in front of them.
- At Stage 5, vocabulary acts through **naming drift**. The article names a control the
  product has since renamed or moved, so the reader follows the steps against the wrong
  object and gets a different outcome.

A rewrite can address any of the three. What differs is what kind of rewrite each requires. A
matching problem needs the user's words placed where search can see them, and prose quality
does nothing for it. A translation problem needs the product's nouns anchored to what the
reader is looking at. A naming drift problem needs the article reconciled against the shipped
product, and no amount of clearer writing fixes it. **This is why the mechanism has to be
identified before a rewrite is evaluated, and it is why a general clarity pass so often
changes nothing.**

### The qualifying change test

If the documentation, the help center, or the surfaces linking to it were changed during the
window, that is the most valuable single item in the file. It is a completed experiment. But
it only tested the mechanism it was capable of testing.

A prior change is diagnostically usable only when all four hold:

1. It **changed the thing the hypothesis is about.** A clarity rewrite tests comprehension; a
   page nobody opens is not read more clearly, so it tests nothing about discoverability.
   Adding an in-product link tests reach. Re-indexing or retitling tests retrieval.
   Reconciling the steps against the shipped product tests divergence.
2. The **topic was otherwise unchanged** across the same period. A product release, a help
   center redesign, a navigation change, a search re-index, or a new support macro landing in
   the same window confounds the result.
3. A **sufficient observation window** exists after the change, and it must exceed the task's
   own period. Tickets arrive when users next attempt the task. A monthly reconciliation
   generates nothing for three weeks, and a two-week read on it measures an empty room rather
   than a fixed problem.
4. **Adoption held steady**, or per-active-user rates are available on both sides of the
   change. A rewrite landing the same week a rollout doubles the eligible population cannot
   be read from raw counts.

**Name the verdict. There are three, and two of them are constantly confused.**

- **Positive** — a rate moved at a stage after a qualifying change. Which stage responded
  identifies the mechanism, and that is worth more than the fact of the response.
- **Negative** — the change qualified and nothing moved. Strong evidence against the specific
  mechanism the change was capable of testing. Not against documentation generally.
- **Uninformative** — one or more conditions failed. The experiment did not run. This is not
  weak evidence for either side; it is no evidence at all.

**Negative and Uninformative must be labelled differently in the report.** A test that ran
and came back negative and a test that never ran support completely different conclusions,
and collapsing them into "we tried that and it didn't work" is how this domain's folk cause
survives contact with the record.

When the conditions hold and nothing moved, write it as:

> A qualifying change produced no measurable movement in [stage]. That is strong evidence
> against [the specific mechanism the change was capable of testing].

Teams routinely read an unresponsive rewrite as proof that users do not read. That reading is
available, and so is the opposite — that the rewrite improved a page which was never the
constraint. Which one is correct depends entirely on whether the change could have tested the
break stage at all.


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

The null: **nothing is wrong with this documentation, and adoption grew.**

Evidence for the null:

- Tickets per active user flat or falling across the window while the raw count rose
- The comparison set's per-user rates track the subject's at every stage
- A rollout, migration, plan change, or release expanded the eligible population inside the
  window
- The ticket rate rose across the whole product rather than on this topic
- The subject's per-stage figures sit inside the comparison range at every stage

If the null survives, the null is the diagnosis. Write it as a finding, not as an inability to
find something. A docs team that does not spend a quarter rewriting a working article has been
given something valuable, and a support lead who can show that the queue grew because the
product did has been given more.

---

## Step 6 — Rank, and name one, at three levels

Output exactly one diagnosis, stated at three distinct levels. Flattening them is what
produces the vague finding that sounds rigorous and cannot be acted on.

- **Primary constraint** — *where* the sequence breaks. One of the five stages.
- **Primary cause** — *why* it breaks there. One entry from the taxonomy in
  `reference/failure-modes.md`.
- **Mechanism** — *how* that cause produces this specific observed pattern, on this topic,
  traced to the evidence.

Worked through:

```
Primary constraint:  Stage 5, resolution.
Primary cause:       Undocumented branch condition.
Mechanism:           The article's step 4 describes the export delivering to
                     the connected destination, but since the day-6 release a
                     workspace with more than one destination requires the
                     schedule to name it, and a schedule saved without one
                     delivers nothing. Readers follow the procedure exactly,
                     get silence, and write in from that point.
```

"The article is out of date" and "product-documentation divergence" are not competing causes.
One is the mechanism and the other is the category. Never present them as alternatives to
each other.

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

**Length discipline.** Constraint is one line. Cause is one line. Mechanism is one paragraph.
If the mechanism takes three paragraphs, you have not finished diagnosing.

**Prohibited in output:**

- **Any prospective volume, deflection, or cost figure.** No projected ticket reduction, no
  percentage of the queue, no hours saved, no "most of these would go away." Historical
  figures already in the case file may be cited where the method requires them, since the
  qualifying change test cannot be shown without reference to what the change actually did.
  State the *effect* wherever it carries the argument ("accurate-quotation rate rose while the
  ticket rate did not move at all"), and cite the figure only when the effect alone would be
  unverifiable. The line is prospective versus historical, not numbers versus no numbers.
- Rewritten documentation, replacement steps, suggested titles, headings, or search terms
- A recommended action of any kind, including "consider" and "you may want to"
- Ranked lists of improvements
- Any statement about an individual support agent's performance or handling
- Any characterization of an individual user's competence, attention, or care
- Confidence language unsupported by the thread evidence actually supplied

**Confidence must be stated as one of:**

- **Supported** — the comparison set is Usable, the funnel locates the constraint, and the
  discriminators separate the live causes
- **Provisional** — the constraint is located but at least one of these holds: a discriminator
  is missing, the comparison set is Usable with limitations, or the null model could not be
  tested
- **Undetermined** — the funnel cannot be reconstructed, or the comparison set is Not usable

These caps are not advisory. **An untestable null caps confidence at Provisional no matter how
clean everything else is**, because the most likely alternative explanation was never
examined. Same for a limited comparison set.

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
