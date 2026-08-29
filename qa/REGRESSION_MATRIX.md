# Regression Matrix

Tracks, per feature, which regression areas must be re-verified when that feature changes.

| Feature | UI | API | Integration | Visual | Error Handling | Security | Accessibility | Status |
|---|---|---|---|---|---|---|---|---|
| FEAT-001 Health Check | n/a | ✅ required | ✅ required | n/a | ✅ required | n/a | n/a | Pass |
| FEAT-002 Document Upload | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | Pass (manual valid and invalid paths) |
| FEAT-003 Chat / Ask Question | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | Pass |
| FEAT-004 LinkedIn Profile Knowledge Import | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | Pending |

FEAT-003 regression includes greeting handling (TC-007) plus supported-answer grounding and unsupported-question refusal (TC-004/TC-005); a greeting must not weaken the factual pipeline. Failure recovery is by re-entry and resend (TC-009); no dedicated Retry button is part of the observed UI.

## How to use
1. When a feature changes, find its row here.
2. Run automated + manual regression for every column marked "required".
3. Update `Status` to `Pass`/`Fail` with a link to the relevant `TEST_EXECUTION_HISTORY.md` entry.

## Run 2026-08-29 approval-check update
Manual invalid-upload, loading, controlled failure/recovery, keyboard, responsive, and console/network checks passed. Backend startup was verified and the automated regression suite completed with `173 passed, 1 warning`; this matrix records full regression sign-off.
