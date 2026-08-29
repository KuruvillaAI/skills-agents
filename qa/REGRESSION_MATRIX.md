# Regression Matrix

Tracks, per feature, which regression areas must be re-verified when that feature changes.

| Feature | UI | API | Integration | Visual | Error Handling | Security | Accessibility | Status |
|---|---|---|---|---|---|---|---|---|
| FEAT-001 Health Check | n/a | ✅ required | ✅ required | n/a | ✅ required | n/a | n/a | Pending |
| FEAT-002 Document Upload | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | Pending |
| FEAT-003 Chat / Ask Question | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | ✅ required | Pending |

FEAT-003 regression includes greeting handling (TC-007) plus supported-answer grounding and unsupported-question refusal (TC-004/TC-005); a greeting must not weaken the factual pipeline.

## How to use
1. When a feature changes, find its row here.
2. Run automated + manual regression for every column marked "required".
3. Update `Status` to `Pass`/`Fail` with a link to the relevant `TEST_EXECUTION_HISTORY.md` entry.
