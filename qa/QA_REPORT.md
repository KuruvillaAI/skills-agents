# QA Report

## Current Status

```text
QA STATUS: FAIL
```

The deployed application passes the chat, grounding, security, and UI checks, but the requested LinkedIn profile is behind LinkedIn's authentication wall and cannot be fetched without signing in.

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
- [x] Required regression tests pass (backend 180 passed, 1 warning; frontend 44 passed)
- [x] Visual QA passes for the tested desktop/mobile states
- [x] QA documentation is updated

Otherwise: `QA STATUS: FAIL`, with the specific unmet criteria and blockers listed below.

## Latest Blockers

- The supplied profile redirects to LinkedIn's authentication wall and returns HTTP 999 to server requests. The application now reports this clearly and supports the documented alternatives: a publicly accessible URL, LinkedIn PDF export, or uploaded/pasted profile content.

Evidence is recorded in `TEST_EXECUTION_HISTORY.md` entry `VQA-2026-08-29-006`. Deployed source commits: backend `e43ab49` with grounding fix `b851c63`, frontend `93c3e0e`, skills `d02d80f`.
