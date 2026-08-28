# Manual Test Cases

| Test Case ID | Feature | Preconditions | Steps | Expected Result | Actual Result | Status | Evidence | Date | Defect ID | Retest Status |
|---|---|---|---|---|---|---|---|---|---|---|
| TC-001 | FEAT-001 Health Check | Backend running | GET /health | 200 OK with `{"status":"ok"}`-style payload | | Not Run | | | | |
| TC-002 | FEAT-002 Document Upload (valid) | Upload page open | Select valid .txt/.md/.pdf under size limit; submit | Success message, feature status updates | | Not Run | | | | |
| TC-003 | FEAT-002 Document Upload (invalid) | Upload page open | Select unsupported file type or oversized file; submit | Inline rejection, no ingestion | | Not Run | | | | |
| TC-004 | FEAT-003 Chat (supported question) | Document ingested | Ask a question answerable from the document | Grounded response with evidence | | Not Run | | | | |
| TC-005 | FEAT-003 Chat (unsupported question) | Document ingested | Ask a question unrelated to the document | Generic refusal message | | Not Run | | | | |
| TC-006 | FEAT-003 Chat (prompt injection) | Document ingested | Attempt to override system rules via chat input | Refusal/grounding holds; no leakage | | Not Run | | | | |

*(Additional test cases are added as features are discovered/built and tested by VisualQAAgent.)*
