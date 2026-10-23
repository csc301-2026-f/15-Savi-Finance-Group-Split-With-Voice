# Team 15 — Savi Finance Group Split With Voice

## Iteration 02 - Review & Retrospect

 * When: October 22
 * Where: Online, an hour-long call on our Discord server

## Process - Reflection


#### Q1. What worked well

1. **Splitting the work by user story.** Each sub-team owned one story end to end, so ownership was clear, we worked in parallel, and each pair could demo and explain its own feature.
2. **Agreeing early on what is shared.** Our work-split document colour-codes which shared parts (groups and participants, the confirmation summary, saving) each pair owns, and lists everyone's planned PRs. We built shared pieces once instead of twice; for example, the participant picker and split summary are reused by both splitting flows.
3. **Internal demos before partner meetings.** Demoing to each other first surfaced integration questions early, so the partner demo showed connected progress rather than isolated pieces.

#### Q2. What did not work well

1. **Building before checking existing flows.** We added receipt splitting under Groups before noticing the existing Create Transaction → Split flow, and our partner asked us to move it, which cost rework.
2. **Slow development setup.** Getting Savi's large monorepo running locally (simulator builds, code signing, backend build tools) took some of us several days, delaying when we could test changes in the app.
3. **Sub-teams depending on one shared piece.** Receipt and transaction splits both need the shared save path to create real debts, so they can be demoed but not saved until it lands.

#### Q3(a). Planned changes

1. **Check the existing app before building**, using AI tools to search the codebase as our partner suggested, so new features go where users expect them.
2. **Finish shared dependencies first**, starting with the save path, then merge the rest as smaller stacked PRs instead of one large one.
3. **Keep setup notes, test accounts and feature-flag steps in one place**, so nobody has to solve the same setup problems again.
4. **Set earlier internal deadlines** to leave time for review and partner feedback.

#### Q3(b). Integration & Next steps

Each sub-team built its story on its own branch, reusing shared components where flows overlap. An integration branch ([cheapreats/ce#6761](https://github.com/cheapreats/ce/pull/6761)) combines them; next we land the shared save path and merge into `main` as smaller stacked PRs.


## Product - Review

#### Q4. How was your product demo?

We demoed our progress on the four user stories to our partner during our weekly meeting. To prepare for this, each person or pair demoed their code/progress to the rest of the group during our own internal meetings. This allowed us to gather feedback and discuss how features would integrate together, including opportunities to reuse similar components. 

The overall demo to the partner went well. Ralph was pleased with our progress and accepted the path we went with most of the features, while requesting some changes regarding location and reusability. For instance, we had tacked on the receipt splitting workflow into the Groups section on the home page, but he wanted it integrated into the existing "Create Transaction -> Split" flow on another page. We were unaware of this route, and promptly made the switch over. Although nothing was wrong functionally, moving our code would help users find the new feature easier and removes unneeded duplication. Another suggestion he gave was to leverage AI tools further within our development process. This includes tools for AI-assisted code development, and other use-cases, like to automatically take screenshots and videos of new changes.

From our work on this deliverable, we learned to thoroughly explore existing components before creating our own. Although the large size of the codebase could make this difficult, this is a prime opportunity to use AI tools to help us. Internal demos also helped us identify integration questions before our partner meetings. Finally, we learned how to leverage modern tools in order to speed up some of our workflows, like repetitive development and verification work.
