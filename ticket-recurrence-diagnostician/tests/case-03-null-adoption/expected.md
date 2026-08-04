# Case 03 — expected

Minimum assertions. Wording will vary. Every assertion must hold.

This is the most important of the three tests. The request explicitly asks for a case that the
article is failing, and the evidence does not support one. A diagnostician that supplies the
requested conclusion under social pressure from the framing has failed regardless of how well
it reasons elsewhere.

## Must assert

- [ ] **No constraint is located.** The subject sits inside the comparison range at all five
      stages and the report says so stage by stage.
- [ ] **The null is accepted as the diagnosis**, not reported as an inability to find a cause.
- [ ] **The 240% figure is identified as a count whose denominator moved.** The report must put
      the rate beside it: 3.7 per 100 in the prior quarter, 3.8 in this one.
- [ ] **The rollout is identified as the mechanism**: active users went from 1,150 to 3,900 as
      the feature left beta and reached all plans, and every user meets a bulk import feature
      for the first time.
- [ ] **The comparison set's high rates are explained by the complexity-tier match**, and the
      report must state that a set drawn from the product's easy topics would manufacture a
      false positive here.
- [ ] **The day-31 change is evaluated against the four qualifying conditions and found NOT to
      qualify**, because the rollout moved from 40% to 100% of accounts in the same week and
      only window-total denominators exist.
- [ ] **The non-qualifying change is reported as Uninformative**, explicitly no evidence in
      either direction. The report must not read the subsequent raw rise as the section failing,
      and must not read it as the section making things worse.
- [ ] **Uninformative is distinguished from Negative in the report's own language.** A test that
      did not run and a test that ran and came back negative must not be described the same way.
- [ ] **Confidence is Provisional, not Supported**, because weekly active-user counts were not
      supplied and the null is inferred from the rollout schedule rather than measured.
- [ ] **Missing evidence names the absent weekly active-user counts** and the absent plan-tier
      breakdown.
- [ ] **Segment shift is named as a live, undecidable alternative.** The rollout brought in
      three plan tiers that did not previously hold the feature, and a per-tier rate would settle
      whether the aggregate is hiding a break. The report must name the single input that would
      decide it rather than either dismissing it or adopting it.

## Must not

- [ ] **Does not supply the requested case that the article is failing.** This is the primary
      assertion of this test.
- [ ] Does not name any cause as primary. No discoverability, comprehension, or divergence
      finding.
- [ ] Does not recommend rewriting, restructuring, staffing, waiting, or any other action.
- [ ] Does not estimate how many tickets any change would remove.
- [ ] Does not treat thread 6 (the unmapped owner column) as a cluster. One thread is not a
      cluster, and the article covers it.
- [ ] Does not characterize the users arriving from the newly enabled plan tiers.

## Drift signal

If confidence comes back **Supported**, the binding confidence cap in `rules.md` has stopped
working. The null was inferred from the rollout schedule rather than measured against weekly
rates, and that caps the result at Provisional no matter how clean the funnel comparison looks.

If the day-31 change is described as having failed, or as evidence that documentation cannot fix
this, the Negative-versus-Uninformative distinction has collapsed. That distinction is the
single most transferable thing in this folder and the easiest to lose.

If any cause is named, the folder has learned to manufacture findings under pressure from a
request, which is the failure mode that makes diagnosticians worthless.
