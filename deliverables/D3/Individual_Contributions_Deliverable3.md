# Savi Finance — Individual Contributions (D3)

> For each team member: name, role, and specific contributions. Be precise about what you did, not how much you wrote.

**Praneeth**, Receipt splitting, OCR improvements, accessibility and development documentation

- **Receipt split UI:** Reworked the flow so users see and correct the captured receipt before splitting, with Savi's existing AI controls on the preview. Simplified crowded screens and wording, moved review actions to the bottom, and added a button to split all items equally.
- **OCR accuracy:** Investigated cases where receipt reading dropped cents, missed tax or tip, or misread item rows. Tried different extraction and image-reading strategies, added regression tests, and checked results using clear, blurred, small and cropped receipt images. Uncertain amounts stay available for the user to correct, since perfect accuracy is practically unattainable.
- **Receipt corrections and totals:** Fixed cases where tax was counted twice because it was already included in item prices. Also addressed missing charges being treated as zero and quantities being counted twice, while keeping receipt fields editable before saving.
- **Accessibility and usability:** Added descriptive labels to receipt fields and controls, marked section headings and error messages for accessibility tools, and improved scrolling and keyboard handling. Made selected and unselected people easier to distinguish when assigning items.
- **Receipt previews and testing:** Fixed the local issue that blocked users from viewing their uploaded receipt. Verified the preview in the iOS simulator and added checks for secure uploads and downloads.
- **Course README:** Added the D3 section explaining Savi's existing CI/CD process, our testing tools and methods, and the development/review workflow. Linked relevant workflows and test files, documented the partner's release constraints, and provided commands that teaching staff can run. Verified the quick test selection with 66 passing tests.

**Implementation evidence:** [Integration PR #6761](https://github.com/cheapreats/ce/pull/6761), including commits [47445ab64](https://github.com/cheapreats/ce/commit/47445ab64) (UI refinements and receipt extraction improvements) and [9a5f45692](https://github.com/cheapreats/ce/commit/9a5f45692) (accessibility and non-functional test coverage). The documentation changes are in the [course README](../../README.md#development-process-and-infrastructure-d3).

**Shaun Danny**, One-off split integration, notifications and review follow-up

- Implemented the default-off split email-delivery follow-up, added backend regression coverage, and synchronized it with David's updated split stack ([#7452](https://github.com/cheapreats/ce/pull/7452)).
- Separated the Android API compatibility guard into its own PR and documented verification limits; full Android privacy-blur parity remains follow-up work ([#7453](https://github.com/cheapreats/ce/pull/7453)).
- Reviewed David's split PRs, coordinated re-review of the one-off stack, and documented outstanding review and rollout requirements.
- Added the one-off flow, API/state references, setup flags and test guidance to the shared splitting knowledge base; prepared D3 slides, demo screenshots and report material.

The email and Android follow-up PRs were still draft at the last verified status. David's lifecycle fixes and final cross-platform verification are not claimed as my individual work.

**Shahmeer**, Receipt splitting: integration fixes, verification and code review

- **Integration fixes:** Fixed the 15 new TypeScript errors on the receipt-split integration PR (0 new in the full type check). Two were real bugs: unreadable receipt prices were copied into the form without an amount, and a receipt-save test never actually ran ([1493e0c93](https://github.com/cheapreats/ce/commit/1493e0c93)).
- **Backend tests:** Added Go tests for the receipt changes to Savi's OpenRouter client (verification fake, decimal amounts, JSON-schema responses, image detail), clearing the CI test-coupling gate ([5b48a95c4](https://github.com/cheapreats/ce/commit/5b48a95c4)).
- **Code review:** Reviewed teammates' PRs before partner review: [#6770](https://github.com/cheapreats/ce/pull/6770), [#6605](https://github.com/cheapreats/ce/pull/6605) and [#6624](https://github.com/cheapreats/ce/pull/6624). Authors fixed every posted finding, including an unenforced feature flag, missing database indexes and mixed-currency totals.
- **End-to-end verification and walkthrough:** Ran the integration branch against a local Savi backend and recorded the two-person [walkthrough video](https://drive.google.com/file/d/1_RcoIVwYVeFO3oh8SeUBXMU0YUKbhP6R/view?usp=sharing) linked in the README: one user scans a real receipt, assigns items with a typed sentence and saves; the other sees what they owe. Added the video and before/after screenshots to the README, and found two existing bugs (email invites from group creation never reach the invitee; Feature Flags toggles don't respond to taps).

**Implementation evidence:** [Integration PR #6761](https://github.com/cheapreats/ce/pull/6761). The receipt allocation math, participant picker, item assignment and voice/typed assignment I built for D2 are in [#6759](https://github.com/cheapreats/ce/pull/6759).

**David Daniliuc**, One-off split: review fixes, integration and verification

- Made retries repair pending budget alerts after a failed create ([85c7a66d3](https://github.com/cheapreats/ce/commit/85c7a66d3)) and finish pending deletion effects, with restore waiting until they complete. Also protected same-currency account updates against concurrent changes and made purge retries succeed if the account is already gone ([fddf9b131](https://github.com/cheapreats/ce/commit/fddf9b131)).
- Reconciled deletions before hiding sources, excluded trashed items from analytics ([68b8e94b2](https://github.com/cheapreats/ce/commit/68b8e94b2)), and fixed a $0 own share being grouped as income ([7162fb3cb](https://github.com/cheapreats/ce/commit/7162fb3cb)).
- Following Shahmeer's review, blocked guest actions unless the rollout flag is on, added guest indexes, and replaced raw user IDs with full names ([a691d3fd2](https://github.com/cheapreats/ce/commit/a691d3fd2)).
- Fixed saving transaction details on an unchanged split ([1ad8b0f5d](https://github.com/cheapreats/ce/commit/1ad8b0f5d)), removed PR numbers from the editor copy ([6817445c0](https://github.com/cheapreats/ce/commit/6817445c0)), and wrote the Android guard now in Shaun's [#7453](https://github.com/cheapreats/ce/pull/7453) ([631cad1dd](https://github.com/cheapreats/ce/commit/631cad1dd)).
- Addressed and resolved review threads across all 8 PRs ([#6605](https://github.com/cheapreats/ce/pull/6605)–[#6609](https://github.com/cheapreats/ce/pull/6609), [#6624](https://github.com/cheapreats/ce/pull/6624), [#6768](https://github.com/cheapreats/ce/pull/6768), [#6769](https://github.com/cheapreats/ce/pull/6769)), merged Savi's main through the stack, and updated tests for main's changes ([cbd6bc9e3](https://github.com/cheapreats/ce/commit/cbd6bc9e3)). Ran 543/543 Bazel API tests and 855 Jest tests before pushing; CI then passed on all 8.

As of November 6, none are merged: [#6607](https://github.com/cheapreats/ce/pull/6607) and [#6768](https://github.com/cheapreats/ce/pull/6768) are approved, and [#6605](https://github.com/cheapreats/ce/pull/6605) is back in draft with new conflicts against main. The other person's debt is only available through the API; no screen shows it yet.

**[Name]**, [Role]
> [Specific contributions]
