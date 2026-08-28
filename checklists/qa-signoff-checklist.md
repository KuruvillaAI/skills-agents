# QA Sign-Off Checklist

- [ ] Application starts successfully
- [ ] All pages load without console errors
- [ ] Critical UI elements are present and functional
- [ ] Feature(s) under test behave as documented in `qa/APPLICATION_FEATURES.md`
- [ ] Related workflows in `qa/USER_WORKFLOWS.md` pass
- [ ] Negative/error cases behave correctly
- [ ] Responsive behavior verified (desktop + mobile)
- [ ] Accessibility-critical interactions verified
- [ ] Grounding verified: supported question → grounded answer; unsupported → refusal
- [ ] Prompt injection attempt does not bypass grounding/security
- [ ] `qa/REGRESSION_MATRIX.md` reviewed and required areas re-tested
- [ ] `qa/TEST_EXECUTION_HISTORY.md` appended with this run
- [ ] `qa/QA_REPORT.md` updated with current status
