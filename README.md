# Savi Finance — Group Split with Voice

> D2 development progress. Feature availability depends on the supplied app build and backend; development demos are not a production release.

## Project

We are extending Savi Finance so people can split shared expenses, understand their own spending, and review who owes whom without maintaining a separate spreadsheet. Our team's work covers one-off splits, receipt/item splitting with voice or typed assignment, group transaction splits, and a balances overview.

**Implementation repository:** [Savi Finance's private monorepo](https://github.com/cheapreats/ce). Teaching staff need access to this repository to inspect the linked implementation PRs and evidence. The features described below are our team's contributions, not a description of the entire Savi product.

**A note on deployability:** We know that a component of the deliverables (such as D2 currently) is having a deployable version of the application for public access. Since we're working on a feature for Savi, an app with an existing userbase, this isn't always possible. We have our features for user stories mostly completed, but the process of merging them into the real codebase will take a little more time/coordination with the Savi team. In order to account for this, we have linked the branches/PRs that we worked on, with screenshots and demo videos attached to showcase our work. Thanks!

## Key Use Cases

### Splitting a one-off expense (David, Shaun)

**Why:** split a shared purchase without creating a group, and track your own spending separately from the full payment.

**What it does:**

- Splits a personal expense with existing Savi users or saved guests using equal, amount, or percentage allocations.
- Validates that shares add up correctly and handles leftover cents consistently.
- Saves the split with the transaction; **Manage split** lets you edit or remove it later.
- Counts your share in Spending and budget alerts while Wallet keeps the full payment: a $120 expense split equally between two people contributes $60 to your spending.

**How to try it** (signed in to the configured development build, with split saving enabled):

1. Tap **Add transaction → Expense**, enter the name, amount and date, and choose an account owned by your personal profile.
2. Tap **Split → Total with Others → Add people** and select at least one saved person.
3. Choose **Equal**, **Amount**, or **Percentage** and check the allocation.
4. Tap **Apply split**, then **Create** to save. Applying alone only updates the draft.
5. Reopen through **Edit → Manage split** to change or remove it, then save. Compare **Wallet** with **Insights → Spending** to see the full payment versus your share.

**Development limits:** PR6 is a read-only preview; saving requires PR7 and own-share spending requires PR8. PR7/8 remain development-only drafts with one unresolved integration-test failure. Guest creation, invitations, settlement, and money transfers are not included. Verification details and known simulator limitations are in the linked PRs.

**Screenshots, video and implementation:** [PR6: editor preview](https://github.com/cheapreats/ce/pull/6624), [PR7: saving and Manage split](https://github.com/cheapreats/ce/pull/6768), [PR8: own-share spending](https://github.com/cheapreats/ce/pull/6769) (Savi's private repository).

### Splitting a receipt by item (Praneeth, Shahmeer)

**Why:** after a group meal, people order different things, so an even split is unfair. Savi users can split a receipt line by line inside the app instead of using a spreadsheet or another app.

**What it does:**
- Starts from the existing **Add transaction → Split → Line Items** flow, as requested by our partner.
- Reads a photographed receipt (or lets you type the items), and lets you correct items, quantities, discounts, tax and tip.
- You choose which group members shared the meal, then tap who had each item, or say or type it: *"Sam had the burger, Alex and I shared the nachos."*
- Shared items are split evenly; tax and tip are split by what each person ordered; amounts always add up exactly to the receipt.
- A review screen shows your share and what each person owes you, and the split is added to the transaction.
- Group invitations can now be accepted from the Notifications screen, so friends can join a group before splitting.

**How to try it** (signed in to the Savi app, with Groups enabled):
1. Create a group from the **Groups** section and invite a friend; they accept it from the bell icon (**Notifications → Join**).
2. Tap **Add transaction**, enter the amount, then tap **Split → Line Items → Split receipt items with people**.
3. Choose the group, then take or upload a photo of the receipt, or type the items, tax and tip.
4. Tap **Choose people**, then **Assign items**: tap names on each item, or type a sentence like the one above and tap **Apply**.
5. Tap **Review** to see what everyone owes, then **Use split in transaction** to return to the transaction.

Saving the split as debts between group members is in progress with the transaction-split sub-team.

**Demo video and screenshots:** [Savi pull request #6759](https://github.com/cheapreats/ce/pull/6759) (Savi's private repository).

### Splitting a transaction with a group (Sumedh, Pranay)
Why: when one person pays for a shared expense, the app has to remember who owes what, or the split disappears as soon as the screen closes. Saving each person's share on the server is what lets Savi show balances and history, and keeps two people (or two devices) from overwriting each other's edits.

What it does:

* Creating a group expense also saves one record per participant with their share. The payer's own share is what is left of the total (a $12 expense shared by the payer and one member saves a single $6 debt, and no debt to oneself), and shares can add up to less than the total but never more.
* Sending the same create request twice, such as a retry after an uncertain submission, returns the existing expense instead of creating a duplicate.
* Only allowed people can create one: the caller must have an editing role in the group, and each participant must be an accepted member whose account is checked for ownership.
* Deleting an expense also deletes its shares, and editing the total can't go below what is already assigned to people.
* Getting or listing group expenses returns who owes what, which is what the History and Summary screens read.
* Each expense has a version number. An edit or delete can send the version it last saw, and if someone changed the expense in the meantime, it is refused with "changed by someone else" and nothing is overwritten.

How to try it (signed in to the Savi app, with Groups enabled, running against a backend that includes the saved-shares work):

1. Create a group from the Groups section and invite a friend. They accept it from the bell icon (Notifications → Join). Your friend needs at least one account in Savi.
2. Open the group and tap New Transaction.
3. Enter the description and amount, pick the account that paid, and choose the members who shared the expense.
4. Choose how to split it (even, by amount, or by percentage) and check the preview of who owes what.
5. Save the transaction. Open the group's History and Summary to see the expense, who paid, and the amount each person owes. These are saved on the server, so they are still there after you close and reopen the app.

In progress: repayment and settling up, attaching an existing transaction to a split, app screens for editing and deleting a group expense (the backend already supports both), and connecting the app to the edit-conflict check.

**Demo video and screenshots:** [Savi pull request #6760](https://github.com/cheapreats/ce/pull/6760) (Savi's private repository).

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
- The final `D2` release must identify the fixed app/backend version, grading access instructions, and known limitations. A release/access link is not yet supplied here.

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

The team will use **Jira for ticketing and task distribution and Slack for asynchronous communication**. We have been granted access to Savi Finance's internal platforms, and will use those for the duration of the project. 

## Access and Use

The feature sections above describe the available development workflows and their prerequisites. A fixed, independently accessible D2 app build and its access instructions have not yet been supplied in this README. The team must confirm these before submission; private PR links, screenshots, and a developer's local simulator do not by themselves provide grading access. Historical D1 prototype information is in the [mockup instructions](deliverables/D1/mockup.md).

## Development Requirements

The implementation stack and setup instructions are still being decided. **[TODO: add requirements and local setup commands once selected]**.

## External Dependencies

Our Group Split feature will depend on Savi's existing application stack, internal APIs, and third-party services.

### Application and Framework Dependencies
- **React Native** — used to build the Savi mobile application.
- **Expo / EAS** — used for local mobile development and mobile builds/deployment.
- **Go + Bazel** — used for Savi's backend services and build system.
- **MongoDB** — Savi's primary database.

### Internal APIs and Services
- **`sf1/api`** — Savi's main backend API, which the mobile application uses to communicate with backend functionality.
- **Existing transaction and receipt services** — may be used when creating splits from existing Savi transactions or receipt data.
- **Existing voice-agent / MCP infrastructure** — may be used for voice-based follow-ups and interactions if this portion of the project is implemented.

### Third-Party Services and APIs
- **Plaid** — Savi's existing banking data provider and may be relevant for transaction-based splitting.
- **OpenAI** — used by Savi for AI-powered functionality and may support voice/AI features.
- **AWS services** — Savi uses AWS services such as S3 for storage and infrastructure.
- **GitHub Actions** — used as part of Savi's CI/CD process.

The exact APIs and third-party services required specifically by Group Split have not yet been finalized and will be confirmed during technical design and implementation.

## GitHub Workflow

The team will use feature branches and pull requests. **Regarding naming, review, merge and naming conventions, we will exclusively follow Savi Finance's established practices as we are directly working on the company's monorepo**.

## License

Our contributions will follow Savi Finance's existing licensing and confidentiality requirements, since we are developing directly within their privately-owned codebase. We will not apply a separate open-source license unless the partner requests.

The code is intended for use within Savi's product and will not be publicly redistributed without permission.
