# QA Knowledge Base

This directory is the **internal QA knowledge domain** for the digital-twin project. It documents the *actual* application (features, UI, workflows, tests, defects, history) as discovered and verified by `VisualQAAgent` and the automated test suites.

> **This knowledge is internal.** It must never be exposed to the public-facing chatbot or referenced in a chatbot response. It is completely separate from the approved digital-twin knowledge document used to ground chatbot answers.

## Index

| File | Purpose |
|---|---|
| [APPLICATION_FEATURES.md](./APPLICATION_FEATURES.md) | Catalog of actual application features |
| [UI_ELEMENT_CATALOG.md](./UI_ELEMENT_CATALOG.md) | Catalog of discovered UI elements |
| [USER_WORKFLOWS.md](./USER_WORKFLOWS.md) | Documented end-to-end user workflows |
| [TEST_CASES.md](./TEST_CASES.md) | Manual test cases |
| [REGRESSION_MATRIX.md](./REGRESSION_MATRIX.md) | Feature → test-type regression coverage |
| [DEFECT_LOG.md](./DEFECT_LOG.md) | Defect tracking |
| [TEST_EXECUTION_HISTORY.md](./TEST_EXECUTION_HISTORY.md) | Append-only history of QA runs |
| [QA_CHANGELOG.md](./QA_CHANGELOG.md) | Changelog of QA-knowledge-base updates |
| [QA_REPORT.md](./QA_REPORT.md) | Current QA status and approval criteria |

## Rules

1. Document only the real, discovered application — never invent features, elements, or workflows that don't exist yet.
2. Update these documents after every `VisualQAAgent` run, per `QADocumentationHook`.
3. Never overwrite `TEST_EXECUTION_HISTORY.md` — always append.
4. Keep this knowledge base fully separate from `skills-agents/architecture/` (engineering knowledge) and the backend's `documents/` (public digital-twin knowledge).

## Latest QA run

Deployed-fix approval is recorded in `TEST_EXECUTION_HISTORY.md` as `VQA-2026-08-29-003`. Startup, the completed automated suite (`173 passed, 1 warning`), manual error/loading/grounding/security/accessibility/responsive checks, and console/network inspection passed. Current status: `QA STATUS: PASS`.
