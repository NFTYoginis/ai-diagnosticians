# Job Post Mismatch Diagnostician

**v0.1** · Status: built. Not yet exercised by a blind run, and no retrospective field validation.

A folder you drop into a Claude Project. Claude becomes a diagnostician that works out why a
requisition is not producing qualified applicants.

It is built for one moment: the role has been open longer than expected, the pile is the wrong
pile, and the meeting with finance is coming. The recommendation about to be made is that the
market is tight and the band needs to go up. Before that becomes a decision, this tells you
whether the evidence actually supports it.

A raise aimed at the wrong constraint costs money on every future hire in that band and does not
fill the role. Locating where the requisition actually breaks is what tells you whether you are
about to apply the right intervention to the wrong problem.

---

## The subject is the post. Not the applicants.

**This folder never evaluates, ranks, or scores an individual applicant, and it does not read
applications, résumés, cover letters, portfolios, or candidate names.** If you supply them, it
declines and asks for aggregate counts instead.

That is not a disclaimer bolted on the front. It is the architecture. The screening stage runs on
counts your own screening produced — *of 231 submissions, 14 met the stated must-haves, broken out
by channel* — and never on the submissions themselves. The method was built so it never needs
them.

The reason is written into [rules.md](rules.md) with the regulation named. Under the EU AI Act,
systems used for recruitment or selection sit in the high-risk annex, in particular systems used
to place targeted job advertisements, to analyse and filter applications, and to evaluate
candidates. Reading applications is the second and third of those. In New York City, Local Law 144
requires an annual bias audit for automated employment decision tools that substantially assist
screening. A folder published openly, that anyone can point at a stack of résumés, has no business
being on that side of the line.

It is a scoping decision, not legal advice. Anyone deploying near this line should take their own.

---

## What it does

Reconstructs the candidate funnel for your requisition, compares it against comparable
requisitions over the same weeks, finds the earliest stage where yours falls below that baseline,
and names the one cause the evidence supports.

Then it tells you what would prove it wrong.

## What it does not do

- Recommend a compensation figure, a band, or a percentage
- Rewrite your post, suggest a title, or propose a requirement list
- Recommend a channel, a vendor, an ATS, or a sourcing strategy
- Analyze applicant demographics or infer protected characteristics
- Evaluate the recruiter, the screener, or the hiring manager
- Tell you what to do next

It stops at the cause. What you do about it is your conversation with your hiring manager and
finance, and it is a different conversation with different inputs.

---

## Setup

1. Create a Claude Project.
2. Upload the contents of this folder to the project knowledge.
3. Paste this into the project's custom instructions:

   > Follow identity.md and rules.md exactly. Run the diagnostic sequence in rules.md in
   > order and use the output contract at the end of that file. Consult reference/ as
   > needed. Do not recommend actions.

That is the whole install. No dependencies, no API keys, nothing to run.

---

## Running a case

Upload the case materials and say: **"Diagnose this requisition."**

### What you need

Four things. Without all four you will get an Undetermined result rather than a wrong one.

1. **The post as published**, on every channel, with edit history and dates
2. **Channel-level funnel data** — impressions, views, apply-starts, submissions, by channel and
   by week, plus sponsorship spend
3. **Four or more comparison requisitions** — same company where possible, adjacent level,
   comparable band, location, work model, window, and channels
4. **Aggregate screening counts** — for each stated must-have, how many submissions met it,
   **broken out by channel**

The fourth is the one teams try to substitute for, and the substitution is always the same: *here
are the applications, you tell us.* That is the one thing this will not do. It is also the item
most often supplied pooled, and pooled is not enough — the by-channel spread is the only thing
that separates the two live causes at the screening stage.

One counterintuitive rule on the third item: **do not pick comparison requisitions that share
your post's requirement structure.** That is the variable under test. A comparison set matched on
it cannot detect a requirement problem, because the suspected cause is held constant across every
member of the set.

### What sharpens it considerably

- **Your written screening rules**, including any criterion not stated in the post. This is what
  catches a screen that is rejecting on something nobody published — a different finding with a
  different owner than "unqualified applicants."
- **The channel's salary indexing and filter documentation.** Threshold exclusion cannot be
  confirmed without it, and the folder will not invent it.
