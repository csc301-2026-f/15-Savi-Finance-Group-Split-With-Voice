# YOUR PRODUCT/TEAM NAME

> Aim for 1000-2000 words. Be concise and analytical. We care about reasoning, impact, and integration quality, not length.

## 1. What Needed to Improve

After D2, our features worked mostly in isolation rather than as one product. Each sub-team had built its flow on its own branch: receipt splits could be built and reviewed but not saved, the one-off split editor was a read-only preview whose saving lived in a later PR, and receipt and transaction splitting each needed groups, participants, saved shares and balances. A split that isn't saved never reaches the other person, so the core promise of the product (both people can see who owes whom) did not hold end to end. The most important gap was turning these separate prototypes into a connected, reliable flow: one shared way to save group expenses, reviewed code that Savi could merge, and screens clear enough for real users.

We identified this through partner input and team reflection. In our D2 presentation we flagged the overlap between sub-teams and the risk of building two inconsistent saving flows. In PR review, Savi's engineers requested changes (for example, splitting oversized PRs and hiding split data from default API responses), and Savi's CEO asked for less wordy UI. At our planning meetings we agreed to fix and integrate existing PRs before starting new features, and to review each other's PRs before Savi does.

## 2. What You Did

Describe what was implemented, key architectural or design changes, and integration challenges.

Ideas:
Talk about our code changes, both for group split and one-off split. 
Maybe talk about how we approached things differently

## 3. Before vs. After

**Receipt splitting now ends in a saved, shared expense.** After D2, a receipt split could be built and reviewed but not saved, so the other person never saw it. In D3 the same flow saves through the shared group-expense path. We verified this end to end with two test accounts on a local Savi backend running the integration branch ([#6761](https://github.com/cheapreats/ce/pull/6761)) and recorded it ([walkthrough video](https://drive.google.com/file/d/1_RcoIVwYVeFO3oh8SeUBXMU0YUKbhP6R/view?usp=sharing)):

| | Before | After |
|---|---|---|
| Other person's view | ![Settled up](screenshots/before-sarah-settled.jpg) Group shows "Settled up" | ![Owes $32.50](screenshots/after-sarah-owes.jpg) Group shows "Owe $32.50 USD" |
| Assigning items | ![Unassigned](screenshots/before-items-unassigned.jpg) Every item "Not assigned yet" | ![Assigned](screenshots/after-items-assigned.jpg) One typed sentence assigns both items |

- **Workflow:** One user scans a $40 receipt (Burger $20, Nachos $12, tax $4, tip $4); Savi's AI fills in the merchant, items, tax and tip. Typing *"Sarah had the burger, we shared the nachos"* assigns both items in one step instead of tapping each one. Tax and tip are split by what each person ordered, so the shares are $32.50 and $7.50 and add up exactly to $40.00.
- **Visible to the other person:** The saved expense appears in the group's history with its receipt items and the line "Sarah Test owes Alex Test US$32.50", and on Sarah's own Overview.

**Fewer errors reach the partner.** We reviewed each other's PRs before Savi's review, and the authors fixed every issue we posted:
- the Owed/Owing widget counted expenses whose save hadn't finished, and added different currencies into one total ([#6770](https://github.com/cheapreats/ce/pull/6770));
- guest creation and invitations ignored the `EXPENSE_SPLITS_ENABLED` rollout flag, and the guest collection had no database indexes ([#6605](https://github.com/cheapreats/ce/pull/6605));
- participant names could show raw `u_…` user IDs instead of names (#6770, #6605).

**More checks pass.** The integration PR went from failing type checks (15 new errors) and Savi's test-coupling gate to passing both, after fixing two real bugs (unreadable receipt prices were copied into the form without an amount; a receipt-save test never ran) and adding Go tests for the receipt AI client.

## 4. Reflection

What worked well, what was harder than expected, and how this affects your path to D4.

Ideas:
Add reflection
Looking forward
- getting things merged in (should be very soon)
- starting on voice and other things

