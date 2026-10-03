# YOUR PRODUCT/TEAM NAME
> _Note:_ This document will evolve throughout your project. You commit regularly to this file while working on the project (especially edits/additions/deletions to the _Highlights_ section). 
 > **This document will serve as a master plan between your team, your partner and your TA.**

## Product Details
 
#### Q1: What is the product?

Team 12 is working on a project in collaboration with an industry partner, Savi Finance. We’re developing a feature intended to be built into Savi Finance’s existing mobile app that lets users split transactions with multiple friends, who can be both Savi and non-Savi users, and uses a voice AI agent to automatically follow up on unpaid balances via phone call. Currently, Savi users split expenses using external tools (e.g., Splitwise) and track their budgets separately, either in Savi or external spreadsheets. As a result, users are forced to log the same transaction twice, once in the split app and once in their budget. Thus, following requests from their users, Savi Finance has decided to integrate this splitting feature as a way to centralize budget handling in one source. Savi Finance is an existing budgeting/personal finance application, available across both Canada and USA. Across multiple platforms (iOS/Android, web, Chrome extension, etc.), Savi Finance supports functions such as secure account connection through trusted providers (e.g., Plaid, Finicity), spending tracking, goal planning and receipt capture. Notably, Savi also currently supports a basic expense-splitting feature, so this project can be seen as an extension of that feature so as to support splits across multiple accounts. We’re also tasked with improving the feature that allows a user to perform receipt capture using their voice. Our primary company contact is Ralph Maamari, the founder of Savi Finance. By the end of the course, we will have developed and enhanced 5 workstreams: one-off splitting, group split from receipts (with voice AI integration for handling conversational nuance of asking for repayment), group split from transactions, UI changes (i.e., showing Total Owed/Total Owing) and MCP control. By extension, we will also add upon features such as email notifications for new splits, ability to create a group for recurring splits and predicting future splits using past splits. For instance, consider a user who splits a $135 bill three ways with friends, one of whom does not use Savi; that friend will receive a notification with their $45 share and can repay without needing to install Savi. If the balance goes unpaid after a set amount, our voice agent will call the friend directly and explain the amount owed conversationally. Beyond one-off splits like this, users can set up recurring groups for ongoing shared costs, such as rent and utilities, so that splitting is automatically handled. 

#### Q2: Who are your target users?


Since we’re working on a feature to be integrated into Savi Finance directly, our target users are Savi Finance’s existing target users, particularly since our feature was requested by current Savi users. Available information points to a recurring trait among Savi's users: many rely on multiple separate apps to manage different parts of their finances (e.g., a budgeting app plus a separate splitting tool like Splitwise), creating redundant, manual work.  Consider the personas provided below as a small sample that illustrates Savi’s user base: 

- Maya (26 y/o, Austin): A marketing coordinator at a medium-sized firm, Maya is an existing Savi user who regularly goes out with her friends for dinners, concerts and other group outings. She finds herself using Splitwise to split costs with friends, and then manually re-entering her share into Savi, after every outing. Given her frequency of outings, she finds tracking and logging finances across two apps unsustainable, and this feature would allow her to directly split the bill on Savi (regardless of whether or not her friends use it) and her share would update her budget automatically without further manual intervention. 
- Devon (23 y/o, Chicago): A junior financial analyst, Devon is an existing Savi user who shares a rented apartment with two roommates. Every month, he and his roommates split rent, utilities, and groceries, currently tracked through a shared spreadsheet that has to be recreated and recalculated each billing cycle. Given how repetitive and error-prone this process has become, he finds manually managing recurring shared costs outside of Savi unsustainable, and this feature would allow him to set up a persistent roommate group on Savi once, with recurring bills splitting automatically each month and syncing directly with the budget he already tracks in the app. 
- Jordan (24 y/o, Denver): A freelance graphic designer, Jordan is a Savi user who often owes small amounts to friends after splitting costs, but between juggling multiple client deadlines and an inconsistent schedule, repayment reminders tend to get buried among his other notifications. Given how easily a text or app alert slips through the cracks when he's heads-down on a project, he finds relying on passive reminders unreliable, and this feature would allow Savi's voice AI agent to call him directly after a set period of non-payment, explain what he owes in a natural, conversational way, and walk him through repaying it (e.g., via e-transfer) without him needing to proactively check an app. 