- **Whether a compensation edit was republished or edited in place.** Without that, a raise cannot
  be evaluated at all.
- **Withdrawal counts after first contact**, with reasons in aggregate.
- **Competing posts visible in the same search results.**

Full intake list in [reference/intake.md](reference/intake.md).

---

## What you get back

A report with fixed headings, in this order:

Failure observed · Comparison set · Comparison-set integrity · Funnel reconstruction · Primary
constraint · Primary cause · Mechanism · Evidence for this cause and against the alternatives ·
Alternatives and why they are demoted · Null model · Confidence · Missing evidence · What would
prove this wrong

The diagnosis comes at three levels rather than one, because flattening them produces a finding
that sounds rigorous and cannot be acted on. **Constraint** is where the funnel breaks. **Cause**
is why it breaks there. **Mechanism** is how that cause produces this specific pattern in this
requisition.

Three worked examples in [examples.md](examples.md), including one that finds nothing wrong.

---

## The three answers people find surprising

**"Your post is fine and the pool is thin."** If every stage sits inside the comparison range and
the whole set is drawing a handful of qualified people, there is no post-specific problem. A raise
here resets the floor for every future hire at that level and does not produce a candidate who
does not exist. This is the finding that saves the most money.

**"Your raise already answered this."** A change is a completed experiment, but it only tested the
mechanism it was capable of testing. And a range edited in place on a live post tests nothing at
all, because it does not re-notify the candidates who already filtered past it. The money changed
and the market never saw it.

**"I cannot tell you from this."** Supply pooled screening counts instead of by-channel and it
reports the two live causes as tied and names the input that would separate them, rather than
picking the more plausible one. That is intended behavior.

---

## How it decides

The method turns on one rule.

Every requisition moves candidates through five stages: **reach, consideration, application,
screening pass, interview conversion.** Find the earliest one where yours falls below the
comparison baseline. **That stage is the diagnosis site, and every stage after it is starved and
therefore tells you nothing.**

The hiring conversation already knows two of these. Low volume means it never reached them, which
is reach or consideration. High volume with the wrong people means the requirements signal for the
wrong thing, which is screening pass. The funnel adds the two the conversation hides: a
requisition can lose qualified people at the application form, and it can lose them in the first
conversation, and from the outside both look exactly like a tight market.

Interview conversion is a stage rather than a metric because reading a post and having a
conversation about the job are different decisions made on different information. The first is a
judgment about the advertisement. The second is a judgment about the role.

A post drawing a quarter of normal impressions will also produce few submissions and a small
screened-in pool. Those are consequences, not separate faults — and a handful of submissions is
not a readable sample of who the post attracts, which is exactly how a distribution problem gets
misdiagnosed as a requirements problem.

The rest of the method is separating the causes that are live at that one stage, using evidence
rather than plausibility, and then trying to reject the whole thing with the null before
committing to it.

Full method in [rules.md](rules.md). Cause taxonomy with evidence signatures in
[reference/failure-modes.md](reference/failure-modes.md).

---

## Files

```
job-post-mismatch-diagnostician/
├── README.md                      this file
├── identity.md                    who it is, what it diagnoses, what it refuses
├── rules.md                       the boundary, the method, and the output contract
├── examples.md                    three worked cases, one of them a null
└── reference/
    ├── failure-modes.md           causes by funnel stage, with evidence signatures
    ├── baselines.md               building the comparison set and reading it
    └── intake.md                  required inputs and missing-evidence handling
```

---

## Scope and honesty

The examples are constructed teaching cases with figures chosen to make each discriminator
legible. They are not client files, they contain no applicants, and the numbers in them are not
market benchmarks.

There are deliberately no industry-average figures anywhere in this folder. Application rates,
pass proportions, time to fill, and normal impression volume vary by role family, seniority,
market, work model, employer exposure, and season, and any number quoted as an industry average
would be wrong in most searches while being treated as authoritative. Every baseline is computed
from your own comparison requisitions.

This diagnoses post and channel performance against requisitions you supply. It is not a market
survey, a compensation benchmark, or a sourcing tool, and it does not model your labour market
beyond the requisitions you give it.
