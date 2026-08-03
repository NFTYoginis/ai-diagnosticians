# Changelog

## Listing Stall Diagnostician

### v0.2

External review found that several diagnostic heuristics were written as if they were
causal proofs. That is the exact failure this folder exists to catch, so the corrections
are the substance of this release rather than polish on top of it.

**Corrected**

- **Price mechanisms.** The prior claim that only post-visit value judgment is addressable
  by a reduction was false. Crossing a search threshold *is* a reduction. Rewritten: a
  reduction can address any of the three mechanisms, and what differs is the kind of
  reduction each one requires. A threshold needs a crossing and magnitude below it is
  irrelevant. Comparison needs landing below specific competitors. Value judgment needs
  magnitude.
- **Reduction falsification, six instances.** Every claim that an unresponsive price cut
  falsifies price was unconditioned. Replaced with a **qualifying reduction test** in
  `reference/baselines.md`: material position change or threshold crossing, listing
  otherwise unchanged, sufficient observation window, stable market. All four must hold.
  A non-qualifying reduction is now reported as uninformative, which is no evidence in
  either direction rather than weak evidence for the null.
- **Comparison set language.** Comps were described as holding the environment constant.
  They do not. Reworded throughout as a natural comparison baseline that reduces
  confounding without eliminating it, with the residual differences named.
- **Removed an invented prevalence claim.** The README asserted price is not the cause
  "roughly half the time." No such measurement exists and the repo simultaneously states
  the system is unvalidated.
- **Landing page CTA.** "See a real output" pointed at constructed teaching cases.
  Now "See a worked diagnosis."

**Added**

- **Second showings as a canonical funnel stage.** Previously the worked cases turned on
  the figure while the formal funnel had no stage for it. The funnel is now five stages
  everywhere: views, engagement, showings, second showings, offers. A first showing is a
  judgment about the listing; a second is a judgment about the house.
- **Comparison-set integrity check** as Step 0.5, returning Usable, Usable with
  limitations, or Not usable. Limitations cap confidence at Provisional.
- **Three-level diagnosis:** constraint (where), cause (why), mechanism (how). Prevents
  presenting a mechanism and its category as competing causes.
- **Confidence caps made binding.** An untestable null caps at Provisional regardless of
  how clean the rest is, because the leading alternative was never examined.
- Regression tests in `tests/`, stated as minimum assertions rather than expected prose.
- License, version, and this changelog.

**Rejected from review, with reasons**

- **A six-stage funnel with search exposure and transaction survival as stages.**
  Impressions are unobtainable for most agents, so a formal exposure stage would sit
  empty in nearly every case and the starved-stage rule would misfire on a blank row.
  Impressions remain optional evidence inside Stage 1. Post-offer failure is a
  transaction failure, not a listing failure, and is deliberately routed outside the
  funnel to keep that boundary legible.

**Still open**

- **Retrospective field validation.** Requires funnel data that is agent-side rather than
  public. A retrospective run on public MLS history alone would correctly return
  Undetermined for want of Step 2 inputs. Options are a real anonymized case supplied with
  permission, or a public run that returns Undetermined and demonstrates the refusal
  behavior on a live listing. Neither has been done. The validation column in the root
  README says so.

### v0.1

Initial build. Identity, rules, three worked examples, failure-mode taxonomy, baseline
construction, intake spec, landing page.
