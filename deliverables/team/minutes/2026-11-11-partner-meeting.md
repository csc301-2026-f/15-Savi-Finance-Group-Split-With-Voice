# Partner Meeting - November 11, 2026

- Time (Toronto): 6:00–6:20 p.m.
- Format: Online
- Location: Online
- Partner: Ralph Maamari, Savi Finance

## Notes

- The team reviewed receipt split designs. The team is third of the three CSC301 teams working with Savi and needs a design lift to catch up.
- The integrate receipt split draft PR bundles many features and blocks new branch work through constant syncing. Options are splitting out changes, stacking PRs, or merging behind a feature flag to remove risk.
- Ralph has no tolerance for AI-generated UI clutter: too much UI, long text and around 30 input fields on one screen.
- The receipt split add-transaction form differs from the regular one. Reuse existing components such as tip, total and line items; new components add maintenance cost and force users to learn unfamiliar UI.
- Iterate designs with Gemini with Canvas, or prompt Claude or Codex to reuse components and improve the design. The latest video has fewer words but still has stray input fields, and screenshots should show where each flow starts.
- Teammates should review PRs, including a visual design check, before Ralph reviews them. Ralph offered design reviews as often as daily, with the aim of finishing iteration within one week.
- Work in pairs: one person codes while the other critiques screenshots in Gemini.
- Phase one covers widgets, the group screen with its transaction list, adding transactions, receipt splitting and one-off splits. Voice is phase two.
- Confirm that push notifications and emails fire on group invites and group transaction splits.
- Decision: phase one PRs are to be merged and deployed to TestFlight by next week.

## Action Items

- Sumedh: release design updates and request reviews daily or every two days, reducing clutter and reusing components.
- Ralph: review and merge PRs posted in Slack, including Shaun's and David's.
- Praneeth: tell Shaun and David to post their PR links in Slack for review and merge.
- Praneeth: post where each flow starts alongside design videos and screenshots.
- Development team: merge phase one PRs and deploy to TestFlight by next week.
