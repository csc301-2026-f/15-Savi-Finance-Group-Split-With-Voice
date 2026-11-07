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

**Sumedh**, Group expense save path: backend, integration and CI follow-up

- **Participant shares:** Made group-expense create save one debt row per non-payer participant, with idempotencyKey-derived IDs so retries are safe ([3a808a76f](https://github.com/cheapreats/ce/commit/3a808a76f)).
- **Share sync:** Update now rejects totals below the assigned shares, delete removes shares first, and get/list return shares ([770881293](https://github.com/cheapreats/ce/commit/770881293)).
- **Conflict detection:** Added a revision counter with an optional expectedRevision on update and delete. Delete claims the revision before removing shares ([4476cda63](https://github.com/cheapreats/ce/commit/4476cda63), [7fa92c487](https://github.com/cheapreats/ce/commit/7fa92c487)).
- **Settle and waive:** Guards run before settling, settle tracks revisions, and both operations keep stored shares and debt rows aligned ([20363d303](https://github.com/cheapreats/ce/commit/20363d303), [d4f7a39bf](https://github.com/cheapreats/ce/commit/d4f7a39bf)).
- **Integration:** Merged main three times, resolving group-transaction conflicts. Fixed mobile expense types and restored the shared Switch's press handling without editing tests ([6f47b2ccc](https://github.com/cheapreats/ce/commit/6f47b2ccc), [1000732d4](https://github.com/cheapreats/ce/commit/1000732d4), [8396ef5da](https://github.com/cheapreats/ce/commit/8396ef5da), [7ecdaae98](https://github.com/cheapreats/ce/commit/7ecdaae98), [1c101bd87](https://github.com/cheapreats/ce/commit/1c101bd87)).
- **Docs, UI and tests:** Rewrote the group expense method docs and regenerated API_DOC.md. Changed the "Total amount" label and added a settle-confirmation test ([7569abeaa](https://github.com/cheapreats/ce/commit/7569abeaa), [b4ea269cf](https://github.com/cheapreats/ce/commit/b4ea269cf), [b66b54ec5](https://github.com/cheapreats/ce/commit/b66b54ec5)).

**Implementation evidence:** [Integration PR #6761](https://github.com/cheapreats/ce/pull/6761), including commits [3a808a76f](https://github.com/cheapreats/ce/commit/3a808a76f) (participant shares and idempotent create), [4476cda63](https://github.com/cheapreats/ce/commit/4476cda63) (revision-based conflict detection), [20363d303](https://github.com/cheapreats/ce/commit/20363d303) (settle and waive) and [1c101bd87](https://github.com/cheapreats/ce/commit/1c101bd87) (shared Switch press fix).

**[Name]**, [Role]
> [Specific contributions]
