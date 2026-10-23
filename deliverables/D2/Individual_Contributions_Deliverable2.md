## Team 12 // Savi Finance — Individual Contributions Document

### Name: David

One-Line Description:

Precise Description:
* placeholder

### Name: Shaun

One-Line Description:

Precise Description:
* placeholder

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

One-Line Description:

Precise Description:
* placeholder

### Name: Sumedh

One-Line Description:

Precise Description:
* placeholder

### Name: Sambhav

One-Line Description:

Precise Description:
* placeholder
