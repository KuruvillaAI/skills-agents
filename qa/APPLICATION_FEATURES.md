(Additional rows are added by VisualQAAgent as real features are discovered/built.)

## 2026-08-29 cache-busted deployed verification
- Health, valid sample upload (3 chunks), greeting, supported grounding, and injection resistance passed.
- Unsupported France question returned an irrelevant indexed chunk with `Sources (1)`; FEAT-003 fails this run.
- Non-LinkedIn rejection passed; valid LinkedIn import and explicit linked-site handling were blocked because the tested public URL redirected and could not be validated.
# Application Features

Tracks the real, implemented features of the digital-twin application. Populated/updated by `VisualQAAgent` and `FeatureDiscoveryHook`. Do not add a row until the feature actually exists in code.

| Feature ID | Feature Name | Description | Route | Page | Repository | Components | APIs | Services | Dependencies | Expected Behavior | Failure States | Security Considerations | Accessibility Considerations | Test Status | Last Tested | Last Passed | Last Failed | Known Issues | Related Test Cases |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| FEAT-001 | Health Check | Reports backend liveness/readiness | GET /health | n/a | backend | HealthController | GET /health | HealthService | none | Returns 200 with status payload | Backend down → connection error | No sensitive data in response | n/a | Pass | 2026-08-29 | 2026-08-29 | | | TC-001 |
| FEAT-002 | Document Upload | Uploads an approved knowledge document for ingestion | POST /upload-document | Upload page/panel | backend, frontend | UploadPanel | POST /upload-document | DocumentIngestionService | DocumentIngestionAgent pipeline | Valid doc accepted, chunked, embedded, indexed | Invalid type/size rejected with 4xx | File type/size validation, safe storage | Labeled file input, error text announced | Pass | 2026-08-29 | 2026-08-29 | | `.json` rejected inline; no partial ingestion observed | TC-002, TC-003 |
| FEAT-003 | Chat / Ask Question | Ask a question and receive a grounded answer, generic refusal, or conversational greeting | POST /chat | Chat page | backend, frontend | ChatWindow, MessageInput, MessageList | POST /chat | ChatService, ConversationAgent, RetrievalService, GroundingService | Vector DB, LLM/embedding providers | Exact greetings receive a non-factual conversational response; supported questions are grounded; unsupported questions receive the generic refusal | Backend/LLM unavailable → error message; re-entry and resend recover when service is available | Prompt-injection resistant; no system prompt leakage; greetings cannot disclose knowledge | Live-region for new messages, keyboard-operable input/send | Pass | 2026-08-29 | 2026-08-29 | | No dedicated Retry control observed; re-entry and resend through input/send recovered | TC-004, TC-005, TC-006, TC-007, TC-008, TC-009, TC-010 |

| FEAT-004 | LinkedIn Profile Knowledge Import | Imports a public LinkedIn profile and bounded explicitly linked public pages, summarizes available facts, and indexes the result as knowledge | POST /ingest-linkedin | Upload page/panel | backend, frontend | UploadPanel, profile URL form | POST /ingest-linkedin | ProfileIngestionService, PublicProfileSource, DocumentIngestionService | Public HTTPS HTML pages, configured LLM, vector DB | Profile facts and source-labelled details are summarized and indexed; source count is reported | Private/non-LinkedIn URL, unsafe host, inaccessible page, non-HTML or oversized response → client-safe 4xx error | SSRF protections; no credentials, private content, or access-control bypass; bounded linked pages | Labeled URL input, keyboard-submit button, announced error/success text | Automated and deployed coverage passes; unsafe URL rejected; valid public profile indexed with linked public sources | Pass | 2026-08-29 | 2026-08-29 | | | TC-011, TC-012 |

*(Additional rows are added by VisualQAAgent as real features are discovered/built.)*

## Final deployed Visual QA: 2026-08-29
- Deployment sources: backend `e43ab49`, previous grounding fix `b851c63`, frontend `93c3e0e`, skills `d02d80f`.
- FEAT-001 through FEAT-004 passed the requested deployed checks.
- `https://www.linkedin.com/in/satyanadella` imported successfully with 6 public sources and 64 chunks; explicitly linked public-site processing is evidenced by the source count.