#### Q3: Why would your users choose your product? What are they using today to solve their problem/need?

The feature we’re working on directly addresses the core frustration shared by the personas presented in Q2, which is manually maintaining accurate finances across many platforms. Today, a user might rely on Splitwise-like software or spreadsheets before they manually re-enter the values into Savi; this is not only redundant, but it also introduces room for error in manual entry. Building splitting natively into Savi allows a split and budget change to happen in the same action and eliminates the duplicate entry entirely. For a user like Maya, who splits bills with friends multiple times a week, this removes a recurring manual task; for Devon, it removes the need to recreate and recalculate a shared spreadsheet every billing cycle, since his roommate group persists automatically. Beyond removing repetitive work, the feature gives users more accurate, synced financial data than they currently have. Rather than estimating or manually transferring split amounts into their budget, users see a total owed/owing view so their budget always reflects reality without manual reconciliation. The ability to learn from past splits to predict future arrangements challenges Splitwise’s resetting of history with each new group or transaction. For Jordan's use case, the value is less about logging and more about actually getting repaid. Standard reminders (texts, push notifications) are easier to ignore when someone is busy, which is why unpaid balances often linger. The voice AI agent's phone/email follow-up cuts through that notification fatigue by handling repayment requests conversationally and directly, and this is something no other splitting tool offers. While Splitwise is the dominant splitting solution today, it requires a separate account (which often needs to be upgraded for premium features) and never synchronizes with a user’s actual budget; with our feature upgrades, we bring many features often trapped behind paywall on apps like Splitwise forward (ex: custom splits, receipt extraction) to enable wider access. Our work primarily tackles Savi’s mission to consolidate a user’s financial life into a single place, as well as making personal finance as collaborative and transparent as possible between all parties. In addition, Savi Finance values keeping up with technology advancements to accelerate product growth, and our work integrating things like voice AI and MCP addresses this organizational interest. 

#### Q4: What are the user stories that make up the Minumum Viable Product (MVP)?

Full user stories and acceptance criteria are also in [user-stories.md](./user-stories.md). Related work is tracked in Savi Finance's Jira under [WI-200](https://savifinance.atlassian.net/browse/WI-200).

**1. One-off Split**

As a Savi Finance user who paid for a shared expense, I want to split one transaction with one or more people without creating a group, in order to track who owes me without entering the expense again in Splitwise or a spreadsheet.

Acceptance criteria:
 * The user can open any transaction, tap "Split," and choose one or more people.
 * The split is even by default, and the user can switch to dollar amounts or percentages.
 * If the splits don't add up to the transaction total (more than $1 off), an error is shown.
 * The user's budget counts only their share, e.g. $25 of a $100 dinner split four ways.
 * Each person's balance with the user updates right away.

**2. Group split**

As a roommate who shares rent and utilities, I want to create a group and split transactions inside it, in order to manage shared costs that repeat in one place.

Acceptance criteria:
 * The user can create a group with a unique name and invite people by email or invite link.
 * Invitees get a notification they can accept or reject. They show as "pending" until they accept.
 * Any member can add a transaction to the group. It's split evenly across members by default, and amounts can be adjusted.
 * The group page shows each person's net balance and a history of all changes.
 * Savi Finance remembers the split percentages used for each type of item in the group (e.g. rent, utilities, groceries) and suggests them the next time that type of item is split. The user can change them before confirming.

**3. Owed/Owing widget**

