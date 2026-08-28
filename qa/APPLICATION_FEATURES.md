# Application Features

Tracks the real, implemented features of the digital-twin application. Populated/updated by `VisualQAAgent` and `FeatureDiscoveryHook`. Do not add a row until the feature actually exists in code.

| Feature ID | Feature Name | Description | Route | Page | Repository | Components | APIs | Services | Dependencies | Expected Behavior | Failure States | Security Considerations | Accessibility Considerations | Test Status | Last Tested | Last Passed | Last Failed | Known Issues | Related Test Cases |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| FEAT-001 | Health Check | Reports backend liveness/readiness | GET /health | n/a | backend | HealthController | GET /health | HealthService | none | Returns 200 with status payload | Backend down → connection error | No sensitive data in response | n/a | Pending | | | | | TC-001 |
| FEAT-002 | Document Upload | Uploads an approved knowledge document for ingestion | POST /upload-document | Upload page/panel | backend, frontend | UploadPanel | POST /upload-document | DocumentIngestionService | DocumentIngestionAgent pipeline | Valid doc accepted, chunked, embedded, indexed | Invalid type/size rejected with 4xx | File type/size validation, safe storage | Labeled file input, error text announced | Pending | | | | | TC-002, TC-003 |
| FEAT-003 | Chat / Ask Question | Ask a question and receive a grounded answer or refusal | POST /chat | Chat page | backend, frontend | ChatWindow, MessageInput, MessageList | POST /chat | ChatService, RetrievalService, GroundingService | Vector DB, LLM/embedding providers | Grounded answer for supported questions; generic refusal for unsupported | Backend/LLM unavailable → error state with retry | Prompt-injection resistant; no system prompt leakage | Live-region for new messages, keyboard-operable input/send | Pending | | | | | TC-004, TC-005, TC-006 |

*(Additional rows are added by VisualQAAgent as real features are discovered/built.)*
