---
applyTo: "backend/**"
---

# Backend Instructions

- Stack: Python 3.11+, FastAPI, Pydantic v2, pytest, uvicorn. Use `async def` route handlers and I/O where it adds real value (LLM calls, network I/O); do not force async on pure CPU-bound code.
- Structure: `app/controllers`, `app/services`, `app/models`, `app/mappers`, `app/interfaces`, `app/repositories`, `app/dependencies`, `app/middleware`, `app/configuration`, `app/exceptions`, `app/utils`, `app/main.py`.
- Every service and repository must be defined behind an interface in `app/interfaces/` and injected via FastAPI's `Depends` (see `app/dependencies/`). Do not `import` a concrete implementation directly inside a controller or another service — depend on the interface.
- Exposed endpoints: `POST /chat`, `POST /upload-document`, `POST /ingest-linkedin`, `GET /health`. Keep the OpenAPI schema accurate — every request/response model must be a Pydantic model.
- Configuration (embedding provider, LLM provider, vector DB backend, thresholds, secrets) must come from environment variables via `app/configuration`, validated at startup with Pydantic settings. Never hardcode API keys or secrets; see `.env.example`.
- Errors must be translated to structured JSON responses with an appropriate HTTP status via `app/exceptions`; never leak stack traces or internal file paths to the client.
- Every new controller/service/repository/mapper requires unit tests under `tests/unit/` and, where it crosses a boundary (ingestion, retrieval, generation, API), an integration test under `tests/integration/`.
- Do not implement question-specific logic anywhere in the response pipeline — grounding must be generic and evidence-driven (see `grounding.instructions.md`).
