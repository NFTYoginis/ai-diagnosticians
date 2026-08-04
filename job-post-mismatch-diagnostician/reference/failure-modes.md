# Failure modes

Organized by funnel stage, because the stage where the requisition breaks determines which
causes are even eligible. Each entry gives the signature that distinguishes it, and the
counter-signature that rules it out.

---

Canonical funnel, used throughout: **1. Reach · 2. Consideration · 3. Application ·
4. Screening pass · 5. Interview conversion.** Referrals, sourced candidates, and post-offer
failures are outside the funnel.

Every signature below is written in aggregates and counts. **None of them requires reading an
application, and none of them may be established by reading one.** See the boundary in
`rules.md`.

---

## Stage 1 — Break at reach

The post is not being served. Nothing about who it attracts is in evidence yet, and a small
pile of submissions is not a sample of anything.

### 1A. Compensation filter floor

The posted range sits just under a filter increment, so the post never appears in the searches
of candidates who would take it.

- **Signature:** the range's lower bound is 1% to 10% under a round filter increment ($100k,
  $120k, $150k, or the local convention). Impressions materially below comparison requisitions
  whose lower bound clears the increment. The deficit is **confined to channels that expose a
  salary floor filter** and absent on channels that do not.
- **Rules it out:** the lower bound comfortably clears the increments in use, or impressions are
  at baseline.
- **Note:** this is a distribution problem wearing a compensation costume. The role is not
  underpaid by $2,000. It is invisible to a filter. Most boards index a range on its **lower**
  bound, so a generous top does not rescue a low floor.
- **Requires a supplied input:** the channel's indexing and filter behaviour is a fact about
  that channel, not something derivable from funnel data. If it was not supplied, this cause
  cannot be confirmed and stays tied with the other live Stage 1 causes. Name the missing input
  rather than inventing the behaviour.

### 1B. No range posted

- **Signature:** the post carries no compensation range in a market or channel where ranges are
  the norm or are legally required. Impressions below comparison requisitions that state one.
  Some channels exclude range-less posts from filtered searches entirely.
- **Rules it out:** a range is posted, or comparison requisitions without ranges show baseline
  impressions.

### 1C. Title mismatch with search behaviour

The post carries an internal title rather than the one the population searches.

- **Signature:** impressions far below comparison requisitions on the same channels at
  comparable spend. The title omits the market-standard term. Comparison requisitions using the
  standard title show baseline impressions.
- **Rules it out:** comparison requisitions sharing the subject's title convention also show
  baseline impressions.
- **Note:** a distribution problem wearing a branding costume.

### 1D. Channel absent from where the population looks

- **Signature:** impressions concentrated on one or two general channels. Comparison
  requisitions that filled used a channel the subject is not on. The specialty's known venues —
  a specialist board, a professional body, a community — are unused.
- **Rules it out:** channel mix matching the comparison set.

### 1E. Sponsorship exhaustion, expiry, or de-ranking

- **Signature:** impressions collapse at a date. The shape is a cliff, not a decline, and the
  date matches budget exhaustion, the end of a boost, a listing expiry, or a duplicate posting
  splitting the ranking.
- **Rules it out:** impressions flat or gently declining across the window, and the board's own
  status showing the post live and in-index throughout.

---

## Stages 2 and 3 — Break at consideration and application

They were served it and did not open it, or opened it and did not finish. What is in evidence:
everything visible on the listing card and the post itself. What is not in evidence: who the
post attracts, because too few completed to say.

### 2A. Compensation by comparison

They saw it beside what else that money buys in the same results and passed.

- **Signature:** impressions at or above baseline, apply-starts materially below. Competing
  posts visible in the same results carry higher stated ranges, or clearer ones, at comparable
  scope.
- **Weakens it:** a **qualifying** raise that moved the post above specific competing posts
  produced no change in apply-start rate. See the qualifying change test in `baselines.md`. A
  raise that left the post in the same competitive position, or that was never re-surfaced,
  never tested this branch and is not evidence against it.

