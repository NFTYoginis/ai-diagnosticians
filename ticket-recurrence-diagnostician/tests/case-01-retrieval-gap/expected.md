# Case 01 — expected

Minimum assertions. Wording will vary. Every assertion must hold.

## Must assert

- [ ] **Failure confirmed.** 5.6 tickets per 100 active users is identified as beyond the
      comparison range (0.70 to 1.90). The comparison must be on the **rate**, not on the raw
      count of 34.
- [ ] **Comparison-set integrity is stated**, with two things named: billing contacts as a
      consequence-tier limitation, and search-log coverage existing for only five of the seven
      topics. The retrieval baseline must be identified as drawn from five.
- [ ] **Primary constraint is Stage 2, retrieval.** Not reach, not comprehension.
- [ ] **Reach is identified as at baseline** and used as the evidence that this is a retrieval
      finding rather than a reach finding. 44 sessions per 100 sits inside 26 to 51.
- [ ] **Primary cause is vocabulary mismatch in the index**, referencing the article's *move*
      and *workspace* against the queries users actually type.
- [ ] **Mechanism is stated separately from cause** and connects the product's rename of the
      control to **Transfer** with the article's stale vocabulary. It must describe the article
      being filed under a name the product no longer uses, not the article being badly written.
- [ ] **Downstream stages are explicitly declared uninformative.** The report must say that no
      conclusion is drawn about whether the article's instructions are clear, complete, or
      correct, because 4 of 34 threads show any contact with it.
- [ ] **Search or indexing defect is ruled out** using the fact that the article returns at
      position one for its own exact title.
- [ ] **The query distribution is used as direct evidence**: the high-volume phrasings share no
      content word with the article's title, and the two phrasings that do share one both
      returned and opened it.
- [ ] **Naming drift at Stage 5 is named as live but not concluded.** The same stale noun in
      step 3 would break inside the procedure if readers reached it. The report must say it is
      starved and untested rather than either concluding it or ignoring it.
- [ ] **Null is tested and rejected**, citing flat adoption (598 to 610) against a rising ticket
      count, and the comparison set's steady rates.
- [ ] **Absence of a prior documentation change is noted** as no completed experiment being
      available, rather than passed over silently.
- [ ] Confidence is **Provisional**, tied to the retrieval baseline resting on five of seven
      comparison topics.

## Must not

- [ ] **Does not answer the question the team asked.** The request is "is the article unclear,
      should we rewrite it" and the report must not assess the article's clarity, because that
      stage is starved.
- [ ] Does not diagnose comprehension as primary. May note it as untested and live once
      retrieval is resolved.
- [ ] Does not suggest a new title, keywords, synonyms, or any replacement text.
- [ ] Does not treat thread 9 as evidence about the procedure. One thread reaching step 3 is not
      a readable sample and the report should say so if it cites it.
- [ ] Does not recommend re-indexing, retitling, or any other action.

## Drift signal

If the constraint lands anywhere other than Stage 2, the starved-stage rule in `rules.md` has
stopped binding. That is the single most important thing this case guards.

If the report assesses the article's writing quality, the folder has answered the question it
was asked instead of the question the evidence can support, which is the same failure in a
politer form.
