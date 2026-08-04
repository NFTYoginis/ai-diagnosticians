# Failure modes

Organized by funnel stage, because the stage where the sequence breaks determines which
causes are even eligible. Each entry gives the signature that distinguishes it, and the
counter-signature that rules it out.

---

Canonical funnel, used throughout: **1. Reach · 2. Retrieval · 3. Comprehension ·
4. Execution · 5. Resolution.** Stages 1 and 2 are the **discoverability** family. Stage 3 is
**comprehension**. Stages 4 and 5 are **product-documentation divergence**. Contacts that
were never self-service attempts are outside the funnel.

---

## Stage 1 — Break at reach

They never arrived at a documentation surface. Nothing about the article itself is in
evidence yet.

### 1A. No in-product entry point

The task happens on a screen that does not link to the documentation, so the only users who
find it are the ones who thought to go looking.

- **Signature:** article pageviews per active user far below comparison topics. Comparison
  topics that perform well are linked from their own surface. Threads contain no evidence of
  any documentation contact. Users describe searching inside the product rather than the help
  center.
- **Rules it out:** pageviews per active user at or above comparison baseline.
- **Note:** cheap to check, and it silently caps every downstream measure. Check it before
  anything interpretive.

### 1B. Absent from the product's own search

Users type the question into the product, not the help center, and nothing surfaces.

- **Signature:** in-product search logs, where available, show the query firing with no help
  result attached. Help-center sessions on the topic arrive overwhelmingly from external
  search rather than from the product.
- **Rules it out:** the topic surfaces in product search at parity with comparison topics.

### 1C. Locale or segment gap

The article exists in one language, or sits behind a plan tier the affected users do not
hold.

- **Signature:** ticket concentration by locale or plan that does not match adoption by locale
  or plan. A topic drawing 40% of its tickets from a locale holding 8% of its active users is
  not a comprehension finding.
- **Rules it out:** coverage matches the adopting population on both axes.

### 1D. Documentation published after the users needed it

- **Signature:** ticket dates cluster before the article's publication date, or before the
  date it was linked from the product.
- **Rules it out:** the article and its entry point both predate the ticket window.
- **Note:** this is the one cause in the taxonomy that resolves itself, and it is worth
  separating so a team does not spend a cycle fixing something already fixed. Check publication
  and link dates against the ticket histogram before reading anything else.

---

## Stage 2 — Break at retrieval

They came looking and did not land on it. What is in evidence: titles, indexing, and the
shape of the help center. What is not in evidence: whether the instructions work, because
almost nobody reached them.

### 2A. Vocabulary mismatch in the index

The article is written in the product's nouns and users search in their own. This is
vocabulary acting through the **matching** mechanism — see the three mechanisms in
`rules.md` Step 4.

- **Signature:** help-center search logs show high query volume on the users' phrasing ending
  in zero-result or no-click outcomes. The article's title and opening paragraph use terms
  absent from those queries. Comparison articles that perform well share vocabulary with the
  queries that reach them.
- **Rules it out:** queries on the topic return the article and it is opened at comparison
  rates.
- **Note:** where the product has renamed a control and the article has not caught up, the
  same stale noun is live at Stage 5 as well, by a different mechanism. Do not conclude about
  Stage 5 from a Stage 2 break. Note that it would be live and leave it untested.

### 2B. The answer is buried inside a broader article

- **Signature:** the topic has no article of its own. The procedure sits in section seven of a
  page about something else. Pageviews on the parent page are normal while the topic still
  generates tickets, and threads reference the parent page without reaching the section.
- **Rules it out:** a dedicated article exists and is retrieved at comparison rates.

### 2C. Near-duplicate articles splitting the click

- **Signature:** several articles cover overlapping ground, search returns three, pageviews
  distribute across them, and completion is low on each. Threads quote different articles for
  the same question.
- **Rules it out:** one canonical article, with the others redirected or consolidated.

### 2D. Search or indexing defect

- **Signature:** the article is not returned for its own exact title. Recently published or
  recently edited articles are absent from results. Comparison topics are unaffected.
- **Rules it out:** the article returns for its own title and for the top queries on the topic.
- **Note:** distinguish this from 2A before concluding. An indexing defect breaks retrieval for
  queries that *should* match. A vocabulary mismatch breaks retrieval for queries that never
  matched in the first place. The test is whether the article returns for its own title.

---

## Stage 3 — Break at comprehension

They opened it and wrote in anyway. What is in evidence: everything on the page. What is not
in evidence: whether the steps actually work, because nobody got far enough to find out.

### 3A. Instructional gap

A step, a prerequisite, or a branch is missing from the procedure.

- **Signature:** threads quote the article and stop at a specific point. "I'm at step 3, then
  what." "It says to open Settings but there's no tab there." The quotes cluster on the
  **last step the reader completed**.
- **Rules it out:** threads quote the article and dispute a term rather than a position.

### 3B. Vocabulary mismatch on the page

The article's nouns do not map onto what the reader is looking at. This is vocabulary acting
through the **translation** mechanism.

- **Signature:** threads quote a **term** and ask what it refers to, or ask whether the thing
  in front of them is the thing named. "Is 'workspace' the same as my account." "What counts
  as a connected destination."