### 2B. Work model unstated or ambiguous

- **Signature:** normal impressions, low view-to-apply-start. The post says "remote" with an
  unstated location requirement, or "hybrid" without a day count, or gives a city with no
  statement either way. Comparison requisitions stating an explicit model convert at baseline.
- **Rules it out:** the model is stated unambiguously and the drop persists.

### 2C. The body reads as a different level than the title

Candidates self-deselect because the scope described does not match the seniority advertised.

- **Signature:** normal impressions, low apply-starts, and the mismatch is visible in the post:
  a senior title over responsibilities that read as execution-only, or a mid title over scope
  that reads as leadership.
- **Rules it out:** title and described scope are consistent, or apply-starts are at baseline.
- **Note:** this and **4A** are the same defect at two different stages, with opposite
  fingerprints. At Stage 2 a misleading signal **suppresses** application, because the people it
  is for read it and leave. At Stage 4 it **attracts**, because a different population reads it
  and applies. Which one you have depends on whether the signal reads as too big or too small
  for the audience it reached, and the volume figure tells you which.

### 3A. Form length or account requirement

- **Signature:** apply-starts at baseline, submissions materially below. Drop-off concentrates
  at a specific field or page. Comparison requisitions with shorter forms convert at baseline.
- **Rules it out:** completion rate inside the comparison range.

### 3B. Redirect or handoff failure

- **Signature:** drop-off concentrated at the handoff between board and applicant tracking
  system. The completion rate **differs sharply by channel**, because only some channels
  redirect. Error reports or dead links on one path.
- **Rules it out:** completion rate uniform across channels.

### 3C. Materials demanded before any conversation

- **Signature:** drop-off at an upload, a take-home, or a long free-text step. Comparison
  requisitions that defer these convert at baseline. Effect is strongest at senior levels, where
  the candidate is not job-hunting full time.
- **Rules it out:** required materials comparable to the set and completion still low.

---

## Stage 4 — Break at screening pass

Volume arrived and it was the wrong volume. This is the case the hiring conversation calls
"unqualified applicants."

Everything here runs on **aggregate counts the employer's own screening produced**. No entry in
this stage is established by reading a submission.

### 4A. Requirement signaling

The stated requirements read as a different job than the one being hired for, so a different
population self-selects in.

- **Signature:** submissions at or above baseline, pass proportion materially below. The pass
  failures **concentrate on one or two must-haves** rather than spreading. The requirement block
  foregrounds attributes shared with a neighbouring job family — tools, surfaces, or
  responsibilities — and buries or omits the ones that define this role.
- **Rules it out:** pass failures spread evenly across the stated requirements, or the pass rate
  varies sharply by channel.

### 4B. Channel-population mismatch

The post is fine and it is being distributed into a population that does not contain the target.

- **Signature:** submissions at or above baseline, pass proportion materially below, and the
  **pass rate varies sharply between channels** — one channel supplying most of the volume and
  almost none of the passes while the others sit at baseline.
- **Rules it out:** pass rate uniform across channels.
- **Does NOT separate it from 4A:** the pooled pass rate, or the size of the pile. Both 4A and
  4B produce high submission volume with a low pass proportion, so "two hundred applications and
  eleven worth reading" is consistent with either. **Variance across channels decides, not the
  aggregate.** A channel problem concentrates, because the population differs per channel. A
  signaling problem is uniform, because the post says the same thing everywhere. Read the spread,
  not the pooled rate.

> **General form of that rule.** When two causes in the same stage produce the same count on
> the same measure, that count screens them in together and cannot rank them. Find the property
> that differs between the two and read that instead. A count that both hypotheses predict is
> not a discriminator.

### 4C. Must-haves not marked as must-haves

Everything is listed at one level, so candidates cannot self-select.

- **Signature:** high volume, low pass, failures concentrating on one or two requirements that
  sit undifferentiated in a long list with no required-versus-preferred separation.
