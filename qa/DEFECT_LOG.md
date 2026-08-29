# Defect Log

Severity scale: `BLOCKER`, `CRITICAL`, `MAJOR`, `MINOR`, `TRIVIAL`.

| Defect ID | Title | Severity | Priority | Feature | Page | Environment | Steps | Expected | Actual | Impact | Component | API | Evidence | Console Error | Network Error | Git Commit | Status | Fix Commit | Retest Status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

| DEF-001 | Generic refusal returned for greetings | MAJOR | High | FEAT-003 | Chat | Deployed frontend/backend | Upload a document, then send `hi` | Conversational greeting | Generic knowledge refusal | Normal chat unusable for greetings | Backend ChatService | POST /chat | Automated regression plus deployed Visual QA on 2026-08-29 | None observed | None observed | a1e7d6c, 4f1fde2 | Fixed and retested | a1e7d6c | Passed deployed retest |

*(No defects recorded yet. VisualQAAgent appends a row here whenever a test fails, per `DefectLoggingHook`. Never delete a historical row — update `Status`/`Fix Commit`/`Retest Status` instead.)*

## 2026-08-29 approval-check observation
The controlled chat failure displayed the server-error message and recovered after re-entering and resending. No dedicated Retry control was present in the observed deployed error state; this remains a scope limitation because resend recovery is available through the existing input and Send controls.

## 2026-08-29 final approval observation
The deployed-fix approval run confirmed the controlled failure/re-entry/resend recovery, with no BLOCKER defects found. The absence of a dedicated Retry control is an observed UI characteristic, not a defect; the documented recovery path is re-entry and resend through the existing input and Send controls.
