---
applyTo: "backend/tests/**,frontend/tests/**,skills-agents/qa/**"
---

# Testing Instructions

- Every new production code unit (controller, service, repository, mapper, component, hook, service, pipeline stage) requires an automated test. No exceptions without an explicit, documented reason.
- Backend: unit tests mock collaborators (repositories, providers) and live under `tests/unit/<layer>/`; integration tests exercise real wiring for ingestion, retrieval, generation, and API and live under `tests/integration/<area>/`.
- Frontend: unit tests cover components/services/mappers/hooks in isolation; integration tests cover full chat workflows (ask → loading → response/refusal → retry → error).
- End-to-end coverage must include the full pipeline: upload → ingest → embed → index → ask → retrieve → ground → generate → display, plus a case verifying an unsupported question is refused.
- Automated tests are necessary but not sufficient: any UI- or workflow-affecting change also requires a `VisualQAAgent` manual verification pass before it can be marked done (see `qa.instructions.md`).
- Never delete or weaken a test to make it pass. If a test is wrong, fix the test with a clear justification, not the assertion alone.
- Security-relevant behavior (grounding refusal, prompt-injection resistance, upload validation, auth/authz) must have explicit negative tests, not just happy-path tests.