As a Savi Finance user, I want to see my Total Owed and Total Owing on my home screen, in order to know where I stand with friends at a glance.

Acceptance criteria:
 * The home screen shows Total Owed to me and Total I Owe, across all one-off and group splits.
 * Tapping a total shows a breakdown by person and by group.
 * Either person can mark a balance as resolved, and can undo it.
 * Resolved balances drop out of the totals but stay in the history.

**4. Receipt Split**

As a user who paid for a group meal, I want to split the bill from a photo of the receipt and assign items to each person using my voice, in order to split the bill fairly when people order different things.

Acceptance criteria:
 * The user can take or upload a photo of a receipt, and it's broken into line items plus tax and tip.
 * The user can fix any items that were read incorrectly.
 * Each item can be assigned to one or more people. Shared items are split evenly.
 * The user can assign items by speaking, e.g. "Sam had the burger, Alex and I shared the nachos," and the assignments appear on screen to confirm or fix.
 * Tax and tip are split based on what each person ordered.
 * The user sees what each person owes before confirming.

**5. Voice follow-up**

As a user who is owed money, I want to have Savi Finance's voice agent call friends who haven't paid after they've ignored their reminders, in order to get paid back without having an awkward conversation.

Acceptance criteria:
 * Voice follow-up is off by default, and the user turns it on per split or group.
 * A call only goes out after push/email reminders go unanswered for a set time.
 * The agent says it's automated and who it's calling for.
 * The agent handles "I already paid," "I'll pay on [date]," "I dispute this," and "don't call me again."
 * Anyone who says "don't call me" is never called again.
 * The person being called can pay the balance during the call through Stripe. A successful payment marks the balance as paid automatically.
 * The call result is shown on the balance. Apart from payments made through Stripe on the call, a balance is never marked paid unless the user confirms it.

**6. Customize the voice agent**

As a user who is owed money, I want to control how the voice agent follows up, in order to make the calls fit my relationship with the person.

Acceptance criteria:
 * The user can set the agent's tone (e.g. friendly or firm), when calls start, and the maximum number of attempts.
 * Settings can be applied to a single split or to a whole group.
 * The user can see a log of past calls and how each one ended (promised a date, disputed, paid, opted out).

User stories sent to Ralph Maamari (Founder, Savi Finance) for review on October 2, 2026:

<p align="center">
  <img src="images/q4-ralph-user-stories.png" alt="Slack message to Ralph with user stories" width="80%">
</p>

Ralph reviewed the stories the same day and approved them with three changes, which are included above: voice input for receipt splits, paying through Stripe during a voice follow-up call, and remembering split percentages by item type in groups.

<p align="center">
  <img src="images/q4-ralph-feedback.png" alt="Ralph's approval and feedback on the user stories" width="80%">
</p>

#### Q5: Have you decided on how you will build it? Share what you know now or tell us the options you are considering.

We haven't finalized every implementation detail yet, but we'll be building within Savi Finance's existing monorepo and architecture.

The Savi Finance mobile application is built in TypeScript using React Native and Expo. Backend services are primarily written in Go and built with Bazel, with `sf1/api` serving as the main JSON-RPC API used by their mobile app. MongoDB is Savi Finance's primary database.

Our current plan is to add the Group Split UI to the existing mobile app and connect it to new or existing backend API functionality for creating groups, splitting expenses, and tracking balances. This feature will also integrate with existing Savi Finance systems like transaction data, receipt-related functionality, and potentially the existing voice-agent service for voice interactions (if time permits).

Below is the high level architecture diagram our group agreed upon:
<p align="center">
  <img src="images/q5-arch-diagram.png" alt="Architecture diagram" width="60%">
</p>

For deployment, we are expected to push to prod at least 3 times throughout the semester. Our deployments will follow Savi Finance's existing infrastructure and CI/CD process, which uses GitHub Actions and deployment scripts within the monorepo. Mobile builds are managed with Expo/EAS, and backend services are deployed through Savi Finance's existing infrastructure. A lot of these tools and technologies are foreign to us, so we'll make sure to research them thoroughly before pushing/deploying our code.

