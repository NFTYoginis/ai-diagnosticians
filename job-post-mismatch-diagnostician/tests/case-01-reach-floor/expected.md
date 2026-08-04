# Case 01 — expected

Minimum assertions. Wording will vary. Every assertion must hold.

## Must assert

- [ ] **Failure confirmed.** 19 submissions and 38 days open are identified as below the comparison
      ranges (186 to 310 submissions, 14 to 31 days open).
- [ ] **Comparison-set integrity is stated**, and requisition 5 is named as a limitation on account
      of triple sponsorship spend, or excluded from the reach baseline. The report must say the
      reach baseline is drawn from four.
- [ ] **Primary constraint is Stage 1, reach.** Not screening pass, not application.
- [ ] Subject impressions are compared against the comparison range and identified as below the
      lowest, not below the average.
- [ ] **Primary cause is compensation filter floor**, referencing the $92,000 lower bound sitting
      under a $100,000 filter increment.
- [ ] **The mechanism turns on lower-bound indexing.** The report must state that the boards index
      on the range's lower bound, so a $104,000 top does not rescue a $92,000 floor. A mechanism
      written as "the role is underpaid" is wrong even if the constraint is right.
- [ ] **The filter documentation is attributed as a supplied input**, not asserted as general
      knowledge about job boards.
- [ ] **The channel split is used as the discriminating evidence.** The deficit is confined to the
      two channels with a salary floor filter; the careers page sits inside its comparison range.
- [ ] **Pass-through is computed and used.** The 3.8% view rate sits inside the comparison range of
      3.2% to 5.1%, so the deficit is volume rather than performance. The report must draw that
      distinction explicitly.
- [ ] **Downstream stages are explicitly declared uninformative.** The report must say no
      conclusion is drawn about the requirement list, the body copy, or who the post attracts.
- [ ] **Nineteen submissions is named as not a readable sample**, and the 2-of-19 pass figure is
      not treated as a pass rate.
- [ ] **Title mismatch is ruled out** using comparison requisitions 1, 3 and 5 sharing the title
      family and showing baseline impressions.
- [ ] **Sponsorship exhaustion, expiry, and de-ranking are ruled out** using equal spend, the flat
      impression series with no cliff, and both boards showing the post live and in-index for 38
      days.
- [ ] **Comparison requisition 3 is read correctly**: it shares the subject's original lower bound
      and was republished with a corrected range, so its baseline figures are not evidence that a
      $92,000 floor performs normally. If the report cites requisition 3 as a counter-example
      against the floor hypothesis, that is a fail.
- [ ] **Null is tested and rejected**, citing four of five comparison requisitions drawing 11,400
      to 19,800 impressions per week on the same channels and four filling inside the window.
- [ ] **Absence of a prior change is noted** as no completed experiment being available, rather than
      passed over silently.
- [ ] Confidence is **Provisional**, tied to the reach baseline resting on four after the spend
      exclusion and to the absence of search-appearance data.

## Must not

- [ ] **Does not answer the question the team asked.** The request is "are the requirements scaring
      people off, should we cut the list" and the report must not assess the requirement list,
      because that stage is starved.
- [ ] Does not diagnose requirement signaling as primary. May list it as untested and live once
      visibility is resolved.
- [ ] Does not suggest a band, a figure, a percentage, or a target.
- [ ] Does not suggest rewriting the post, cutting requirements, changing channels, or republishing.
- [ ] Does not treat the two passing submissions as evidence about anything.

## Drift signal

If the constraint lands anywhere other than Stage 1, the starved-stage rule in `rules.md` has
stopped binding. That is the single most important thing this case guards.

If the mechanism is written as the role being underpaid rather than being indexed below a filter
increment, the three-mechanism split for compensation in `rules.md` Step 4 has collapsed. The
constraint would be right and the finding would still be useless, because the two call for
completely different responses and only one of them is cheap.
