# Regression tests

Each case folder holds an `inputs.md` you paste into a project running this folder, and an
`expected.md` listing the **minimum assertions** the output must satisfy.

Assertions, not expected prose. Model updates change wording constantly and would break a
literal-match test every release while telling you nothing. What must not drift is where the
diagnostician locates the constraint, what it demotes, whether it tests the null, and whether
it stays inside its refusal boundaries.

## Running one

1. Open a Claude Project with this diagnostician's folder loaded.
2. Paste the contents of `inputs.md`.
3. Say: `Diagnose this ticket pattern.`
4. Check the output against every assertion in `expected.md`.

A test fails if any assertion fails. Record which one, since that identifies the file that
drifted.

## The cases

| Case | Tests | The failure it guards against |
|---|---|---|
| [case-01-retrieval-gap](case-01-retrieval-gap/) | Stage 2 break, vocabulary matching mechanism, downstream stages declared uninformative | Diagnosing the article's writing when almost nobody opened it |
| [case-02-divergence](case-02-divergence/) | Stage 5 break, qualifying rewrite read as a positive at a stage that was not the constraint, mechanism separated from cause | Concluding that users do not read, when the threads show them reading |
| [case-03-null-adoption](case-03-null-adoption/) | Null accepted, non-qualifying change reported as uninformative, no recommendation issued | Manufacturing a cause from a raw count whose denominator moved |

## Boundary assertions that apply to every case

These are checked on all three outputs and are the most common way a folder like this degrades:

- No rewritten documentation, replacement steps, suggested title, headings, or search terms
- No prospective volume, deflection, or cost figure anywhere
- No recommended action, including hedged forms such as "consider" or "you may want to"
- No ranked list of improvements
- No statement about an individual support agent's performance or handling
- No characterization of an individual user's competence, attention, or care
- Report uses the exact headings from the output contract in `rules.md`, in order
- Confidence is exactly one of Supported, Provisional, Undetermined
