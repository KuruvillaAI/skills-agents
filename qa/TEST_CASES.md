# Manual Test Cases

| Test Case ID | Feature | Preconditions | Steps | Expected Result | Actual Result | Status | Evidence | Date | Defect ID | Retest Status |
|---|---|---|---|---|---|---|---|---|---|---|
| TC-001 | FEAT-001 Health Check | Backend running | GET /health | 200 OK with `{"status":"ok"}`-style payload | HTTP 200; `{"status":"ok","app_name":"digital-twin-backend","vector_db_provider":"faiss","embedding_provider":"mock","llm_provider":"mock","document_count":2}` | Pass | Direct fetch from integrated browser | 2026-08-29 | | |
| TC-002 | FEAT-002 Document Upload (valid) | Upload page open | Select valid .txt/.md/.pdf under size limit; submit | Success message, feature status updates | `sample-knowledge-document.txt` accepted; UI reported indexed with 2 chunks | Pass | Upload status snapshot | 2026-08-29 | | |
| TC-003 | FEAT-002 Document Upload (invalid) | Upload page open | Select unsupported file type or oversized file; submit | Inline rejection, no ingestion | `frontend/package.json` was rejected with `Unsupported file type '.json'. Allowed types: .txt, .md, .pdf.`; indexed-document count remained 2 | Pass | Browser snapshot and 400 console event | 2026-08-29 | | |
| TC-004 | FEAT-003 Chat (supported question) | Document ingested | Ask a question answerable from the document | Grounded response with evidence | Returned Python answer and expandable `Sources (1)` evidence containing the document text | Pass | Chat snapshot and expanded source | 2026-08-29 | | |
| TC-005 | FEAT-003 Chat (unsupported question) | Document ingested | Ask a question unrelated to the document | Generic refusal message | Returned `I'm sorry, but I don't have enough information in my knowledge document to answer that.` | Pass | Chat snapshot | 2026-08-29 | | |
| TC-006 | FEAT-003 Chat (prompt injection) | Document ingested | Attempt to override system rules via chat input | Refusal/grounding holds; no leakage | Injection asking for system prompt and internal QA knowledge returned the generic refusal; no QA content disclosed | Pass | Chat snapshot | 2026-08-29 | | |
| TC-007 | FEAT-003 Chat (greeting) | Chat page open, document may or may not be ingested | Send `hi`, `hello`, or a time-of-day greeting | Natural conversational response; not the knowledge refusal; no evidence or personal facts are claimed | Returned `Hi! How can I help you?` with no source evidence | Pass | Chat snapshot | 2026-08-29 | | |
| TC-008 | FEAT-003 Chat loading state | Document ingested | Submit a supported question and inspect the request before completion | Loading indicator is visible and controls reflect in-flight state | `...` was visible in a 100 ms in-flight capture before the grounded response | Pass | Browser body capture during request | 2026-08-29 | | |
| TC-009 | FEAT-003 Chat failure and recovery | Document ingested | Abort one chat request, observe error, remove fault, re-enter the message, and resend | Clear error appears and re-entry/resend recovers | Controlled `POST /chat` abort showed the server error message; re-entering and resending then returned grounded `Sources (1)`. No dedicated Retry button was observed | Pass (resend recovery) | Browser body, requestFailed event, and follow-up response | 2026-08-29 | | |
| TC-010 | FEAT-003 Keyboard operation | Chat page open | Tab through Upload, textbox, and Send; submit with Enter | Focusable controls can be operated without a mouse | Upload and textbox received focus; Send received focus after typing; Enter on textbox and Send both submitted | Pass (tested controls) | Accessibility snapshots showing active elements and resulting messages | 2026-08-29 | | |

| TC-011 | FEAT-004 LinkedIn profile import (valid public source) | Public LinkedIn profile URL is accessible | Submit a public LinkedIn URL | Profile page and bounded explicit public links are summarized, indexed, and source count is returned | Public `https://www.linkedin.com/in/satyanadella` imported successfully; UI reported 6 public sources and 64 chunks | Pass | Integrated-browser transcript, 2026-08-29 | 2026-08-29 | | |
| TC-012 | FEAT-004 LinkedIn profile import (unsafe URL) | Import form available | Submit a non-LinkedIn, private-network, credential-bearing, or non-HTTPS URL | Request is rejected without fetching or indexing content | `https://example.com` returned `Please provide a public LinkedIn profile URL.` with HTTP 400 | Pass | Integrated-browser snapshot and network event, 2026-08-29 | 2026-08-29 | | |

*(Additional test cases are added as features are discovered/built and tested by VisualQAAgent.)*

## Run 2026-08-29: Cache-busted deployed Visual QA
- TC-001, TC-002, TC-004, TC-006, TC-007, TC-009 resend recovery, and TC-012 passed.
- TC-005 failed: France returned unrelated document content with `Sources (1)`, not refusal (DEF-002).
- TC-011 blocked: tested public LinkedIn URL redirected and could not be validated. Mobile geometry passed; keyboard/loading timing were not evidenced.

## Run 2026-08-29: Final deployed Visual QA
- TC-001 through TC-012 passed, including valid public LinkedIn import and linked public-site processing.
- Backend: 180 passed, 1 warning. Frontend: 44 passed.
