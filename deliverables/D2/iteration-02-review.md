# Team 15 — Savi Finance: Group Split with Voice

 > _Note:_ This document is meant to be written during (or shortly after) your review meeting, which should happen fairly close to the due date.      
 >      
 > _Suggestion:_ Have your review meeting a day or two before the due date. This way you will have some time to go over (and edit) this document, and all team members should have a chance to make their contribution.


## Iteration 02 - Review & Retrospect

 * When: October 22
 * Where: Online, an hour-long call on our Discord server

## Process - Reflection


#### Q1. What worked well

**1. Splitting work based on user stories**

One of the most effective decisions we made was splitting up the work based on user stories and assigning clear ownership to different team members. For example, we divided the splitting functionality into one-off splits, group splitting from receipts, and group splitting from transactions, with separate pairs responsible for each. This allowed us to work on different features in parallel while minimizing overlap and confusion about who was responsible for what. Having clearly defined responsibilities also made it easier to track progress and hold ourselves accountable for our respective tasks. This approach worked particularly well because the different pairs could independently make progress on their features, while still coordinating when their work needed to integrate.

**2. Consulting each other about shared and similar components**

Another process that worked well was discussing overlapping functionality between user stories before implementing it independently. This was especially important for the two group-splitting flows, since splitting from a receipt and splitting from a transaction require many of the same underlying features, such as participant selection, saving allocations, and displaying split summaries. Rather than having both pairs build separate implementations, we discussed which functionality should be shared and assigned ownership accordingly. For example, the receipt-splitting pair developed reusable components for group creation, which could also be used by the transaction-splitting pair. We also agreed on using a shared expense-saving system so that both flows would ultimately produce consistent balances. This coordination helped reduce duplicated effort, encouraged consistency across the application, and made integration between different features more manageable.

**3. Being flexible and willing to help each other**

Although we had assigned responsibilities, we were also willing to collaborate and help each other when necessary rather than strictly limiting ourselves to our own tasks. When someone needed clarification or input on an implementation decision, other team members were available to provide feedback. This flexibility was beneficial because it prevented individual tasks from becoming completely isolated and allowed us to make decisions with the overall project in mind. It also helped us maintain momentum and work more effectively as a team.


#### Q2. What did not work well

List **process-related** (i.e. team organization and how you work) decisions and actions that did not work well.

 * 2 - 4 important decisions, processes, actions, or anything else that did not work well for you, ordered from most to least important.
 * Give a supporting argument about what makes you think that way.
 * Feel free to refer/link to process artifact(s).

Possible Ideas -> Time management (starting slightly late gave less time for feedback), add more


#### Q3(a). Planned changes

List any **process-related** (i.e. team organization and/or how you work) changes you are planning to make (if there are any)

 * Ordered from most to least important, with supporting argument explaining a change.

1 - Most crucially, members will escalate to the team as quickly as possible in the event where they have a substantial change to their schedules. We've allocated work based on members' schedules for D2 while ensuring workload was as equitable as possible, but different members of the group had different commitments emerge that affected how soon they could get to their share of the work. We noticed in this iteration that having members communicate that allowed them to see how other members were using different tools to save time in their workflows, as well as seeing how code (either written by other members or on the Savi repository) could be re-purposed in ways they may not have seen earlier. Simply put, knowledge wasn't siloed when members escalated this week, so we hope to retain that as a standard practice to boost knowledge sharing. 

#### Q3(b). Integration & Next steps
Briefly explain how you integrated the previously developed individuals components as one product (i.e. How did you split the work across your team) and how was the work integrated together.

 * Keep this very short (1-3 lines).

We split the work by user story across pairs (one-off splits, group splits from receipts, group splits from transactions) and integrated through shared pieces, such as the receipt pair's reusable group components, which the transaction pair reused, and a common expense-saving backend so both group flows produce consistent balances. Internal demos before the partner meeting surfaced integration questions early. Next steps: allocation controls, balances and repayment, and protecting simultaneous edits to the same expense from the frontend.

## Product - Review

#### Q4. How was your product demo?
 * How did you prepare your demo?
 * What did you manage to demo to your partner?
 * Did your partner accept the features? And were there change requests?
 * What were your learnings through this process? This can be either from a process and/or product perspective.
 * *This section will be marked very leniently so keep it brief and just make sure the points are addressed*

 We demoed our progress on the four user stories to our partner during our weekly meeting. To prepare for this, each person or pair demoed their code/progress to the rest of the group during our own internal meetings. This allowed us to gather feedback and discuss how features would integrate together, including opportunities to reuse similar components. 

The overall demo to the partner went well. Ralph was pleased with our progress and accepted the path we went with most of the features, while requesting some changes regarding location and reusability. For instance, we had tacked on the receipt splitting workflow into the Groups section on the home page, but he wanted it integrated into the existing "Create Transaction -> Split" flow on another page. We were unaware of this route, and promptly made the switch over. Although nothing was wrong functionally, moving our code would help users find the new feature easier and removes unneeded duplication. Another suggestion he gave was to leverage AI tools further within our development process. This includes tools for AI-assisted code development, and other use-cases, like to automatically take screenshots and videos of new changes.

From our work on this deliverable, we learned to thoroughly explore existing components before creating our own. Although the large size of the codebase could make this difficult, this is a prime opportunity to use AI tools to help us. Internal demos also helped us identify integration questions before our partner meetings. Finally, we learned how to leverage modern tools in order to speed up some of our workflows, like repetitive development and verification work.
