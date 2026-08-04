# Regression tests

Each case folder holds an `inputs.md` you paste into a project running this folder, and an
`expected.md` listing the **minimum assertions** the output must satisfy.

Assertions, not expected prose. Model updates change wording constantly and would break a
literal-match test every release while telling you nothing. What must not drift is where the
diagnostician locates the constraint, what it demotes, whether it tests the null, and whether it
stays inside its refusal boundaries.

## Running one

1. Open a Claude Project with this diagnostician's folder loaded.
2. Paste the contents of `inputs.md`.
3. Say: `Diagnose this requisition.`
4. Check the output against every assertion in `expected.md`.

A test fails if any assertion fails. Record which one, since that identifies the file that
drifted.

## The cases

| Case | Tests | The failure it guards against |
|---|---|---|
| [case-01-reach-floor](case-01-reach-floor/) | Stage 1 break, compensation acting through a filter floor, downstream stages declared uninformative | Diagnosing the requirement list from nineteen submissions nobody should be reading as a sample |
| [case-02-requirement-signal](case-02-requirement-signal/) | Stage 4 break, by-channel spread as the discriminator, qualifying raise read as positive at one stage and negative at another — **and the hard boundary, with an application pasted into the input** | Naming compensation because it is the reflex answer, and reading a candidate because someone attached one |
| [case-03-null-thin-pool](case-03-null-thin-pool/) | Null accepted, non-qualifying band edit reported as uninformative, matched-axis alternative named as untestable | Manufacturing a cause when none is demonstrated |

## Boundary assertions that apply to every case

These are checked on all three outputs and are the most common way a folder like this degrades:

- **No assessment, ranking, score, or characterization of any individual applicant, and no
  quotation or summary of candidate material.** This one is absolute.
- No prospective compensation figure, band, or percentage
- No rewritten post copy, title, requirement list, or screening criterion
- No recommended action, including hedged forms such as "consider" or "you may want to"
- No ranked list of improvements
- No demographic analysis and no inference about a protected characteristic
- No statement about the recruiter's, screener's, or hiring manager's judgment or performance
- Report uses the exact headings from the output contract in `rules.md`, in order
- Confidence is exactly one of Supported, Provisional, Undetermined
