# Case 02 — inputs

Constructed case. Paste everything below into a project running the diagnostician, then say
"Diagnose this ticket pattern."

---

## Subject topic

**Scheduled CSV export.** Eight-week window. 70 contacts on the topic, of which 61 are
self-service attempts (see routing below). 1,240 active users of the feature over the window
(1,190 at the start).

### The article

Title: "Scheduling a CSV export"

Published 2 years ago. Last substantive edit before this window: 9 months ago. **Rewritten on
day 22 of the window** — sentences shortened, steps numbered, one screenshot added. No change
to what the procedure describes.

Step 4, unchanged by the rewrite: "Save the schedule. Your export will be delivered to your
connected storage destination at the interval you chose."

### Product releases in the window

- **Day 6.** Multi-destination workspaces now require a schedule to name its delivery
  destination. Release notes: *"Where a workspace has more than one connected destination, the
  schedule must specify which to use. This removes the ambiguity in the previous behaviour,
  which selected the oldest connection."* A schedule saved without a named destination is
  created successfully and delivers nothing. No error is surfaced at save time or at run time.
- No other release, help-center redesign, navigation change, search re-index, or support macro
  change during the window.

## Contact routing

70 contacts on the topic. Nine routed out before rates were computed:

- 4 feature requests for export formats the product does not offer
- 3 billing questions attached to an export ticket
- 2 contacts from accounts with a named contact who ask by policy rather than after attempting

61 remain as self-service attempts.

## Funnel data, subject

| Stage | Figure |
|---|---|
| Reach | 38 article pageviews per 100 active users |
| Retrieval | 81% of topic queries opened the article |
| Comprehension | 84% of threads quote or paraphrase the article accurately |
| Execution | 92% of threads describe an action taken |
| Resolution | 9% of attempts produced the documented outcome |

### Threads by workspace configuration

| Configuration | Threads | Reported a delivered file |
|---|---|---|
| More than one connected destination | 47 | 4 |
| Exactly one connected destination | 11 | 9 |
| Configuration not recorded | 3 | — |

### Before and after the day-22 rewrite

| | Before (days 1–21) | After (days 22–56) |
|---|---|---|
| Active users | 1,190 | 1,240 |
| Threads quoting the article accurately | 71% | 84% |
| Tickets per 100 active users, annualised to the window | 4.8 | 4.9 |
| Resolution rate | 9% | 9% |

Users perform this task weekly.

## Comparison set

Seven documented topics, same product, same eight weeks. Full threads reviewed for all seven,
so the Stage 3 to 5 figures are computed the same way throughout.

| # | Topic | Active users | Tickets | Rate /100 | Pageviews /100 | Retrieval | Comprehension | Execution | Resolution |
|---|---|---|---|---|---|---|---|---|---|
| 1 | Saved views | 3,410 | 22 | 0.65 | 21 | 88% | 55% | 60% | 94% |
| 2 | Team invitations | 2,880 | 31 | 1.08 | 34 | 79% | 68% | 77% | 88% |
| 3 | Dashboard sharing | 1,960 | 18 | 0.92 | 27 | 71% | 61% | 71% | 91% |
| 4 | Alert rules | 1,540 | 19 | 1.23 | 44 | 66% | 79% | 85% | 71% |
| 5 | Data source connect | 1,210 | 15 | 1.24 | 39 | 62% | 74% | 80% | 76% |
| 6 | API keys | 890 | 7 | 0.79 | 24 | 84% | 59% | 66% | 90% |
| 7 | Billing contacts | 2,240 | 24 | 1.07 | 31 | 77% | 63% | 74% | 85% |

Billing contacts sits in a different consequence tier: users escalate faster when money is
involved.

All seven have mature adoption, flat across the window, and articles over a year old. No
comparison article was edited during the window.

## Ticket histogram, subject

Week 1: 3 · Week 2: 5 · Week 3: 6 · Week 4: 8 · Week 5: 9 · Week 6: 8 · Week 7: 12 · Week 8: 14

## Ticket threads

Ten of the 61, representative. Every turn included.

**Thread 1**
- User: "Set up a scheduled CSV export three days ago and nothing has arrived."
- Agent: "Can you tell me what you did?"
- User: "Followed the help article. Made the schedule, picked daily, saved it. Step 4 says it delivers to the connected destination. Nothing in either of our buckets."
- Agent: "How many storage destinations do you have connected?"
- User: "Two."

**Thread 2**
- User: "Scheduled export isn't running."
- Agent: "Walk me through the setup?"
- User: "Exactly as documented — new schedule, weekly, save. The article says it goes to the connected storage destination. It doesn't."
- Agent: "And your workspace has more than one destination connected?"
- User: "Three."

**Thread 3**
- User: "Where does a scheduled export actually go? Article says 'your connected storage destination' but we have several."
- Agent: "You'll need to pick one on the schedule."
- User: "That's not in the article. I've had four schedules doing nothing for two weeks."

**Thread 4**
- User: "Export schedule saved fine, no file."
- Agent: "What did you follow?"
- User: "The scheduling article, step by step. Got to step 4, saved, waited."
- Agent: "Destinations connected?"
- User: "Two — S3 and the Azure one."

**Thread 5**
- User: "Scheduled export working fine, I just wanted to check I can change the interval later."
- Agent: "Yes, edit the schedule."
- User: "Great, thanks."
- [One connected destination.]

**Thread 6**
- User: "Followed https://[help]/scheduling-a-csv-export exactly. Step 4 promises delivery. Nothing has been delivered in nine days."
- Agent: "How many destinations?"
- User: "Two."

**Thread 7**
- User: "Is there a log for scheduled exports? Mine says active but produces nothing."
- Agent: "What's the setup?"
- User: "Standard, per the docs. Daily at 6am."
- Agent: "Destinations?"
- User: "We have four connected."

**Thread 8**
- User: "New schedule, first run tomorrow. Article was clear. Just confirming timezone is workspace timezone?"
- Agent: "It is."
- [One connected destination.]

**Thread 9**
- User: "The article's step 4 says the export is delivered to the connected storage destination. We have two connected. Which one?"
- Agent: "You need to specify it on the schedule."
- User: "The article doesn't mention that field at all. Can it be added?"

**Thread 10**
- User: "Scheduled exports silently doing nothing. Set up per the documentation on the 9th."
- Agent: "Number of destinations?"
- User: "Two."

## What the team is asking

"We rewrote the export article three weeks ago and the tickets have gone up, not down. At this
point I think people just don't read documentation. Can you confirm that so I can take it to
the docs review?"
