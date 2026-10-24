# Team Meeting - October 17, 2026

- Time (Toronto): Not recorded
- Format: Not recorded
- Location: Not recorded
- Participants: Project team; no TA present

## Notes

- The team planned D2 implementation with a 2–2–2–1 split: two people on one-off splits, two on receipt-based group splits, two on transaction-based group splits, and one on the owed/owing widget.
- The target is finished, individually verified PRs by Monday, October 19, leaving time to combine and refactor the work before the Wednesday partner demo. The course writeup follows that demo.
- The team understood Ralph's priority as building group splitting and completing one-off splitting, but needed clarification about the remaining one-off scope.
- A Codex review discussed during the meeting found existing one-off mobile and backend code only partially met acceptance criteria. Reported gaps included an error for totals differing by more than one dollar and per-person balance updates. These were planning observations, not a final verification of the implementation.
- The technical design also lists an owed/owing widget, split-creation email notifications, UI updates and MCP control. Voice and MCP control were deferred to later deliverables.
- Preselected splitting means reusing a group's previous amounts or percentages, with user edits allowed; no predictive model is required. This belongs to the group-splitting teams.
- The owed/owing widget shows home-screen totals with a per-person breakdown on tap. The meeting's estimate was roughly 45 minutes of work.
- Reuse existing frontend components, following Ralph's feedback. The four group-splitting developers coordinate as one sub-team because their code overlaps.
- Each person implements their part, then duplicated code is consolidated into shared objects and endpoints. Email notification infrastructure has one owner and is reused across features.
- The team needs Ralph to clarify whether he wants one combined PR or a PR per major user story. PRs should include designs and screenshots.

## Action Items

- Speaker 1 (not identified in the summary): own shared email notification infrastructure and work on one-off splits with the teammate named Sean in the summary.
- Speaker 2 (not identified in the summary): ask Ralph which one-off updates are required and how he wants PRs delivered.
- Everyone: finish and verify individual PRs by Monday, October 19, so the team can combine and refactor them.
- Group-splitting sub-team: coordinate shared components and consolidate duplicate objects and endpoints during integration.
- Team: complete the D2 course writeup after the Wednesday partner demo.
