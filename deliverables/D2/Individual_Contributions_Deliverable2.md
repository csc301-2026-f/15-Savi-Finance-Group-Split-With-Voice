## Team 12 // Savi Finance — Individual Contributions Document

### Name: David

One-Line Description:

Precise Description:
* placeholder

### Name: Shaun

One-Line Description: Built the one-off split mobile workflow with David's backend and added own-share spending attribution.

Precise Description:

* Added participant selection and equal, amount, and percentage splits ([PR6](https://github.com/cheapreats/ce/pull/6624), with David).
* Connected saving, reopening, editing, and removing splits to the backend ([PR7](https://github.com/cheapreats/ce/pull/6768)).
* Redesigned Manage split to match Savi's UI and distinguish the full payment from your share.
* Added own-share spending and budget alerts while preserving full Wallet payments ([PR8](https://github.com/cheapreats/ce/pull/6769)).
* Added regression tests, captured iOS screenshots, and documented the D2 workflow and limitations.

Status: PR7/PR8 are development-only drafts; verification details and outstanding issues are linked in the README.

### Name: Praneeth

One-Line Description: Built the receipt capture/editing half of receipt splitting (with Shahmeer), moved it into Savi’s existing transaction workflow, integrated the receipt and transaction-splitting branches into a working save flow.

Precise Description:
* Receipt scanning/OCR: Connected receipt capture and upload to Savi’s existing AI extraction service. Investigated OpenRouter failures, applied Jun’s model/provider configuration, and verified live extraction through the local API using a mock/synthetic receipt.
* Integration of both group-splitting flows: Created the integration branch while preserving both pairs’ commits and history. Connected receipt allocations to the group transaction team’s shared saving backend, including payment linkage, saved receipt details, retry/recovery behavior, and persisted History/Summary ([Integration PR](https://github.com/cheapreats/ce/pull/6761)).
* Receipt editor: Built the interface for correcting merchant, items, total, tax and tip, then extended it with quantities and discount rows.
* Draft state and validation: Implemented receipt draft storage and checks for valid money inputs, quantities and matching totals, preventing incomplete or inconsistent receipts from proceeding (see `receiptSplitSlice.ts`, `receiptSplitDraft.ts`).
* Transaction workflow: Following feedback from a discussion with Ralph, moved receipt splitting into Create/Edit Transaction → Split → Line Items, removed the separate Groups entry point, and preserved transaction fields and receipt corrections during navigation.
* Testing and handoff: Added regression tests, prepared simulator demos, verified saving through group History/Summary, and maintained setup instructions and implementation boundaries in RECEIPT_SPLIT_HANDOFF.md. This helped maintain a log of work + current status to share with Shahmeer during development.
* Iteration review: Contributed to the writing of iteration-02-review.md, covering Q2, Q4, and a small bit of Q1.

### Name: Shahmeer

One-Line Description: Built the item-splitting half of the receipt split flow (with Praneeth): choosing who shares an expense, assigning items to people, calculating what each person owes, plus group invitations and voice/typed item assignment.

Precise Description:
* Allocation logic: calculates each person's share in exact cents. Shared items are split evenly, tax and tip follow what each person ordered, and leftover cents are assigned deterministically so shares always add up to the receipt total (`receiptSplitAllocation.ts`, 12 tests).
* Participant picker: choose which group members share an expense; pending invitees cannot be selected; built as a shared component the transaction-split sub-team can reuse (`ParticipantPicker.tsx`).
* Item assignment screen ("Who had what?"): assign each receipt item to one or more people, with live per-person totals.
* Review summary: total, payer's share and what each person owes, as a reusable component (`SplitSummary.tsx`).
* Group invitations: found that the app hid group invitations (the backend supported them), so nobody could join a group; added Join/Decline for group invitations to the Notifications screen.
* Voice/typed item assignment: saying or typing "Sam had the burger, Alex and I shared the nachos" fills in the assignments; the on-device parser reports anything it cannot match instead of guessing (`voiceAssignment.ts`, 10 tests).
* Developer setup and verification: got the iOS simulator build working (stale prebuilt app, code signing and Bazel issues), tested the flow with Savi's test accounts, and documented setup and behaviour for the team in `RECEIPT_SPLIT_HANDOFF.md`.
* PR evidence: recorded the demo video and before/after screenshots for the receipt split PR (cheapreats/ce#6759) by driving the iOS simulator, and traced the live receipt-scanning failure to a likely cause (production still uses an outdated model name).

### Name: Pranay

One-Line Description: Built out the save and display group expense splits, transaction history, and fallback loops (with Sumedh). These contributions connect the mobile interface to the team’s backend work on persisted participant shares and give users a clearer workflow for recording shared expenses and reviewing who owes whom.

Precise Description:
* Rework group expense creation with participant selection, equal splits, input validation, and a preview of who owes what.
* Add transaction history showing expense totals, payer details, individual debts, and settled shares.
* Add loading, empty, error, and retry states to group expense flows.
* Implemented currency parsing and remainder-cent allocation so shares add up to the exact expense total.
* Updated group screens to prioritize email addresses when identifying members, making expense participants and debt breakdowns easier to recognize.
* Developer setup and verification: got the android build working and running through Android studio and tested the flow with Savi's test accounts.
* PR evidence: documented after screenshots for the group transaction split PR (cheapreats/ce#6760) by working through the E2E flow on android simulator.


### Name: Sumedh

One-Line Description:

Precise Description:
* placeholder

### Name: Sambhav

One-Line Description: Added a Splits card to the Overview showing Total Owed to You and Total You Owe across one-off and group splits.

Precise Description:
* New Splits card on Overview showing two totals: Owed to you and You owe.
* Tapping a total shows a breakdown by person and by group.
* Balances can be marked resolved and undone; resolved ones drop out of the totals but stay in a Resolved history. For now this is saved only on the device.