- **Rules it out:** threads locate themselves in the procedure without disputing what anything
  is called.
- **Does NOT separate it from 3A:** the count of threads quoting the article. Both 3A and 3B
  produce a cluster on the same article and both produce readers who quote it, so eleven of
  fifteen quoting the export page is consistent with either. **Position decides, not count.**
  A 3A quote advances to a place in the procedure and stops there. A 3B quote attaches to a
  noun and asks what it is. A reader blocked by a missing step knows where they are and not
  what comes next. A reader blocked by vocabulary knows what comes next and not where they
  are. Read where the quote lands, not how many there are.

> **General form of that rule.** When two causes in the same stage produce a cluster on the
> same artifact, the clustering count screens them in together and cannot rank them. Find the
> property that differs between the two and read that instead. A count that both hypotheses
> predict is not a discriminator.

### 3C. Written for a different entry path

The procedure assumes the reader arrived from a place they did not.

- **Signature:** threads describe starting somewhere else — a different menu, a different
  object, a mobile client, an admin console rather than the workspace. Step 1 does not match
  where the reader is standing.
- **Rules it out:** threads follow the documented path and break later in it.

### 3D. No worked example where the task branches

- **Signature:** the article states the rule abstractly and the task has cases. Threads ask
  which case applies to them rather than what the steps are. Comparison articles for similarly
  branched tasks carry an example and draw fewer tickets.
- **Rules it out:** an example covering the common case is present and threads still break
  elsewhere.

---

## Stages 4 and 5 — Break after the reader acts

They understood the article and did what it said. The documentation communicated. Something
about the product did not match it.

**4A and 4B are Stage 4 causes** and show up as readers who cannot start. **5A, 5B, and 5C are
Stage 5 causes** and show up as readers who finished and got something else. Reading which of
the two broke separates "the article describes an interface this reader does not have" from
"the article describes a behavior the product no longer has."

### 4A. Unstated prerequisite

- **Signature:** threads report reaching a step and being blocked by a condition the article
  never names — a setting that must be enabled, an object that must exist first, a plan tier.
  The blocked step is the same one every time.
- **Rules it out:** the article names its prerequisites and threads do not cite one.

### 4B. Permission or role gate

- **Signature:** the control exists but only for a role the reader does not hold. Threads
  cluster by role rather than by segment or locale. The article does not say who can perform
  the task.
- **Rules it out:** the article states the required role, or the blocked readers hold it.

### 5A. Naming or interface drift

The article names a control the product has renamed, moved, or removed. This is vocabulary
acting through the **naming drift** mechanism.

- **Signature:** threads describe following the steps and reaching a screen the article does
  not describe. The article's last edit predates the release that moved the control.
  Comparison articles edited after the same release are unaffected.
- **Rules it out:** the described interface matches the shipped one at the reader's version.

### 5B. Behavioral divergence

The steps are correct and the result is not what the article says it will be.

- **Signature:** threads report a specific outcome — an empty file, a partial sync, a silent
  truncation — and it is the same outcome across threads. The article makes a promise the
  product does not keep at this input.
- **Rules it out:** reported outcomes are scattered and unrelated, which points back to
  comprehension.
- **Note:** divergence and defect sit close together here and the boundary matters. If the
  product is doing something it was never intended to do, that is a defect and belongs outside
  the funnel. If the product is doing exactly what it was built to do and the article describes
  something else, that is divergence and it is a documentation failure. The record that
  separates them is the product's own intent, not the user's expectation.

### 5C. Undocumented limit or edge case

- **Signature:** the outcome diverges only above a size, a count, a plan tier, a locale, or a
  data shape. Threads reporting success and threads reporting failure **sort on that
  variable**. The article describes the common case and does not mention the branch.
- **Rules it out:** the limit is documented, or the failures do not sort on any such variable.
- **Note:** the sorting is the evidence. A cause that produces failures on one side of a line
  and successes on the other is doing something a comprehension failure cannot do, because
  confusion does not respect a threshold.

---

## Outside the funnel — Not a documentation failure

These arrive in the same queue and are not what this folder diagnoses. Route them out before
computing any rate, and say plainly that the constraint sits outside documentation.

- **Defect or incident.** The product is broken and the article correctly describes intended
  behavior.
- **Feature request.** The user wants something the product does not do. No article closes it.
- **Channel preference.** Accounts with a named contact often ask by habit or by policy. The
  contact is not evidence that self-service failed, because self-service was never attempted.
- **Account-specific.** A billing dispute, a data recovery, a permission only support can
  change. No documentation could have answered it.

Leaving these in inflates every rate in the analysis, and they concentrate in exactly the
segments most likely to be over-represented in a hand-picked sample.

---

## The null: adoption growth

Nothing is wrong with this documentation.

- **Signature:** tickets per active user flat or falling across the window while the raw count
  rose. A rollout, migration, plan change, or release expanded the eligible population inside
  the window. The comparison set's rates track the subject's. The subject's per-stage figures
  sit inside the comparison range at every stage rather than falling below at any of them.
- **Rules it out:** the comparison set's rates holding steady while the subject's climbs.

A topic performing at product-normal rates while its user base grows is not a topic with a
problem. A rewrite here costs a writing cycle and removes nothing, because the constraint is
not this article.