- **Rules it out:** the post separates required from preferred and the failures still
  concentrate, which points to 4A instead.
- **Note:** 4A and 4C are close and the difference is actionable. In 4A the requirement is
  stated and describes the wrong job. In 4C the requirement is stated, describes the right job,
  and is invisible in the noise.

### 4D. Screening rule and post disagree

The screen is applying a criterion the post does not state.

- **Signature:** the pass failures concentrate on something absent from the post — a degree, a
  years floor, a named tool, an industry — visible by comparing the written screening rules
  against the published requirements.
- **Rules it out:** every criterion in the screening rules appears in the post.
- **Note:** this is the one cause in the taxonomy where the finding is about the screen rather
  than the post, and it is worth separating, because **"unqualified applicants" and "applicants
  who did not meet a rule nobody published" are different findings with different owners.** The
  finding is about the rule as written and its disagreement with the post. It is never about the
  judgment of the person applying it, and no finding is written about a named person.

---

## Stage 5 — Break at interview conversion

Screened-in candidates did not convert to a conversation, or had one and left. The post did its
job. Something after it did not.

Withdrawal reasons are read as **aggregate patterns about the post and the process**. They are
not evaluations of the people who withdrew and the report does not characterize them.

### 5A. Scope divergence

The conversation describes a job the post did not.

- **Signature:** withdrawals cluster immediately after first contact. Aggregate reasons name
  scope, level, team size, or responsibilities. The post's title or described scope does not
  match what the conversation covers.
- **Rules it out:** withdrawals spread across the loop rather than clustering at first contact.

### 5B. Work-model or location divergence

- **Signature:** withdrawals cluster on onsite days, relocation, or time zone. The post read
  remote or hybrid and the role is not, or the location was nominal. Comparison requisitions
  with explicit models do not show the drop.
- **Rules it out:** the model was explicit in the post and matches what is described.

### 5C. Compensation, post-conversation

They liked the role and will not take that number.

- **Signature:** aggregate withdrawal reasons name compensation. Comparison requisitions at
  higher bands convert at baseline. Frequently paired with a post that stated no range, or a wide
  one whose actual offer sits at the bottom, so the mismatch surfaced late.
- **Weakens it:** a **qualifying** raise of sufficient magnitude with no corresponding change in
  conversion.
- **Note:** this is the branch where a magnitude raise is the matching intervention. Confirm it
  here rather than assuming it at Stage 1, where the same word describes a completely different
  mechanism.

### 5D. Process friction

- **Signature:** withdrawals cluster by **elapsed time** rather than by content. Long gaps
  between submission and first contact, scheduling delays, or a loop whose length is disclosed
  late. Comparison requisitions with faster first contact convert at baseline.
- **Rules it out:** time-to-first-contact inside the comparison range.

---

## Outside the funnel — Not a post failure

- **Referrals, internal transfers, and sourced candidates** who never saw the advertisement. A
  requisition filled by referral tells you nothing about the post, and leaving these in inflates
  every rate in the analysis.
- **Post-offer.** Offers extended and declined, or accepted and reneged. That is a compensation,
  competing-offer, or process failure after the post did its job. Say plainly that the constraint
  moved past the advertisement.
- **Requisition changed mid-window.** Cancelled, frozen, re-scoped, or backfilled. The subject is
  not stable and the funnel cannot be pooled across the change.

---

## The null: thin local pool

Nothing is wrong with this post.

- **Signature:** reach at baseline, so the post is being served. The comparison set's qualified
  volume is low **across the whole set**, not uniquely low for the subject. The subject's
  per-stage figures track the comparison baseline at every stage. Days open across the set has
  risen relative to prior cycles for the same roles.
- **Rules it out:** comparison requisitions at the same band, location, and work model producing
  normal qualified volume while the subject does not.

A requisition performing at market in a thin market is not a requisition with a problem. A raise
here resets the floor for every future hire at that level and does not produce a candidate who
does not exist, because the constraint is not this post.
