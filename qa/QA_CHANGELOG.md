# QA Changelog

Chronological log of updates to the QA knowledge base itself (not application changes).

## Unreleased
- Initial QA knowledge base scaffold created: `QA_KNOWLEDGE_BASE.md`, `APPLICATION_FEATURES.md`, `UI_ELEMENT_CATALOG.md`, `USER_WORKFLOWS.md`, `TEST_CASES.md`, `REGRESSION_MATRIX.md`, `DEFECT_LOG.md`, `TEST_EXECUTION_HISTORY.md`, `QA_REPORT.md` with initial (pre-build) feature/UI/workflow expectations for FEAT-001..003.
- Added conversational greeting coverage (TC-007/WF-009), documented the grounding exception, and recorded DEF-001 pending deployed retest.
- Added FEAT-004 for public LinkedIn profile knowledge import and its unsafe-URL negative path.
- 2026-08-29: Recorded deployed Visual QA run VQA-2026-08-29-001 against commits `a1e7d6c` and `4f1fde2`; updated observed feature/UI/workflow/test/regression status; marked DEF-001 deployed retest passed; retained QA status as FAIL because invalid/error, loading, retry, and complete accessibility approval criteria were not fully exercised.
- 2026-08-29: Recorded post-deployment approval checks VQA-2026-08-29-002: unsupported `.json` upload rejection, in-flight `...` loading state, controlled `/chat` failure and resend recovery, keyboard focus/submit paths, mobile overflow check, and console/network evidence. Retained QA status as FAIL because startup was not initiated and automated regression was not run; no dedicated Retry control was observed.
- 2026-08-29: Finalized deployed-fix approval as VQA-2026-08-29-003: verified backend startup with `python -m uvicorn app.main:app --host 127.0.0.1 --port 8001`, recorded the completed automated suite (`173 passed, 1 warning`), and consolidated full manual evidence. Updated the QA report and regression status to PASS. Corrected the catalog and failure workflow to document observed re-entry/resend recovery; no Retry button is documented.
