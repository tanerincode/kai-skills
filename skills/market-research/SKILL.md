---
name: market-research
description: Answer "is there a market for X", "who else does this", "what do they charge" with verified evidence and a verdict. Use for any market, competitor or pricing question before an idea is built.
---

# Market research

The finish line is a verdict the person can act on, with the evidence separated into what was verified and what was inferred, saved as `research/<yyyy-mm-dd>-<slug>.md`.

1. **Write the question** in one line at the top of the file: who the buyer is, what they would pay for, what would make the answer "no".
2. **Search widely**, three query families: the product category (plain words a buyer would type), the problem (what people complain about), and "alternatives to <known player>". Note communities and marketplaces where buyers gather.
3. **Read the actual sites**, not the search snippets: landing page, pricing page, terms, changelog, app-store reviews. Open the pricing page of every competitor and copy the numbers. A fact you did not see on their page is inferred, say so.
4. **Table the competitors**: name, link, what it does, price and unit, free tier, who it is for, last visible activity. Five to ten is enough; more is noise.
5. **Demand signals**: search volume if a tool is available, size and activity of communities, review counts and dates, job posts, funding. Each with a link and a date.
6. **Verdict**: one paragraph. Is there a market, who pays, what price band, where the gap is, and the smallest version worth building to test it. Disagree with the premise if the evidence says so.
7. **Save and remember**: the file in `research/`, sources as links, and the one-line conclusion stored in memory (`context_store`, L3) so the next session starts from the verdict, not the search.

Read the existing `research/` files first; the question may be answered already. Cost nothing: no paid reports, no sign-ups with the person's card.
