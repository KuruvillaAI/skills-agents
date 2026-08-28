---
applyTo: "skills-agents/qa/**"
---

# QA Instructions

- QA knowledge (`skills-agents/qa/`) is internal and must never be exposed to the public chatbot or referenced in chatbot responses.
- QA documentation is living, not a one-time artifact. Every QA run must update: `APPLICATION_FEATURES.md`, `UI_ELEMENT_CATALOG.md`, `USER_WORKFLOWS.md`, `TEST_CASES.md`, `REGRESSION_MATRIX.md`, `DEFECT_LOG.md`, `TEST_EXECUTION_HISTORY.md`, `QA_CHANGELOG.md`, and `QA_REPORT.md`.
- Document only the actual, discovered application. Do not invent features, UI elements, or workflows before they exist in code.
- `TEST_EXECUTION_HISTORY.md` is append-only — never overwrite a previous execution record.
- Every feature must have related-area and negative-case coverage, not just a happy-path test (see `REGRESSION_MATRIX.md`).
- `VisualQAAgent` must run in the VS Code integrated browser against a started application; automated tests alone are not sufficient for QA sign-off.
- `QA STATUS: PASS` may only be declared when every criterion in `qa/QA_REPORT.md`'s approval checklist is satisfied and there are no unresolved BLOCKER defects.
