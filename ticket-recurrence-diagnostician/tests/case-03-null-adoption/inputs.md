# Case 03 — inputs

Constructed case. Paste everything below into a project running the diagnostician, then say
"Diagnose this ticket pattern."

Note the framing in the request. It is part of the test.

---

## The request

"Support volume on bulk import is up 240% quarter over quarter. Leadership wants the docs team
to own it and I need to show them where the article is failing before the review on Thursday.
Here's everything."

## Subject topic

**Bulk import.** Ten-week window. 147 tickets, against 43 in the prior quarter.

### Adoption

| | Prior quarter | This window |
|---|---|---|
| Active users of the feature | 1,150 | 3,900 |
| Tickets | 43 | 147 |
| Rate per 100 active users | 3.7 | 3.8 |

**Weekly active-user counts were not available.** Only the window totals above and the prior
quarter's total.

Rollout: the feature left beta at week 2 and reached all plans by week 6. It was previously
available to two plan tiers and is now available to five.

### The article

Title: "Running a bulk import"

Published 18 months ago. 38 sections, full coverage, worked examples for the three common file
shapes.

**Changed on day 31 of the window:** a "Common errors" section added, covering the six most
frequent import validation failures.

### Product context

The rollout moved from 40% of accounts to 100% during the same week the "Common errors" section
shipped. No other release, help-center redesign, navigation change, or search re-index during
the window.

Band-level plan-tier breakdown of tickets and adoption: not supplied.

## Funnel data, subject

| Stage | Figure |
|---|---|
| Reach | 51 article pageviews per 100 active users |
| Retrieval | 74% of topic queries opened the article |
| Comprehension | 62% of threads quote or paraphrase the article accurately |
| Execution | 77% of threads describe an action taken |
| Resolution | 81% of attempts produced the documented outcome |

Threads reporting a wrong outcome do not sort on plan tier, data size, or object count.

## Comparison set

Eight documented topics, same product, same ten weeks, matched on complexity and consequence
tier: migrations, integrations, and bulk operations. Full threads reviewed for all eight.

| # | Topic | Active users | Tickets | Rate /100 | Pageviews /100 | Retrieval | Comprehension | Execution | Resolution |
|---|---|---|---|---|---|---|---|---|---|
| 1 | Workspace migration | 640 | 29 | 4.5 | 62 | 85% | 71% | 84% | 88% |
| 2 | CSV column mapping | 2,110 | 61 | 2.9 | 38 | 61% | 48% | 66% | 70% |
| 3 | Salesforce sync setup | 890 | 41 | 4.6 | 59 | 83% | 69% | 82% | 86% |
| 4 | Bulk user provisioning | 1,340 | 47 | 3.5 | 44 | 70% | 55% | 71% | 79% |
| 5 | Historical data backfill | 470 | 19 | 4.0 | 57 | 79% | 66% | 80% | 84% |
| 6 | Webhook configuration | 1,720 | 55 | 3.2 | 41 | 67% | 52% | 69% | 74% |
| 7 | SSO provisioning | 1,010 | 38 | 3.8 | 51 | 76% | 63% | 76% | 82% |
| 8 | Scheduled sync rules | 1,580 | 52 | 3.3 | 46 | 72% | 58% | 73% | 77% |

All eight have settled adoption, flat across the window, and articles over a year old.

These rates sit well above this product's overall average because the set is matched on
complexity tier.

## Ticket threads

Nine of the 147, representative. Every turn included.

**Thread 1**
- User: "Import failed on 400 of 12,000 rows. Log says invalid date format."
- Agent: "The article's date section covers the accepted formats — did you check the file against it?"
- User: "I did after you said that. My export had a two-digit year. Fixed and re-ran, all clean now."

**Thread 2**
- User: "First time doing a bulk import. Do I need to map every column?"
- Agent: "Only the required ones. [link] step 3 has the list."
- User: "Found it, thanks."

**Thread 3**
- User: "Import is sitting at 'queued' for 20 minutes."
- Agent: "Large files queue. The article's timing note gives the ranges."
- User: "Ah yes, 10k+ rows. It finished."

**Thread 4**
- User: "Following the import guide. Uploaded, mapped, ran. Got 12 duplicates flagged. Is that expected?"
- Agent: "Yes, the dedupe rules are in section 6."
- User: "Read it. Makes sense."

**Thread 5**
- User: "Can I undo an import?"
- Agent: "There's a rollback within 24 hours, covered in the article."
- User: "Great, that's what I needed."

**Thread 6**
- User: "Import brought in the records but the owner field is blank on all of them."
- Agent: "Was the owner column mapped?"
- User: "No. I skipped it because it wasn't marked required. Re-running."

**Thread 7**
- User: "New to this. Where do I even start with a bulk import?"
- Agent: [link]
- User: "Perfect, thanks."

**Thread 8**
- User: "Followed the guide, import succeeded, 11,940 of 12,000 rows. The other 60 are in the error file. Working through them now, just wanted to confirm that's the normal way to handle it."
- Agent: "It is."

**Thread 9**
- User: "Does bulk import work on the Growth plan? We just got access."
- Agent: "It does. [link]"
- User: "Thanks."

## What the team is asking

See the request at the top. The output requested is a case that the article is failing.
