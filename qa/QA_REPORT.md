# QA Report

## Current Status

```text
QA STATUS: FAIL
```

The deployed application passes the chat, grounding, security, and UI checks. The exact requested LinkedIn profile is publicly redirected by LinkedIn to an authentication wall/HTTP 999 and cannot be fetched without signing in.

## Approval Criteria

`QA STATUS: PASS` requires all of the following:

- [x] Application starts (verified with `python -m uvicorn app.main:app --host 127.0.0.1 --port 8001`)
- [x] Pages load
- [x] Critical UI works for the tested paths
- [ ] Features work for the tested paths (the supplied LinkedIn profile is not publicly accessible)
- [x] APIs work for health, upload, and chat
- [x] Integration works for upload-to-grounded-chat
- [x] Grounding works (supported answer included `Sources (1)`; France returned no sources)
- [x] Unsupported questions are refused
- [x] Prompt injection protection works for the tested probe
- [x] Error handling works (invalid upload rejected; controlled backend-unavailable error recovered by resend)
- [x] Loading states work (disabled controls and in-flight `...` observed)
- [x] Responsive UI works at 390x844 with no horizontal overflow
- [x] Accessibility-critical flows work (Tab focus and Enter submission observed)
- [x] No unresolved BLOCKER defects
- [x] Required regression tests pass (backend 181 passed, 1 warning; frontend 44 passed)
- [x] Visual QA passes for the tested desktop/mobile states
- [x] QA documentation is updated

Otherwise: `QA STATUS: FAIL`, with the specific unmet criteria and blockers listed below.

## Latest Blockers

- The exact supplied profile `https://in.linkedin.com/in/kuruvilla-biju-cheruvallil` publicly redirects to LinkedIn's authentication wall and returns HTTP 999 to server requests. The application reports this clearly and supports the documented alternatives: a publicly accessible URL, LinkedIn PDF export, or uploaded/pasted profile content. This is the sole blocker; no bypass was attempted.

Evidence is recorded in `TEST_EXECUTION_HISTORY.md` entry `VQA-2026-08-29-007`.

## Latest Run

- Exact profile response: actionable access-wall message, not `profile page could not be fetched`.
- Health: HTTP 200; sample upload: indexed in 3 chunks.
- Chat: exact requested prompts exercised; grounded answers included `Sources (1)` and `Sources (2)` where supported; unrelated and injection probes returned the generic refusal.
- Loading, controlled error/recovery, keyboard, 390x844 responsive, console, and network checks passed.
- Backend: 181 passed, 1 warning. Frontend: 44 passed.
- `QA STATUS: FAIL` solely because the exact profile cannot be imported through LinkedIn's public authwall/HTTP 999.