As for Savi Finance's third party apps and APIs, we've learned that their existing integrations include Plaid for banking data, OpenAI for AI-powered features, and AWS for services such as S3. The exact APIs and services needed for our feature will be finalized soon during technical design.

----
## Intellectual Property Confidentiality Agreement 
> Note this section is **not marked** but must be completed briefly if you have a partner. If you have any questions, please ask on Piazza.
>  
**By default, you own any work that you do as part of your coursework.** However, some partners may want you to keep the project confidential after the course is complete. As part of your first deliverable, you should discuss and agree upon an option with your partner. Examples include:
1. You can share the software and the code freely with anyone with or without a license, regardless of domain, for any use.
2. You can upload the code to GitHub or other similar publicly available domains.
3. You will only share the code under an open-source license with the partner but agree to not distribute it in any way to any other entity or individual. 
4. You will share the code under an open-source license and distribute it as you wish but only the partner can access the system deployed during the course.
5. You will only reference the work you did in your resume, interviews, etc. You agree to not share the code or software in any capacity with anyone unless your partner has agreed to it.

**Your partner cannot ask you to sign any legal agreements or documents pertaining to non-disclosure, confidentiality, IP ownership, etc.**

Briefly describe which option you have agreed to.

Our agreement is a mix of a few of the options. Each one of us is only allowed to show the code that we have personally contributed to the codebase to external sources (like interviews, etc.). We are allowed to take videos, screenshots, demos of the final product to add to our portfolio and show to external sources.

----

## Teamwork Details

#### Q6: Have you met with your team?

Several members of our team have known one another since our first year at UofT, while others became acquianted through mutual friends. Our first team-building meeting was held online, where we bonded by playing some NYT and puzzle games together, in addition to discussing the project's architecture and technical design.

<p align="center">
  <img src="images/q6-team-meeting.png" alt="Team meeting screenshot" width="80%">
</p>

Team Fun Facts:
 * David and Shahmeer originally met while working as interns at Shopify this summer in Toronto.
 * Many of us enjoy going to concerts, especially Pranay and Sambhav, who have been to 5+ concerts this summer together.
 * We all LOVE cats except Pranay who is scared of them.

#### Q7: What are the roles & responsibilities on the team?

Our roles follow Savi Finance's mobile, backend, and voice/AI development areas. Everyone will contribute code and review related work; exact ticket ownership may shift as the technical design is finalized.

**Mobile Development — React Native/Expo screens and API integration**

* **Praneeth Suryadevara:** Work on one-off and group split screens, including transaction and member selection. Praneeth's React Native and full-stack experience fits this work, and Praneeth is looking to gain experience shipping features to real users.
* **Pranay Chopra:** Work on receipt review and owed/owing screens. Pranay has built React interfaces and fintech software and is interested in the intersection of finance and technology.

**Backend Development — Savi Finance's current API, data, and split logic**

* **David Daniliuc:** Work on split calculations, balances, and transaction integration, including tests for financial calculations. David's Go, systems, and infrastructure experience fits the API work.
* **Shaun Danny:** Work on APIs and data storage for groups and invitations, and coordinate API contracts with mobile and AI contributors. Shaun's REST API, data pipeline, and cloud experience fits this work. Shaun also wants to learn more about system architecture.

**AI/LLM Integration — receipt voice input and voice follow-ups**

* **Sumedh Gadepalli:** Connect voice features to Savi Finance's existing voice infrastructure. Sumedh has built an AI voice-agent prototype and is interested in AI infrastructure.
* **Sambhav Athreya:** Work on voice-based receipt item assignment and review of AI output. Sambhav's AI engineering internship, LLM agent work, and generative AI research fit this task.
* **Shahmeer Khan:** Work on voice follow-up behavior, call outcomes, and agent settings. Shahmeer's machine learning and multi-agent AI experience fits this work.

