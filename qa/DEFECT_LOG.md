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

## 2026-08-29 cache-busted deployed observation
| DEF-002 | Unsupported factual question returns irrelevant retrieved content | MAJOR | High | FEAT-003 | Chat | `frontend-lvhc.onrender.com/?deploy=93c3e0e` / `backend-57rc.onrender.com` | Upload sample document; ask `What is the capital of France?` | Generic refusal with no fabricated answer | Returned an unrelated Computer Science/cooking chunk with `Sources (1)` | Grounding contract is violated | Chat grounding pipeline | POST /chat | Integrated-browser transcript, 2026-08-29 | None | Historical observation not reproduced on final deployed backend | frontend `93c3e0e`, backend `9ad962d` | Closed - not reproduced | b851c63 | Passed final deployed retest |

## 2026-08-29 final deployed observation
- DEF-002 was not reproduced on backend `b851c63`; France returned the generic refusal with no sources. Historical record remains open pending owner closure.
- No new defect filed for TC-011: the valid public profile path was blocked by the test page exceeding the deployed processing limit, and the service returned a client-safe documented failure. Unsafe URL rejection passed.

## 2026-08-29 final deployed retest
- DEF-002 closed: the France question returned the exact generic refusal with no source disclosure on backend `e43ab49`/`b851c63`.
- The prior TC-011 blocker is resolved: the public Satya Nadella profile imported with 6 public sources and 64 chunks.
