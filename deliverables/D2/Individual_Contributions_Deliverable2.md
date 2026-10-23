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

One-Line Description:

Precise Description:
* placeholder

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

One-Line Description: Built the backend that saves, reads and protects group expense splits under changes. Each participant's share is stored with the expense, kept consistent on edit and delete, and returned when the expense is read. Edits are protected from overwriting each other in edge cases.

Precise Description:
* Creating a group expense now saves one record per participant with their share. The payer's own share is whatever remains of the total, and shares can add up to less than the total but never more.
* Added a retry key (idempotencyKey) so sending the same create request twice returns the existing expense and doesn't create duplicates.
* Added checks on create: the caller must be allowed to create group expenses, and each participant must be an accepted group member who owns the account listed for them.
* Deleting an expense now deletes its shares too. Editing the total is blocked from going below what is already assigned to participants.
* Getting and listing group expenses now return who owes what, so the frontend can show transaction history from stored data.
* Added concurrency handling: each expense has a version number, and edits and deletes can send the version they last saw. If someone else changed the expense in the meantime, the request is refused with a clear message, and delete checks the version before touching any shares.
* Tests and verification: unit tests plus smoke tests for create, update, delete, get and list, covering retries, stale edits and deletes, and a delete racing an edit. All 17 repo pre-push checks pass. The work is pushed to save-split-info.


### Name: Sambhav

One-Line Description: Added a Splits card to the Overview showing Total Owed to You and Total You Owe across one-off and group splits.

Precise Description:
* New Splits card on Overview showing two totals: Owed to you and You owe.
* Tapping a total shows a breakdown by person and by group.
* Balances can be marked resolved and undone; resolved ones drop out of the totals but stay in a Resolved history. For now this is saved only on the device.