**Partner Liaison — communication and coordination**

* **Sumedh Gadepalli:** Serves as the dedicated contact with Ralph. Responsibilities include collecting questions, preparing meeting topics, relaying decisions and follow-ups to the team. Sumedh has already coordinated the team's introduction and interests with Ralph by email.

#### Q8: How will you work as a team?

 * **Weekly team meeting:** We meet online every Tuesday at 5:30pm to review Jira progress, assign or rebalance work, discuss technical decisions, and identify blockers. We may schedule additional online working sessions or move the meeting when a deadline requires it.
 * **Weekly partner meeting:** We meet with Ralph from Savi Finance online every Wednesday from 6:00pm to 6:20pm to discuss product direction and technical blockers, ask partner-specific questions, and receive feedback on our progress. Before D1, we met with Ralph on September 23 and September 30; the minutes are recorded in `/minutes`.
 * **Weekly TA meeting:** We meet with our TA online every Thursday from 7:00pm to 7:30pm to clarify course deliverable expectations, receive feedback on our process, and raise issues that cannot be resolved internally.
 * **Day-to-day collaboration:** We coordinate in Discord, track work in Jira, and use GitHub pull requests for code review. Each pull request is reviewed by at least one teammate before it is merged. We record meeting decisions and action items in the meeting minutes or the relevant Jira ticket.
  
#### Q9: How will you organize your team?

We use the tools provided by our partner, Savi Finance, as well as one of our own:
 * **Jira (Savi Finance):** our task board. Every piece of work is a ticket with one owner.
 * **Confluence (Savi Finance):** documentation, such as the architecture, technical designs and end-to-end user flows.
 * **Slack (Savi Finance):** questions and day-to-day communication with our partner.
 * **GitHub:** code, pull requests, documentation, and meeting minutes under `/minutes`.
 * **Discord (team only):** a separate server for communication within the team.

Our partner works in Jira, Confluence and Slack directly, and can see our code and notes on GitHub.

**Prioritization:** We prioritize work required for the MVP according to our partner's delivery plan.

**Assignment:** During our weekly team meeting, we assign tickets to team members based on their role and responsibilities. Each ticket has one owner. As team members complete their assigned work, they may take on unassigned tickets within their area of responsibility.

**Status:** Tickets move through the following stages: To Do, In Progress, In Review, and Done. The Jira board is the source of truth for ticket ownership and progress.

#### Q10: What are the rules regarding how your team works?

**Communications:**
 * Team: Discord for day-to-day communication. Everyone checks it daily and responds within one day. When a deadline is approaching, we respond within an hour.
 * Partner: Slack for questions and a weekly 20-minute meeting on Wednesdays at 6:00pm for more complex questions and technical blockers. Our partner liaison is responsible for communicating with the partner and passing updates to the team.

**Collaboration:**
 * Attendance and action items: If a member cannot attend a meeting, they notify the team via Discord beforehand and review the meeting notes afterward. Action items are recorded in `/minutes` or as Jira tickets with an owner, and we review them at the start of the next meeting.
 * Non-contribution or non-response: We escalate in steps. First, a direct ping in the group channel. If there is no response, a direct message to check in and offer help. If the issue remains unresolved, a message to the whole team, and finally we bring it to our TA.

## Organisation Details

#### Q11. How does your team fit within the overall team organisation of the partner?
* Given the team structure of your partner, what role do you think your team will play?
* Examples include product development that includes developing new features, or quality assurance that includes developing features that test the product reliability, or software maintenance that includes fixing crucial bugs in the product.
* Provide examples of why you think you fit this role.

Our team will primarily act as a small product development team within Savi Finance’s broader product and engineering organization. Savi Finance already has employees working across different areas of software engineering (like product, design, mobile, web dev, security), while our CSC301 team has been given focused ownership for a new feature area.

