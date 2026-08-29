# Defect Log

Severity scale: `BLOCKER`, `CRITICAL`, `MAJOR`, `MINOR`, `TRIVIAL`.

| Defect ID | Title | Severity | Priority | Feature | Page | Environment | Steps | Expected | Actual | Impact | Component | API | Evidence | Console Error | Network Error | Git Commit | Status | Fix Commit | Retest Status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

| DEF-001 | Generic refusal returned for greetings | MAJOR | High | FEAT-003 | Chat | Deployed frontend/backend | Upload a document, then send `hi` | Conversational greeting | Generic knowledge refusal | Normal chat unusable for greetings | Backend ChatService | POST /chat | Automated regression added; deployment retest pending | None observed | None observed | Fix message replies | Fixed locally | Fix message replies | Pending deployment QA |

*(No defects recorded yet. VisualQAAgent appends a row here whenever a test fails, per `DefectLoggingHook`. Never delete a historical row — update `Status`/`Fix Commit`/`Retest Status` instead.)*
