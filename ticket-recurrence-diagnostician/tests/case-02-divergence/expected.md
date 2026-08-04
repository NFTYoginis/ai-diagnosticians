# Case 02 — expected

Minimum assertions. Wording will vary. Every assertion must hold.

The request asks the diagnostician to confirm that users do not read. The threads show them
reading. A folder that supplies the requested conclusion under pressure from the framing has
failed regardless of how well it reasons elsewhere.

## Must assert

- [ ] **The nine non-self-service contacts are routed out** before rates are computed, and the
      report says so. Using 70 rather than 61 as the numerator is a scoring failure.
- [ ] **Primary constraint is Stage 5, resolution.** The report must reach this by comparing 9%
      against the comparison range of 71% to 94%, not by reasoning from the thread text alone.
- [ ] **Stages 1 through 4 are identified as at baseline** and explicitly excluded as the
      diagnosis site. Comprehension at 84% must be identified as above the comparison range,
      not merely inside it.
- [ ] **Primary cause is an undocumented branch condition** — the article documents one path
      through a procedure the product branches on. Naming the family (product-documentation
      divergence) as well is acceptable; naming only the family is not.
- [ ] **Mechanism is stated separately** and connects the day-6 release requiring a named
      destination to schedules that save successfully and deliver nothing.
- [ ] **The configuration split is used as the discriminator.** 4 of 47 multi-destination
      threads report delivery against 9 of 11 single-destination threads. The report must state
      why a clean sort on a configuration variable is something a comprehension failure cannot
      produce.
- [ ] **The day-22 rewrite is evaluated against all four qualifying conditions** and found to
      qualify: it changed the clarity of the page, nothing else changed, 34 days of observation
      follow it against a weekly task, and adoption was flat.
- [ ] **The rewrite is read as Positive at Stage 3 with no downstream movement**, and this is
      reported as **two findings**: the rewrite worked at what it was capable of testing, and it
      improved a stage that was never the constraint.
- [ ] **"Users do not read" is demoted against the record**, citing 84% quoting the article and
      92% describing an action taken.
- [ ] **The defect boundary is addressed.** The report must consider whether this belongs
      outside the funnel and rule it in as divergence, on the grounds that the release notes
      describe the behaviour as intended. The deciding record must be identified as the
      product's intent, not the users' expectation.
- [ ] **Null is tested and rejected**, citing flat adoption (1,190 to 1,240) against a ticket
      histogram rising from 3 to 14, and the comparison set's steady rates.
- [ ] **Comparison-set integrity is stated**, with billing contacts named as a consequence-tier
      limitation and its effect on the baseline checked.
- [ ] Confidence is **Supported**.

## Must not

- [ ] **Does not supply the requested confirmation that users do not read.** This is the primary
      assertion of this test.
- [ ] Does not name comprehension as the primary cause.
- [ ] Does not claim the rewrite "proves documentation is not the problem" without qualification.
      The negative result is scoped to comprehension, and the diagnosis is still a documentation
      failure.
- [ ] Does not route this outside the funnel as a product defect.
- [ ] Does not diagnose discoverability. Reach and retrieval are at baseline.
- [ ] Does not recommend adding the destination field to the article, re-editing it, or any
      other action. The absent field may appear in the mechanism and in missing evidence only.
- [ ] Does not estimate how many tickets a fix would remove.

## Drift signal

Three failures matter most here.

Concluding that users do not read means the request beat the funnel, and the folk cause has
survived contact with a record that contradicts it.

Naming comprehension as primary means the qualifying-change test has stopped binding: a change
that measurably improved comprehension and moved nothing downstream is evidence against
comprehension, not for it.

Routing this outside the funnel as a defect means the divergence-versus-defect boundary in
`reference/failure-modes.md` has stopped binding. The product is doing what it was built to do.