Therefore, our role is mainly new feature development. We are responsible for designing and implementing the group split and follow-up features within Savi Finance’s existing app and codebase, while working relatively independently on daily development. Ralph Maamari (CEO/founder) is our main partner contact, and has communicated that he will provide product direction, technical guidance, and support when we encounter larger design/engineering blockers.

We will also work within Savi Finance’s existing processes. Slack will be used for most communication, and also as a way to communicate with other Savi Finance team members (for example, we’ve been told to contact CTO Jun for complex technical questions). We’ve been added to Savi Finance’s Jira and Confluence, and those will be used for project tracking and communication. Finally, GitHub is for code implementation and PR review. Our changes are intended to be merged into the production codebase rather than delivered only as a separate prototype (see answer to next question).

Overall, we fit into Savi Finance as a temporary engineering squad focused on one feature. We will develop our assigned functionality, while their existing feature continues to develop the surrounding product.

#### Q12. How does your project fit within the overall product from the partner?
* Look at the big picture of the product and think about how your project fits into this product.
* Is your project the first step towards building this product? Is it the first prototype? Are you developing the frontend of a product whose backend is developed by the partner? Are you building the release pipelines for a product that is developed by the partner? Are you building a core feature set and take full ownership of these features?
* You should also provide details of who else is contributing to what parts of the product, if you have this information. This is more important if the project that you will be working on has strong coupling with parts that will be contributed to by members other than your team (e.g., from a partner).
* You can be creative for these questions and even use a graphical or pictorial representation to demonstrate the fit.
* Briefly specify what your partner considers a success for this project. Do they want you to build specific features? Publish a usable product? Just a prototype? Be as specific as you can be at this point.

Savi Finance is an already existing personal finance application, founded in 2022 and with 1.7k+ monthly users. This means that our project is adding our features directly into the existing product. Rather than building a standalone prototype, our team will take ownership of the Group Split feature from design through implementation and production deployment.

There is also some starter code in the repository from previous sprints. Our team can reuse, modify, or discard that code as needed, so we’re building on prior work if useful while still having full ownership of the feature’s final design and implementation.

Our feature will support one-off splits, group splits from receipts or existing transactions, tracking who owes/is owed money, and later voice/MCP interactions around these workflows.

Savi Finance’s goal for us is for the product to result in usable production functionality. At least three production pushes are expected during the term, with the first focused on one-off splitting and later releases expanding into the broader group-splitting experience.

## Potential Risks

#### Q13. What are some potential risks to your project?

1. **Tight timeline while still onboarding.**

Savi Finance expects one-off splits in production within about two weeks, at least three production pushes this term, and an approved technical design in Confluence before any major feature is built. We are still setting up the repo and learning the codebase, so the first push leaves little room for error, and a late first push would delay every later release.

2. **Some parts of the project are not clearly defined yet.**

The split and group features are well defined by Savi Finance's existing Jira tickets and Confluence specs. Other parts are less clear: what MCP control should do and who it is for, which voice agent settings users should be able to change, and whether people without Savi Finance accounts can be split with directly. Stories written before these are settled may be too abstract or may not match what Savi Finance exactly wants.

3. **Mistakes reach real users.**

Our code merges into Savi Finance's production app. A bug in the budget math or in balances would show real users wrong information about their finances.

#### Q14. What are some potential mitigation strategies for the risks you identified?

1. Keep the first push limited to one-off splits. Write its technical design first and get Ralph's sign-off early. Break work into small PRs (under 300 lines, per Savi Finance's guidelines).
2. Keep a running list of open questions and bring the most important ones to each meeting. Write stories for the first two pushes in full now, and add or refine later stories as they get clarified.
3. Write unit tests for split amounts and budget math. Test only with test accounts in Savi Finance's developer environment. Walk through the full user journey before each push.
