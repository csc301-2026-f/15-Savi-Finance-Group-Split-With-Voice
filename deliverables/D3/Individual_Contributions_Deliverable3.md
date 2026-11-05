# Savi Finance — Individual Contributions (D3)

> For each team member: name, role, and specific contributions. Be precise about what you did, not how much you wrote.

**Praneeth**, Receipt splitting, OCR improvements, accessibility and development documentation

Improved the receipt split flow based on Ralph's feedback, addressed receipt-reading errors, and documented how our team uses Savi's testing and development setup.

- **Receipt split UI:** Reworked the flow so users see and correct the captured receipt before splitting, with Savi's existing AI controls on the preview. Simplified crowded screens and wording, moved review actions to the bottom, and added a button to split all items equally.
- **OCR accuracy:** Investigated cases where receipt reading dropped cents, missed tax or tip, or misread item rows. Tried different extraction and image-reading strategies, added regression tests, and checked results using clear, blurred, small and cropped receipt images. Uncertain amounts stay available for the user to correct, since perfect accuracy is practically unattainable.
- **Receipt corrections and totals:** Fixed cases where tax was counted twice because it was already included in item prices. Also addressed missing charges being treated as zero and quantities being counted twice, while keeping receipt fields editable before saving.
- **Accessibility and usability:** Added descriptive labels to receipt fields and controls, marked section headings and error messages for accessibility tools, and improved scrolling and keyboard handling. Made selected and unselected people easier to distinguish when assigning items.
- **Receipt previews and testing:** Fixed the local issue that blocked users from viewing their uploaded receipt. Verified the preview in the iOS simulator and added checks for secure uploads and downloads. Maintained the receipt handoff document with setup instructions, test results and remaining limitations.
- **Course README:** Added the D3 section explaining Savi's existing CI/CD process, our testing tools and methods, and the development/review workflow. Linked relevant workflows and test files, documented the partner's release constraints, and provided commands that teaching staff can run. Verified the quick test selection with 66 passing tests.

**Implementation evidence:** [Integration PR #6761](https://github.com/cheapreats/ce/pull/6761), including commit [47445ab64](https://github.com/cheapreats/ce/commit/47445ab64). The documentation changes are in the [course README](../../README.md#development-process-and-infrastructure-d3).

**[Name]**, [Role]
> [Specific contributions]

**[Name]**, [Role]
> [Specific contributions]

**[Name]**, [Role]
> [Specific contributions]

**[Name]**, [Role]
> [Specific contributions]
