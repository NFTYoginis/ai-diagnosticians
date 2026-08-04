# AI Diagnosticians

Folder-based Claude Projects that work out **why** a recurring professional failure
happened, using documents already produced during the work.

A diagnostician is not an editor and not an auditor. An editor improves a draft. An
auditor lists everything wrong. A diagnostician works backward from something that
already failed in the real world and names the one cause the evidence supports, shows
how it got there, and stops before prescribing anything.

**Landing page:** https://nftyoginis.github.io/ai-diagnosticians/

---

## In this repo

| Diagnostician | Diagnoses | Version | Validation |
|---|---|---|---|
| [listing-stall-diagnostician](listing-stall-diagnostician/) | Why a specific real estate listing hasn't sold, and whether price is actually the cause | v0.4 | Three independent blind runs, all passed. Regression assertions in [tests/](listing-stall-diagnostician/tests/). **No retrospective field validation yet.** |
| [ticket-recurrence-diagnostician](ticket-recurrence-diagnostician/) | Why support tickets keep arriving for something the documentation already covers | v0.1 | Structure verified against the reference. **Never run. No blind runs yet.** |
| [job-post-mismatch-diagnostician](job-post-mismatch-diagnostician/) | Why a job post draws applicants but not qualified ones | v0.1 | Structure verified against the reference. **Never run. No blind runs yet.** |

The validation column is the point of the table. Only the first folder has been put in
front of readers who did not build it, and the other two have not been run once. They are
not being presented as equivalent.

Further diagnosticians in the same architecture are in progress. Each will carry its own
validation status in this table rather than borrowing credibility from the others.

---

## The method

Every diagnostician in this portfolio runs the same sequence.

1. **Confirm the failure is real.** Compare against a baseline before assuming anything
   broke. A great deal of what gets called failure is normal variation measured against
   a stale expectation.
2. **Build the comparison set, then test whether it holds.** Diagnosis needs a baseline.
   The strongest domains have one occurring naturally in the work: comparable listings,
   other answers to the same question, resolved versus recurring tickets. Then check the
   set's integrity before trusting it, and say whether it is usable, usable with named
   limitations, or not usable. A rigorous-sounding diagnosis on a weak comparison set is
   the most likely way one of these produces a confident wrong answer.
3. **Locate the break.** Find the earliest stage where the subject falls below that
   baseline. Everything downstream of a break is starved and therefore uninformative.
   This is what separates a diagnosis from a list.
4. **Discriminate.** Within the break, at least two causes are live. Separate them with
   evidence. If the record would look identical whether a cause were true or false, that
   cause is not decidable and must be reported as such rather than chosen.
5. **Test the null.** Attempt to reject your own diagnosis. *Nothing is meaningfully
   broken* is a legitimate and frequently correct answer.
6. **Name one, at three levels.** *Constraint* is where it breaks. *Cause* is why it
   breaks there. *Mechanism* is how that cause produces this specific pattern. Flattening
   them yields a finding that sounds rigorous and cannot be acted on. Everything else is
   demoted to downstream-of-the-primary or not-supported-by-this-evidence.
7. **Stop.** State confidence, missing evidence, and what would prove the diagnosis
   wrong. Do not prescribe.

## What makes a domain qualify

- **Recurrence.** A folder is infrastructure. Nobody builds infrastructure for a failure
  they hit once every three years.
- **Documentary-native evidence.** The evidence must already exist as documents produced
  during the work. If the user has to write a retrospective account of what happened, the
  diagnostician is reading a story authored by the person who is already wrong about the
  cause.
- **A natural comparison set.** Preferably within-case, where the environment is largely
  shared and the outcome varies. A comparison baseline reduces confounding. It is not an
  experimental control, and writing it up as one turns a strong baseline into a false
  proof.
- **Competing hypotheses that need different evidence.** If one explanation always wins,
  there is nothing to diagnose.
- **A loud folk cause.** The value is in converting the reflex answer into a hypothesis.
- **A bounded subject**, stated as a rule. The listing diagnostician evaluates listing
  performance, not the homeowner.

## Shared file structure

```
<diagnostician>/
├── README.md        how to use it, what to feed it
├── identity.md      who it is, what it diagnoses, what it refuses
├── rules.md         the method and the output contract
├── examples.md      worked cases, including at least one null
└── reference/       failure modes, baselines, intake spec
```

Every folder runs this structure with only the domain knowledge swapped, which is what
makes the claim that the method transfers checkable rather than asserted. Diff any two.

---

## Honesty notes

The worked examples are constructed teaching cases with figures chosen to make each
discriminator legible. They are not client files.

There are no industry-average benchmarks anywhere in this repo. Rates and baselines vary
too much by market, segment, and period for a quoted average to be anything other than
wrong in most contexts while being treated as authoritative. Every baseline is computed
from the comparison set supplied with the case.

Built for [Weekly Comp #10: The Diagnostician](https://www.skool.com/).
