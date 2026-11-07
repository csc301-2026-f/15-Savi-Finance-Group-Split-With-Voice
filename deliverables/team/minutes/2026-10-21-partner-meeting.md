# Partner Meeting - October 21, 2026

- Time (Toronto): Not recorded
- Format: Not recorded
- Location: Not recorded
- Partner: Ralph Maamari, Savi Finance

## Notes

- The team showed the one-off split backend PRs and receipt and group split demos. Ralph set PR verification rules, asked the team to reuse existing transaction UI and outlined next week's deliverables.
- Sumedh Gadepalli flagged that the team fell short of last week's MVP promise because of midterms and interviews, though everyone has started coding.
- Ralph asked members to say early if blockers are about experience rather than time. He urged delegating to AI in short bursts and focusing effort on verifying and reviewing its output.
- Ralph suggested building a skill that posts per-person commitments to Slack with linked Jira tickets.
- David Daniliuc shipped a five-PR backend stack covering models, APIs and balancing. PRs 6 to 9 cover the split editor, save and reopen, analytics and an end-to-end test.
- PR 6, the split editor frontend, is drafted. It works on Android but not iOS, and this is under investigation with a teammate not identified in the summary.
- Ralph's force pushes were only merge-conflict fixes, caused by heavy merging on the repo.
- PR verification should be produced by AI running the iOS and Android simulators, with before and after screenshots attached automatically.
- PR descriptions should be cleaned of AI slop. Screenshots can optionally go through Gemini with Canvas or Muse for design review.
- To get faster review, add Ralph as a reviewer through the settings icon and post PR links in the Slack group chat.
- Every team member is expected to review teammates' PRs, with or without AI help.
- Speaker 3 (not identified in the summary) demoed a receipt split screen built under a diagnostics-enabled groups tab. It duplicates existing transaction split UI.
- Voice split already works (Shahmeer Khan). The remaining work is moving it to wherever a receipt photo is taken.
- Discoverability is key. Ralph's gut pick is a "Split with voice" card on the photo preview with a short explanation.
- Sumedh built the group expense backend: per-participant shares, retries, sync on edits and deletes, who-owes-what lists and concurrency handling.
- Ralph called this a refinement week and deferred one topic to next week, when a helpful tool should be ready.
- Voice agent experience is in high demand. Ralph offered training, free voice credits and possible job referrals.
- Decision: frontend PRs need iOS and Android screenshots or video; backend PRs must show JSON responses, not just passing tests.
- Decision: receipt and group split reuse the existing transaction split UI instead of a separate one.
- Decision: voice features are left out of next week's scope.
- Decision: email notifications can go in a separate PR but must include a rendered image of the email.

## Action Items

- Ralph Maamari: paste receipt split flow notes into the chat for Speaker 3.
- Speaker 3 (not identified in the summary): design an end-to-end receipt voice split flow in Muse or Gemini with Canvas and get approval in chat.
- Speaker 3 (not identified in the summary): move receipt split into the existing transaction and add receipt flow, reusing current UI.
- David Daniliuc: add a verification loop (iOS and Android screenshots or video) to PR 6 before review.
- David Daniliuc: fix the PR 6 frontend not rendering on iOS.
- Jun: get the OpenRouter key for receipt scanning.
- Team: by next Wednesday, integrate UI refinements, build the remaining group components and screens and the Owing widget, with analytics impact as a bonus.
