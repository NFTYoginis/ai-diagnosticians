# Intake

What a case needs before a diagnosis is possible, and what to do when it is missing.

---

## Required

Without all four, the funnel cannot be reconstructed and the correct output is
**Undetermined**.

1. **The documentation as the user sees it** — the article or articles covering the topic, in
   full, with their publication and last-edit dates, and the surfaces that link to them.
2. **Full ticket threads, not opening messages.** Every turn, in order, for the tickets on the
   topic in the window.
3. **A comparison set of four or more documented topics** — same product, same window, each
   with an active-user denominator. See `baselines.md`.
4. **An active-user count for the subject topic's feature** over the window. This is the
   denominator. Without it, ticket volume is uninterpretable and the null cannot be tested.

The second is the one teams most often substitute for and the one the method most depends on.

**An opening message is compatible with every cause in the taxonomy.** "How do I export a CSV"
is what a user writes whether they never found the article, found it and could not follow it,
or followed it exactly and got an empty file. The turn that separates those is almost always
the second or the third, when the agent asks what they have already tried. Summaries destroy
it. So do subject lines, tags, and category labels, all of which were assigned by someone who
had already decided what the ticket was about — frequently the same someone who is now asking
you to confirm it.

---

## Strongly wanted

Each of these decides a specific branch. Note in the report which were absent.

- **Help-center search logs** for the window — queries, zero-result rate, which article opened.
  The only direct evidence at Stage 2.
- **Article pageviews** for the subject and for the comparison topics.
- **Release notes and edit history** across the window — the input the qualifying change test
  runs on, and the input that catches an article that went stale without being touched.
- **Rollout or adoption curve** for the feature, by week — the input the null model runs on.
- **In-product help click data**, and help-entry impressions where they are instrumented.
- **Reopen and repeat-contact counts** on the topic.
- **Locale and plan-tier breakdown** of both tickets and adoption, which is what separates a
  coverage gap from a comprehension finding.

---

## Useful

- In-article helpfulness responses
- Scroll depth or time on page against comparable articles
- The support macros in use on the topic, which reveal what agents have decided the answer is
- Community forum threads on the same question
- Prior versions of the article
- The product's own in-product search logs

---

## Handling missing evidence

**Never substitute inference for a missing input.** The failure mode this folder exists to
prevent is a confident cause built on absent data.

| Missing | Effect | What to write |
|---|---|---|
| Full threads (opening messages, tags, or summaries only) | Break cannot be located | Undetermined. Name it as the single blocking input and say that all three causes remain live. |
| Active-user denominator | Failure cannot be confirmed and the null cannot be tested | Undetermined on whether a failure exists at all. Do not read a raw count as a finding. |
| Help-center search logs | Stage 2 has no comparative baseline | Eliminate Stage 2 structurally if Stage 3 is at or above baseline, and label the elimination structural. Otherwise report that retrieval branches remain live and untested. |
| Article pageviews | Stage 1 has no comparative baseline | Same treatment. Structural elimination where downstream is healthy, named as structural rather than comparative. |
| Comparison set under 4 | Baseline unreliable | Provisional at best. Say the comparison set is too small to establish a range. |
| Rollout or adoption curve | Null model untestable | State that the null could not be rejected, which caps confidence at Provisional regardless of how clean the rest is. |
| Article edit and release dates | Stage 5 discriminators unavailable | If the break is at Stage 5, report Undetermined for the drift-versus-divergence split. Do not infer staleness from tone. |

The rollout row matters most. If you cannot test the null, you cannot claim a positive
diagnosis at full confidence, because the most likely alternative explanation was never
examined.

---

## Reading threads

Threads are primary evidence, and they are the reason this folder needs the whole record
rather than a summary. Read them. A tag is not evidence about a thread; it is evidence about
whoever tagged it.

What to look for, and only in the branches where it is live:

- **Prior contact with the documentation, for Stages 1 and 2.** Did the user quote it,
  paraphrase it, name it, or link it? Did they say they searched and found nothing? Absence of
  any reference is weak evidence in a single thread and strong evidence in aggregate.
- **Where the quote lands, for Stage 3.** A position in the procedure, or a noun. That
  distinction separates the two live causes at this stage and the count of quotes does not.
  See the discriminator in `failure-modes.md`.
- **What the user says happened, for Stages 4 and 5.** The specific screen, the specific error,
  the specific output. A reader who could not start and a reader holding a wrong result write
  different sentences, and the difference is the diagnosis.
- **Whether success and failure sort on a variable, for Stage 5C.** Plan tier, data size,
  locale, object count. Confusion does not respect a threshold, so a clean split on one is
  evidence a comprehension cause cannot produce.

Ticket volume on its own is not a diagnosis. Plenty of heavily documented features generate
steady contact and nothing is wrong. The question is always whether the threads explain the
specific stage that broke.

---

## Reading the article

Open it. Read it as published, at the version the user was on, in the locale they were in.

A description of an article is not evidence about the article, and neither is the team's
memory of what it says. If the article was referenced but not supplied, say that the
page-dependent branches could not be assessed and name them.

Check three things before anything interpretive, because all three are cheap and all three
silently invalidate downstream reasoning:

- **Publication date against the ticket histogram.** Tickets predating the article are not
  evidence about the article.
- **Last-edit date against the release dates in the window.** An article untouched across a
  release that moved the interface is the Stage 5 signature.
- **Locale and plan coverage against the adopting population.**

---

## Privacy

User names, account names, company names, agent names, and contact details are not needed and
should not appear in the report. Refer to users by segment or role, and to agents not at all.
Thread text is quoted for its content and attributed to nobody.

Support threads routinely contain personal data, credentials, and customer business
information. Whether to place them in a project is the operator's disclosure decision and not
this folder's. Either way the report does not reproduce that material, and nothing in the
method requires it.
