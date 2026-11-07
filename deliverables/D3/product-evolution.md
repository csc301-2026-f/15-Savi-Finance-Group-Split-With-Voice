# YOUR PRODUCT/TEAM NAME

> Aim for 1000-2000 words. Be concise and analytical. We care about reasoning, impact, and integration quality, not length.

## 1. What Needed to Improve

Identify the most important gap or limitation after D2 and how you identified it.

Ideas:
- the key gap for our user stories was transforming from the task being functional to being production ready quality
- Responded to Savi Finance feedback, e.g. UI is poor
- whatever the gap is here is the gap that blocks us from doing our first big integration into prod

## 2. What You Did

Between deliverable 2 and 3, development mostly consisted of refining our existing draft PRs to be ready for integration using feedback from Savi Finance, so as per our original plan with Ralph (our industry partner representative), we can get the new work onto the main application and get user feedback. Thus, the sub-groups for group splitting and one-off splitting that were formed for D2 continued for D3 as well. The sub-group focused on group splitting (Sumedh, Praneeth, Shahmeer, Pranay, Sambhav) worked on UI refinements (i.e., making it less wordy), re-using components built by other Savi Finance developers and keeping our work synchronized with the main branch of the monorepo as program components evolved. Work that came out of this sub-group also included improvements in OCR accuracy and additions like accessibility labels, as well as type fixes. Similiarly, the sub-group focused on one-off splitting (Shaun, David) also made UI improvements, worked on save/edit reliability and retry handling and edge cases in split calculation, alongside implementing split email notifications. This group also repeatedly worked to keep their branch synchronized with main. Both groups have regression tests implemented for their scope of the work, and members of the group continue to extend Savi's test suite as they develop new frontend and backend features. Members also reviewed each other's work for their PRs. No key architectural or design changes were made from deliverable 2 to deliverable 3. However, integration challenges largely centered around keeping our work synchronized with main; we noted previously that Savi's codebase evolves rapidly (140k+ lines/week) and our group is limited in the visibility we have into what Savi's full-time developers are working on in parallel. As a result, we experienced issues such as being blocked on issues and CI failures in the main branch that don't relate to our work, having to re-write and modify prior work since similar implementations of some components we were working on reaching main before our work was pushed, and having to rebase all PRs, rerunning CI and fixing associated failures every time the base changes. Ultimately, we have completed all the work associated with our previously-opened PRs and are waiting on Savi to fix some CI issues on their end and approve our changes before we move forward with new feature development. 

Links to associated PRs: 
https://github.com/cheapreats/ce/pull/6761
https://github.com/cheapreats/ce/pull/6624
https://github.com/cheapreats/ce/pull/6768
https://github.com/cheapreats/ce/pull/6769

## 3. Before vs. After

Show concrete improvements: workflow clarity, speed, error reduction, reliability, etc.

Ideas:
Hard to say things like speed
Can talk about reliability in terms of less bugs -> more end-to-end flows tested
More CI Checks did pass now so maybe use that for error reduction

## 4. Reflection

What worked well, what was harder than expected, and how this affects your path to D4.

Ideas:
Add reflection
Looking forward
- getting things merged in (should be very soon)
- starting on voice and other things

In our work for deliverable 3, many things worked well for us in our development process. Primarily, preserving our original sub-groups was an optimal decision since we were mostly refining prior work; this proved to have its own challenges, so it helped members that had worked on a feature previously to have its context before attempting to refine it. Moreover, when members from one sub-group reviewed the work of the other, it allowed for newer insights to be uncovered into potential improvements. Also, we noticed in our work for D2 that work done by some members could be leveraged by others, both within and between sub-groups; consequently, we developed a shared "knowledge base" which is actively maintained and contains a list of components associated with each code path so we can see if anything can be reused. On the note of knowledge sharing, frequent communication with not only Ralph, but other developers from Savi Finance (i.e., Jun Zheng) was useful as it made the process of adapting to code changes simpler and gave us more clarity about the work we should actually be responsible for. In addition, using AI tools in our workflows proved to be especially helpful for us in the stretch of development between D2 and D3; with the codebase rapidly having changes made to its main branch, AI assistants helped to quickly surface which changes affected the code paths we were working on and what we'd need to do for them. AI tools were also useful for tasks beyond coding as well, such as capturing visuals for PR reviews. Several of these decisions were particularly useful in helping us navigate the blockers that came with a quickly-evolving codebase. The time taken to keep our respective branches up-to-date with Savi's main was far longer than anticipated. We found at different points that our CI would fail due to issues with code in the main branch that had no relation to our work. We were able to obtain some clarity and direction on these issues in discussions with Ralph and Jun, and what to leave to them to resolve on their end; fortunately, providing them with visibility into this has gotten us to a point where we've gotten our PRs to be ready for review. They should be merged very soon once all fixes are in. For this reason, we will provide smaller, more frequent updates of what we're working on to Ralph and Jun heading into D4. Doing so will allow us to see how we can independently move onto other parts of our project scope (e.g., voice features, MCP) without being roadblocked by in-flight Savi development. 

