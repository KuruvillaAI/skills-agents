# Regression Matrix

Tracks, per feature, which regression areas must be re-verified when that feature changes.

| Feature | UI | API | Integration | Visual | Error Handling | Security | Accessibility | Status |
|---|---|---|---|---|---|---|---|---|
| FEAT-001 Health Check | n/a | ✅ required | ✅ required | n/a | ✅ required | n/a | n/a | Pass |
| FEAT-002 Document Upload | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | Pass (manual valid and invalid paths) |
| FEAT-003 Chat / Ask Question | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | Pass |
| FEAT-004 LinkedIn Profile Knowledge Import | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | Pass |

FEAT-003 regression includes greeting handling (TC-007) plus supported-answer grounding and unsupported-question refusal (TC-004/TC-005); a greeting must not weaken the factual pipeline. Failure recovery is by re-entry and resend (TC-009); no dedicated Retry button is part of the observed UI.

## How to use
1. When a feature changes, find its row here.
2. Run automated + manual regression for every column marked "required".
3. Update `Status` to `Pass`/`Fail` with a link to the relevant `TEST_EXECUTION_HISTORY.md` entry.

## Run 2026-08-29 approval-check update
Manual invalid-upload, loading, controlled failure/recovery, keyboard, responsive, and console/network checks passed. Backend startup was verified and the automated regression suite completed with `173 passed, 1 warning`; this matrix records full regression sign-off.

## Run 2026-08-29 cache-busted deployed Visual QA
- FEAT-003: **Fail** for unsupported factual refusal (DEF-002); greeting, supported grounding, injection, and recovery passed.
- FEAT-004: **Blocked** for valid public profile and explicit linked-site behavior; unsafe URL rejection passed. Overall regression status: **Fail**.

## Run 2026-08-29 final deployed Visual QA
- FEAT-001 through FEAT-004 passed the requested deployed regression checks.
- FEAT-004 unsafe URL rejection, valid public-profile import, and linked public-site processing passed. Overall status: **Pass**.
- Automated regression passed: backend 180 tests with 1 warning; frontend 44 tests.

## 2026-08-29 VQA-2026-08-29-007
- FEAT-001, FEAT-002, and FEAT-003 regression areas passed in the deployed browser, including negative/security, loading/recovery, keyboard, mobile, and console/network checks.
- FEAT-004 exact requested-profile import is **Blocked** by LinkedIn's public authwall/HTTP 999. The actionable application response and alternatives passed; successful import cannot be verified without bypassing the wall.
- Automated regression passed: backend 181 tests with 1 warning; frontend 44 tests. Overall status: **Fail**, with the authwall as the sole blocker.
