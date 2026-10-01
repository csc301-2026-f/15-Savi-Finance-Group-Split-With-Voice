# Partner Meeting - September 30, 2026

- Partner: Ralph, Savi Finance
- Time: 6:00-6:20pm Toronto time
- Format: Online
- Notes source: [Shared meeting notes](https://notes.wisprflow.ai/shared/EINjAy10EC1hSHGIdWhYQ5TEYjq9Ljiszg-U7hs2bhE), titled "Group Split Voice Feature Kickoff", shared by Shaun.

## Logistics and Access

- Recurring meetings move to Wednesdays, 6:00-6:20pm, starting September 30.
- Team access is needed for Jira/Confluence, GitHub and Slack.
- Use Slack for questions; reserve meetings for hard problems and technical blockers.

## Project Scope

- The team owns design and implementation end-to-end.
- Existing code can be reused or discarded as appropriate.
- Workstreams: one-off splits; group splits from receipts with voice; group splits from transactions; owed/owing UI; MCP control.
- Voice follow-ups can use the existing voice infrastructure.

## Delivery

- At least three production pushes across the term.
- First push: one-off splits, targeted within the first two weeks.
- Second push: full group feature, including invites, transactions and owed/owing.
- Production deploys happen through PR merges. The notes identify John as the CTO who creates TestFlight/App Store builds.

## Decisions Recorded in the Shared Notes

- Reuse existing components and keep designs minimal.
- Ralph is the sole company contact; prior assignees were removed from Jira tickets.
- Portfolio use is encouraged. Share only code personally written; use screenshots or video of the final product for the portfolio.

## Action Items Recorded in the Shared Notes

- Ralph: move recurring meetings to Wednesdays, 6:00-6:20pm, starting September 30.
- Sumedh: email Ralph the team's GitHub usernames, with optional learning goals and career interests.
- Everyone: complete onboarding, product review, local development setup and the introduction email before the following week.

## Technical Tooling and Design Workflow

- Ralph demonstrated using Gemini with Canvas to redesign Figma screens from a screenshot and prompt.
- Prompt tips in the notes: use a senior-role framing and ask for step-by-step reasoning.
- Generate four to six variants, then focus a new thread on the selected design.
- Extend the root agents.md file when prompts become repetitive; changes go through PR review.
- Ralph plans to cover MCPs, voice-agent tuning and further AI concepts in later sessions.
- The notes discuss a semantic router for short yes/no voice replies as a latency option, with deeper discussion when the team needs it.
- The notes name LiveKit and Deepgram as stack components that can be replaced if there is a clear case for doing so.

These minutes summarize the supplied shared notes. Named action items are recorded assignments, not confirmation that they were completed. The note's displayed timestamp is not used as the meeting start time.
