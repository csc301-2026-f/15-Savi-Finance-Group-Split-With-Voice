# Savi Finance — Group Split with Voice

> D2 development progress. Feature availability depends on the supplied app build and backend; development demos are not a production release.

## Project

We are extending Savi Finance so people can split shared expenses, understand their own spending, and review who owes whom without maintaining a separate spreadsheet. Our team's work covers one-off splits, receipt/item splitting with voice or typed assignment, group transaction splits, and a balances overview.

**Implementation repository:** [Savi Finance's private monorepo](https://github.com/cheapreats/ce). Teaching staff need access to this repository to inspect the linked implementation PRs and evidence. The features described below are our team's contributions, not a description of the entire Savi product.

**A note on deployability:** We know that a component of the deliverables (such as D2 currently) is having a deployable version of the application for public access. Since we're working on a feature for Savi, an app with an existing userbase, this isn't always possible. We have our features for user stories mostly completed, but the process of merging them into the real codebase will take a little more time/coordination with the Savi team. In order to account for this, we have linked the branches/PRs that we worked on, with screenshots and demo videos attached to showcase our work. We discussed this approach with our tutorial TA, Rayan, who approved of this approach. Thanks!

## Key Use Cases

### Splitting a one-off expense (David, Shaun)

**Why:** split a shared purchase without creating a group, and track your own expense separately from the full payment.

**What it does:**

- Splits a personal expense with existing Savi users or saved guests.
- Supports equal, amount, and percentage splits, with validation so shares add up correctly.
- Saves the split with the transaction; **Manage split** lets you edit or remove it later.
- Shows your share in Spending while Wallet keeps the full payment: a $120 expense split equally between two people contributes $60 to your spending.

**How to try it** (signed in to the configured development build, with split saving enabled):

1. Tap **Add transaction**, choose **Expense**, and enter the name, amount, date, and a test account owned by your personal profile.
2. Tap **Split → Total with Others**, then select at least one other person under **Add people**.
3. Choose **Equal**, **Amount**, or **Percentage** and enter the shares if needed.
4. Tap **Apply split**, then **Create** to save the transaction. Wait for synchronization to finish.
5. Reopen the saved transaction through **Edit → Manage split** to change or remove the allocation, then save. With own-share spending enabled, compare **Wallet** with **Insights → Spending**.

Development-only: saving requires the mobile write flag and a compatible non-production backend; own-share spending requires PR8. Guest creation, invitations, and money transfers are not included. PR7/PR8 remain drafts, not a released D2 build; developer prerequisites and verification limits are documented in the linked PRs.

**Screenshots and implementation:** [PR6: editor preview](https://github.com/cheapreats/ce/pull/6624), [PR7: saving and Manage split](https://github.com/cheapreats/ce/pull/6768), [PR8: own-share spending](https://github.com/cheapreats/ce/pull/6769) (Savi's private repository).

### Splitting a receipt by item (Praneeth, Shahmeer)

**Why:** After a group purchase, people buy different things and may want a more nuanced way of splitting. With this change, Savi users can split a receipt line by line inside the app, by either taking a photo or manually entering items, instead of using a spreadsheet or more complex solution.

**What it does:**

- Starts from the existing **Add transaction → Split → Line Items** flow, as requested by our partner.
- Extracts merchant, total and item information from a receipt photo using Savi's existing AI service, or lets you enter the receipt manually. You can correct items, quantities and discounts, and enter tax and tip.
- You choose which group members shared the meal, then tap who had each item, or say or type it: *"Sam had the burger, Alex and I shared the nachos."*
- Shared items are split evenly; tax and tip are split by what each person ordered; amounts always add up exactly to the receipt.
- A review screen shows your share and what each person owes you. On the integration branch, Create/Save records the payment, receipt details and group debts.
- Group invitations can now be accepted from the Notifications screen, so friends can join a group before splitting.

**How to try it** (signed in to the development app, with Groups enabled; use the integration branch and local backend for saving):

1. Enable `group_card` under **Diagnostics → Feature Flags** if Groups is hidden. Create a group from **Overview → Groups** and invite a friend; they accept from **Notifications → Join**.
2. Tap **Add transaction**, choose **Expense**, enter the name and amount, and select a test account owned by the payer. Tap **Split → Line Items → Split receipt items with people**.
3. Choose the group, then take or upload a photo of the receipt, or type the items, tax and tip.
4. Tap **Choose people**, then **Assign items**: tap names on each item, or type a sentence like the one above and tap **Apply**.
5. Tap **Review split**, then **Use split in transaction** to return to the transaction draft. This step alone does not save an expense.
6. Tap **Create** (or **Save** for an existing expense), then open the group's **History** and **Summary** to see the saved receipt and balances.

Live extraction uses `openai/gpt-6-luna` through OpenRouter, pinned to `azure/us`. A generated receipt was successfully read through the authenticated local API ($35 total, with a $28 soup line). Photo-library upload and live extraction were verified in the iOS simulator using a generated receipt. Real-photo accuracy, camera capture and real-device microphone behavior still need verification. Typed assignment and manual receipt entry are available without live AI inference. Saved receipt item/assignment editing, group budget-share adjustments and post-save notifications remain unfinished.

**Demo video and screenshots:** [Savi pull request #6759](https://github.com/cheapreats/ce/pull/6759) (Savi's private repository).

### Splitting a transaction with a group (Sumedh, Pranay)

**Why:** when one person pays for a shared expense, the app has to remember who owes what, or the split disappears as soon as the screen closes. Saving each person's share on the server is what lets Savi show balances and history, and keeps two people (or two devices) from overwriting each other's edits.

**What it does:**

* Creating a group expense saves a debt record for each non-payer participant with a positive amount owed. The payer's own share is what is left of the total (a $12 expense shared by the payer and one member saves a single $6 debt, and no debt to oneself), and shares can add up to less than the total but never more.
* Sending the same create request twice, such as a retry after an uncertain submission, returns the existing expense instead of creating a duplicate.
* The caller must have an editing role in the group, and each participant must be an accepted member. Only the payer needs a funding account; if another participant's account is supplied, its ownership is checked.
* Deleting an expense also deletes its shares, and editing the total can't go below what is already assigned to people.
* Getting or listing group expenses returns who owes what, which is what the History and Summary screens read.
* Each expense has a version number. An edit or delete can send the version it last saw, and if someone changed the expense in the meantime, it is refused with "changed by someone else" and nothing is overwritten.

**How to try it** (signed in to the development app, with Groups enabled and a backend that includes the saved-shares work):

1. Create a group from the Groups section and invite a friend. They accept it from the bell icon (Notifications → Join). Only the payer needs a funding account; the friend can participate without linking a bank account.
2. Open the group and tap New Transaction.
3. Enter the description and amount, pick the account that paid, and choose the members who shared the expense.
4. Choose how to split it (even, by amount, or by percentage) and check the preview of who owes what.
5. Save the transaction. Open the group's History and Summary to see the expense, who paid, and the amount each person owes. These are saved on the server, so they are still there after you close and reopen the app.

In progress: repayment and settling up, attaching an existing transaction to a split, app screens for editing and deleting a group expense (the backend already supports both), and connecting the app to the edit-conflict check.

**Demo video and screenshots:** [Savi pull request #6760](https://github.com/cheapreats/ce/pull/6760) (Savi's private repository).

### Group split integration (Praneeth, Shahmeer, Sumedh, Pranay)

The four-person group split team combines the receipt and transaction-splitting pairs' work on **`feature/integrate-receipt-split`**, connecting and verifying the shared save flow. The original branches, commits and authors are preserved.

**What was integrated and how it works:**

- Both flows use the same group members, shared expense storage, debt records and History/Summary screens. Transaction splitting produces shares from a total; receipt splitting produces shares from item assignments and proportional tax/tip.
- Receipt review passes the confirmed allocation back to Create/Edit Transaction. Create/Save then calls the shared group-saving API, creates or links one full personal payment, and records debts for the other participants. Receipt items, quantities, discounts and assignments are retained with the group expense.
- Repeating an unchanged receipt save returns the same payment and expense instead of creating duplicates or resetting partial repayments. Interrupted receipt saves can be resumed from group History.
- The verified local example is a $35 receipt split between two people: one $35 personal payment, a $17.50 payer share and a $17.50 debt shown in group History/Summary. This records obligations; it does not transfer money.

**Integration PR and verification:** [Savi PR #6761](https://github.com/cheapreats/ce/pull/6761). This branch holds our overall development progress on the two group split flows as a checkpoint for D2. We plan to organize the changes into a **stack of smaller PRs** so the Savi team can review them more easily.

### Owes / Owed Widget (Sambhav)

**Why:** Savi users can see where they stand on the home screen, without checking each group or transaction.

**What it does:**

- Adds a **Splits** card to the Overview with two totals: **Owed to you** and **You owe**.
- Combines one-off splits from your own transactions with group splits.
- Tap a total to see the breakdown **by person** and **by group**; group balances name the person you owe.
- Mark a person's balance as **resolved** once you've settled up, and **undo** it if you made a mistake.
- Resolved balances drop out of the totals but stay in a **Resolved** history list.

**How to try it** (signed in to the Savi app):

1. Turn on the card: **Account → Diagnostics → View All Flags**, then switch on `mobile_split_balances`.
2. Go to **Overview** and scroll to the **Splits** card.
3. Tap **Owed to you** or **You owe** to see the breakdown by person and by group.
4. Tap **Resolve** next to a person: the total drops and they move to **Resolved**.
5. Tap **Undo** in the Resolved list to bring the balance back.

**Screenshots:** [Savi pull request #6770](https://github.com/cheapreats/ce/pull/6770)

## Deliverable 2

- [Iteration review and retrospective](deliverables/D2/iteration-02-review.md)
- [Individual contributions](deliverables/D2/Individual_Contributions_Deliverable2.md)
- Group split integration checkpoint: [`3f5caef7b`](https://github.com/cheapreats/ce/commit/3f5caef7b2d047ecd64b25c4c9849c700fd67c10), linked through [integration PR #6761](https://github.com/cheapreats/ce/pull/6761). The other feature PRs provide their own implementation and verification details.

## Deliverable 1

- [Planning document](deliverables/D1/planning.md)
- [Mockup instructions](deliverables/D1/mockup.md)
- Team information: `deliverables/team/`

## Confirmed Course and Meeting Context

- Official CSC301 group number: **15**. Team name in the tutorial schedule: **Team 12**.
- Deliverable 1 is due **Friday, October 2, 2026 at 11:59pm Toronto time**. [Quercus assignment](https://q.utoronto.ca/courses/441425/assignments/1794225).
- Tutorial: **Thursdays, 7:00-7:30pm Toronto time**, with mentor TA **Rayan El Ghazzi**. D1 Demo Day is **Thursday, October 1, 2026**. [Tutorial schedule](https://q.utoronto.ca/courses/441425/pages/tutorial-schedule).
- Recurring partner meeting: **Wednesdays, 6:00-6:20pm Toronto time**, on [Google Meet](https://meet.google.com/ogv-qkay-sxa), organized by **ralphpalxyz@gmail.com**.
- Mentor TA contact: **rayan.el.ghazzi@mail.utoronto.ca**. [Course syllabus](https://q.utoronto.ca/courses/441425/assignments/syllabus).

## Task Management

The team uses **Jira for ticketing and task distribution and Slack for asynchronous communication**, through Savi Finance's internal platforms.

## Access and Use

This course repository contains the project documentation; the implementation lives in Savi's private monorepo. Teaching staff need repository access to open the linked PRs and demo evidence. Each feature section describes the relevant development workflow and limitations. The group split integration runs locally using the setup below; these unmerged changes are not available merely by installing Savi's released app. Historical D1 prototype information is in the [mockup instructions](deliverables/D1/mockup.md).

## Development Requirements

This course repo is not a standalone application. For all who wish to set this repo up locally, they must follow **Savi Finance's existing setup instructions**.

- [Savi local backend setup](https://github.com/cheapreats/ce/blob/feature/integrate-receipt-split/dev/README.md)
- [Savi mobile development setup](https://github.com/cheapreats/ce/blob/feature/integrate-receipt-split/sba-mobile/README.md)
- [Receipt split setup, behavior and limitations](https://github.com/cheapreats/ce/blob/feature/integrate-receipt-split/sba-mobile/screens/groups/RECEIPT_SPLIT_HANDOFF.md)

Developers need access to the private monorepo, Node.js/npm, Go/Bazel and Docker for local services. The mobile app uses an Expo development build; iOS requires macOS/Xcode and Android requires the Android development tools. Expo Go does not include all of Savi's native modules.

For the two group split flows:

1. Check out `feature/integrate-receipt-split` in Savi's monorepo. Run both the mobile app and backend from this branch.
2. Follow the backend guide and start `make dev-up` from the monorepo root in a dedicated terminal.
3. Follow the mobile guide to build/install a development client, configure the simulator's local HTTPS trust, and run `make dev-mobile`. In `sba-mobile/`, install dependencies with `npm ci` and start Metro with `npx expo start --dev-client --clear`.
4. Sign in with an approved development/test account and use the feature steps above. Enable `group_card` if Groups is hidden. Create a test group and a payer-owned test account as needed; the prepared demo group on one developer's laptop is not automatically present on another machine.

For **live receipt extraction**, set these in the backend's ignored `sf1/api/.env`, then restart the backend:

```dotenv
OPEN_ROUTER_API_KEY=<approved development key>
OPEN_ROUTER_FAKE_MODE=
```

The model (`openai/gpt-6-luna`) and provider (`azure/us`) are configured in code. The mobile client must point to the local backend; a local key does not change Savi's hosted API. Manual receipt entry, assignment and saving do not require an OpenRouter key. Use fake-provider mode for the hermetic test suite, as described in Savi's setup documentation.

## External Dependencies

Our split workflows extend Savi's existing application stack and APIs. Local manual-expense demos do not require live banking connections.

### Application and Framework Dependencies

- **React Native** — used to build the Savi mobile application.
- **Expo / EAS** — used for local mobile development and mobile builds/deployment.
- **Go + Bazel** — used for Savi's backend services and build system.
- **MongoDB** — Savi's primary database.

### Internal APIs and Services

- **`sf1/api`** — Savi's main backend API, which the mobile application uses to communicate with backend functionality.
- **Existing transaction and receipt services** — reused for personal payment creation/editing, receipt extraction and attachment handling.
- **On-device voice/typed assignment parser** — maps spoken or typed item assignments to receipt participants. Voice follow-ups and model-based assignment fallback remain separate work.

### Third-Party Services and APIs

- **Plaid** — Savi's existing banking data provider and may be relevant for transaction-based splitting.
- **OpenRouter / OpenAI on Azure** — receipt image extraction uses `openai/gpt-6-luna` through OpenRouter's `azure/us` route. Manual receipt entry remains available without this service.
- **AWS S3 / local MinIO** — Savi's attachment storage and its local development equivalent.
- **GitHub Actions** — used as part of Savi's CI/CD process.

Live service credentials and environment configuration follow Savi's setup instructions and remain outside this course repository.

## GitHub Workflow

Implementation work stays on feature branches in Savi's monorepo and is submitted through PRs following the company's review and merge practices. The receipt and group transaction branches remain available as individual contribution evidence; the integration branch combines their work for testing and demonstration. Savi controls review and merging into its production codebase. Course documentation is maintained separately in this repository through team branches and PRs.

## Coding Standards and Verification

We follow Savi's existing component, API, validation and formatting conventions. Changes include relevant mobile/backend regression tests, local demo verification and the monorepo's `make presubmit` checks; verification details and outstanding failures are documented in the implementation PRs.

## License

Our contributions will follow Savi Finance's existing licensing and confidentiality requirements, since we are developing directly within their privately-owned codebase. We will not apply a separate open-source license unless the partner requests.

The code is intended for use within Savi's product and will not be publicly redistributed without permission.
