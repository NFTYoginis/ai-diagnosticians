# Ticket Recurrence Diagnostician

**v0.2** · Status: **three blind runs across three cases**, each run in a session that had never
seen this folder and was forbidden from opening the answer keys, each scored line by line against
assertions written before the run. No retrospective field validation — every case here is
constructed, and nothing has been checked against a real support queue with a known outcome.

**Read those run scores with one caveat.** They were taken before a routing defect was found in
Step 1, which let the screen terminate and skip the funnel the output contract requires. The runs
passed because they did not follow that instruction, not because it was sound. It is fixed, and
the folder that scored has not been re-run as the folder that now ships.

A folder you drop into a Claude Project. Claude becomes a diagnostician that works out why
tickets keep arriving for something your documentation already covers.

It is built for one moment: the same question keeps landing in the queue, a meeting is coming
about whose failure that is, and someone is about to conclude that users do not read.

That conclusion survives because it fits every observation. Users who never found the article,
users who read it and could not follow it, and users who followed it exactly and got a
different result all write the same first message. This tells you which pile you actually
have, because the three need different fixes and different owners.

---

## What it does

Reconstructs the path a user takes to answer their own question, compares your topic against
other documented topics in the same product over the same weeks, finds the earliest stage
where yours falls below that baseline, and names the one cause the evidence supports.

Then it tells you what would prove it wrong.

## What it does not do

- Write or rewrite documentation, suggest a title, or propose search terms
- Prioritize a backlog or recommend a fix
- Evaluate a support agent
- Characterize a user's competence
- Estimate how many tickets something would deflect, or what they cost

It stops at the cause. What to write about it is a technical writer's job, and it is a
different job with different inputs.

---

## Setup

1. Create a Claude Project.
2. Upload everything in this folder **except `tests/`** to the project knowledge.

   `tests/` stays out deliberately. It holds the answer keys the regression cases are scored
   against, and a diagnostician that can read its own expected outputs is not being tested by
   them. It belongs in the repo, where a stranger can run the cases and check the result
   against the key themselves. It does not belong in the project, where the folder under test
   would be reading them.
3. Paste this into the project's custom instructions:

   > Follow identity.md and rules.md exactly. Run the diagnostic sequence in rules.md in
   > order and use the output contract at the end of that file. Consult reference/ as
   > needed. Do not recommend actions.

That is the whole install. No dependencies, no API keys, nothing to run.

---

## Running a case

Upload the case materials and say: **"Diagnose this ticket pattern."**

### What you need

Four things. Without all four you will get an Undetermined result rather than a wrong one.

1. **The documentation** — the article as published, with publication and last-edit dates, and
   the surfaces that link to it
2. **Full ticket threads** — every turn, in order, not opening messages
3. **Four or more comparison topics** — other documented topics in the same product, same
   window, each with an active-user count
4. **An active-user count for this feature** over the window

The second item is the one most often substituted for and the one the method depends on
entirely. **"How do I export a CSV" is compatible with every cause in the taxonomy.** It is
what a user writes whether they never found the article, read it and could not follow it, or
followed it exactly and got an empty file. The turn that separates those is usually the second
or the third, when the agent asks what they have tried. A summary destroys it, and so does a
tag, which was assigned by someone who had already decided what the ticket was about.

The fourth item is what stops a growing feature from looking like a broken one.

### What sharpens it considerably

- **Help-center search logs.** The only direct evidence at retrieval, and the difference
  between naming a discoverability cause and eliminating one structurally.
- **Article edit dates against your release dates.** Documentation goes stale without anyone
  touching it, and that pattern is invisible if you only read the article.
- **The rollout or adoption curve**, by week. This is what the null model runs on.
- **Locale and plan-tier breakdown** of both tickets and adoption.

Full intake list in [reference/intake.md](reference/intake.md).

---

## What you get back

A report with fixed headings, in this order:

Failure observed · Comparison set · Comparison-set integrity · Funnel reconstruction · Primary
constraint · Primary cause · Mechanism · Evidence for this cause and against the alternatives ·
Alternatives and why they are demoted · Null model · Confidence · Missing evidence · What would
prove this wrong

The diagnosis comes at three levels rather than one, because flattening them produces a finding
that sounds rigorous and cannot be acted on. **Constraint** is where the sequence breaks.
**Cause** is why it breaks there. **Mechanism** is how that cause produces this specific
pattern on this topic.

Three worked examples in [examples.md](examples.md), including one that finds nothing wrong.

---

## The three answers people find surprising

**"Your documentation is fine and your feature grew."** If tickets per active user held steady
while the raw count tripled, nothing broke — the denominator moved. This comes back more often
than teams expect, and it is the finding that saves the most time, because a quarter spent
rewriting a working article removes nothing.

**"Your rewrite already answered this."** A change you shipped is a completed experiment, but
it only tested the mechanism it was capable of testing. A clarity pass on a page almost nobody
opens says nothing about discoverability. When a change *did* qualify and nothing moved, that
is strong evidence against that mechanism, and the usual reading — that users do not read — is
the weaker of the two available.

**"I cannot tell you from this."** If you supply opening messages instead of threads, it names
the missing input and stops rather than producing a confident cause built on nothing. That is
the intended behavior, not a bug.

---

## How it decides

The method turns on one rule.

Every self-service attempt moves a user through five stages: **reach, retrieval, comprehension,
execution, resolution.** Find the earliest one where yours falls below the comparison baseline.
**That stage is the diagnosis site, and every stage after it is starved and therefore tells you
nothing.**

The three causes fall out of the stage. A break at reach or retrieval is **discoverability**. A
break at comprehension is **comprehension**. A break at execution or resolution is
**product-documentation divergence** — the article is right on paper and wrong about the
product.

Resolution is a stage rather than a metric because carrying out the steps and getting the
promised outcome are different events, and only the second one closes the question. Those
tickets read exactly like comprehension tickets at the opening message and separate cleanly two
turns later.

If almost nobody opens the article, no thread will report that the steps failed. That silence
is a consequence of the retrieval problem, not evidence about the writing. Reading it as a
separate fault is how you end up with a nine-item documentation backlog and no idea which item
is producing the queue.

The rest of the method is separating the causes that are live at that one stage, using evidence
rather than plausibility, and then trying to reject the whole thing with the null before
committing to it.

Full method in [rules.md](rules.md). Cause taxonomy with evidence signatures in
[reference/failure-modes.md](reference/failure-modes.md).

---

## Files

```
ticket-recurrence-diagnostician/
├── README.md                      this file
├── identity.md                    who it is, what it diagnoses, what it refuses
├── rules.md                       the method and the output contract
├── examples.md                    three worked cases, one of them a null
└── reference/
    ├── failure-modes.md           causes by funnel stage, with evidence signatures
    ├── baselines.md               building the comparison set and reading it
    └── intake.md                  required inputs and missing-evidence handling
```

---

## Scope and honesty

The examples are constructed teaching cases with figures chosen to make each discriminator
legible. They are not customer files and the numbers in them are not benchmarks.

There are deliberately no industry-average figures anywhere in this folder. Ticket rates,
deflection rates, and normal help-center behavior vary by product, segment, price point, and
how much a failure costs the user, and any number quoted as an industry average would be wrong
for most products while being treated as authoritative. Every baseline is computed from your
own comparison set.

This diagnoses documentation performance against topics you supply. It does not read your help
center, model your product, or know anything about your users beyond the records you give it.

Support threads routinely contain personal data and customer business information. Whether to
place them in a project is your disclosure decision. The report refers to users by segment, to
agents not at all, and reproduces neither.
