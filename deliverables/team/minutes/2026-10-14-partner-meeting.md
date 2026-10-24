# Partner Meeting - October 14, 2026

- Time (Toronto): Not recorded
- Format: Not recorded
- Location: Not recorded
- Partner: Ralph Maamari, Savi Finance

## Notes

- Ralph reviewed the group split architecture document. The target is merged group and one-off split PRs before the following week's partner meeting, with working software to demonstrate to the TA.
- The seven-person team discussed workload. Sambhav proposed taking group creation and one-off splits. Ralph considered one-off splitting nearly built and group splitting a relatively small change; widget and MCP work could each have one owner. Voice follow-up requires more onboarding time.
- Ralph emphasized design and usability alongside implementation. Compare the app before and after changes; the existing Figma designs are outdated.
- Designs should show the complete group flow, including what opens after tapping Groups and how members and percentages are selected.
- Reuse existing transaction and widget components to avoid redundant code, including duplication introduced by AI tools.
- Voice follow-up designs need to explain that debtors may receive calls and show where users configure the follow-up strategy. Split-related Insights changes also need design coverage.
- Ralph encouraged AI-assisted development and design using tools such as Claude, Codex, Anti-Gravity and Muse. He mentioned free options, a Muse token offer with a 24-hour claim window, and a cheaper model rather than frontier models for this work.
- Teaching staff are already invited to Savi's monorepo; implementation code does not need to be copied into the course repository for D2.
- Ralph explained that merged PRs auto-deploy. Open PRs early with visual screenshots, share links in Slack, and request review.
- The agreed ownership model is one person per user story, covering frontend through backend.
- Include the Jira ticket ID in PR titles, such as WI-3841, to synchronize status. Agent instructions for Jira synchronization may need documentation; Ralph welcomed a configuration PR.

## Action Items

- Ralph: share the Muse token offer with the team.
- Development team: complete group and one-off split work and open PRs early enough to merge before the next partner meeting.
- Development team: include visual screenshots, post PR links in Slack, and request Ralph's review.
- Development team: review architecture-document comments and update the end-to-end designs, including voice follow-up and split-related Insights behavior.
