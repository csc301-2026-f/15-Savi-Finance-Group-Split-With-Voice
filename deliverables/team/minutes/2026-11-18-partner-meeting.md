# Partner Meeting - November 18, 2026

- Time (Toronto): 6:00–6:20 p.m.
- Format: Online
- Location: Online
- Partner: Ralph Maamari, Savi Finance

## Notes

- The team reviewed the receipt splitting UI. One-off splits (design fixes in progress), group split with receipt and group split from transactions (the split modal) are going well.
- Someone is working on the old widget, but no PR images have been shared. MCP control status is unclear.
- The biggest concern is the group feature (create a group, invite friends, log transactions). Only a rough design has been seen and its status is unclear; it will be revisited.
- A shared skill can help agents improve design work. Designs should still go through Gemini or Muse with human judgment, since AI design recommendations are often weak. AI still struggles with UI development; anyone who finds a working approach or tries the shared skill should report back.
- A captured receipt can lead to many actions: storing it in a folder, parsing it into a logged transaction, splitting it with others by voice or chat, or attaching it as an image to a transaction. Reuse existing components instead of rebuilding each flow.
- Using the Ask Savi architecture as a post-capture overlay supports these actions natively, for example routing to a split receipt agent. The agent could learn that a user always orders the burger and mango lassi at a location and split their portion automatically. The post-capture microphone should reuse the Ask Savi chat bar rather than being built from scratch.
- Consider every notification channel (email, text, voice calls for follow-ups, push) and reuse the existing back-end pipeline for each.
- Keep customization in settings rather than laid out on screen. Show one utility at a time, like Airbnb's search opening a dedicated pane. Avoid screens with 20 actions; make the next action obvious.
- CI/CD deploys automatically on merge; no new practices are needed despite the new test deployment flag.
- Merge early to allow testing on the real app, since production behaves differently from the simulator.
- Review each other's PRs and use AI first to raise quality before requesting approval. Feedback every three hours is possible but heavy.
- Decision: merge about 90% of PRs before next week's meeting.

## Action Items

- Ralph: review PRs shared through Slack links.
- Sumedh: check the status of the group feature design and circle back.
- Group split team: send a group split status update tonight.
- Everyone: share PR links in Slack once ready and review each other's PRs.
- Everyone: merge about 90% of PRs before next week's meeting.
