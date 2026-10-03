# User Stories: Group Split with Voice Follow-ups

**Team 15 × Savi Finance** · CSC301 Fall 2026

These user stories make up the MVP for the Group Split with Voice Follow-ups feature in Savi Finance's mobile app. Related work is tracked in Savi's Jira under epic [WI-200](https://savifinance.atlassian.net/browse/WI-200).

---

## 1. One-off Split

As a Savi user who paid for a shared expense, I want to split one transaction with one or more people without creating a group, in order to track who owes me without entering the expense again in Splitwise or a spreadsheet.

**Acceptance criteria:**

- The user can open any transaction, tap "Split," and choose one or more people.
- The split is even by default, and the user can switch to dollar amounts or percentages.
- If the splits don't add up to the transaction total (more than $1 off), an error is shown.
- The user's budget counts only their share, e.g. $25 of a $100 dinner split four ways.
- Each person's balance with the user updates right away.

## 2. Group Split

As a roommate who shares rent and utilities, I want to create a group and split transactions inside it, in order to manage shared costs that repeat in one place.

**Acceptance criteria:**

- The user can create a group with a unique name and invite people by email or invite link.
- Invitees get a notification they can accept or reject. They show as "pending" until they accept.
- Any member can add a transaction to the group. It's split evenly across members by default, and amounts can be adjusted.
- The group page shows each person's net balance and a history of all changes.
- Savi remembers the split percentages used for each type of item in the group (e.g. rent, utilities, groceries) and suggests them the next time that type of item is split. The user can change them before confirming.

## 3. Owed/Owing Widget

As a Savi user, I want to see my Total Owed and Total Owing on my home screen, in order to know where I stand with friends at a glance.

**Acceptance criteria:**

- The home screen shows Total Owed to the user and Total the user Owes, across all one-off and group splits.
- Tapping a total shows a breakdown by person and by group.
- Either person can mark a balance as resolved, and can undo it.
- Resolved balances drop out of the totals but stay in the history.

## 4. Receipt Split

As a user who paid for a group meal, I want to split the bill from a photo of the receipt and assign items to each person using my voice, in order to split the bill fairly when people order different things.

**Acceptance criteria:**

- The user can take or upload a photo of a receipt, and it's broken into line items plus tax and tip.
- The user can fix any items that were read incorrectly.
- Each item can be assigned to one or more people. Shared items are split evenly.
- The user can assign items by speaking, e.g. "Sam had the burger, Alex and I shared the nachos," and the assignments appear on screen to confirm or fix.
- Tax and tip are split based on what each person ordered.
- The user sees what each person owes before confirming.

## 5. Voice Follow-up

As a user who is owed money, I want to have Savi's voice agent call friends who haven't paid after they've ignored their reminders, in order to get paid back without having an awkward conversation.

**Acceptance criteria:**

- Voice follow-up is off by default, and the user turns it on per split or group.
- A call only goes out after push/email reminders go unanswered for a set time.
- The agent says it's automated and who it's calling for.
- The agent handles "I already paid," "I'll pay on [date]," "I dispute this," and "don't call me again."
- Anyone who says "don't call me" is never called again.
- The person being called can pay the balance during the call through Stripe. A successful payment marks the balance as paid automatically.
- The call result is shown on the balance. Apart from payments made through Stripe on the call, a balance is never marked paid unless the user confirms it.

## 6. Customize the Voice Agent

As a user who is owed money, I want to control how the voice agent follows up, in order to make the calls fit my relationship with the person.

**Acceptance criteria:**

- The user can set the agent's tone (e.g. friendly or firm), when calls start, and the maximum number of attempts.
- Settings can be applied to a single split or to a whole group.
- The user can see a log of past calls and how each one ended (promised a date, disputed, paid, opted out).
