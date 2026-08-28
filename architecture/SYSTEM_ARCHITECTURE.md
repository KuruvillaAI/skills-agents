# System Architecture

## Repositories
```text
digital-twin/
├── skills-agents/   # Copilot agents, skills, hooks, prompts, QA & architecture knowledge (built first)
├── backend/         # FastAPI document-grounded RAG service (built second)
├── frontend/        # React + Vite + TypeScript chat UI (built third)
└── infra/           # Docker, Docker Compose, Terraform, CI/CD, monitoring (built fourth)
```

## Three Knowledge Domains
1. **Digital Twin Knowledge** — the approved document; flows through Document ingestion → Embeddings → Vector database → Retrieval → Grounded response. This is the *only* thing the public chatbot may draw on for personal information about the user.
2. **QA Knowledge** (`skills-agents/qa/`) — internal features/UI/workflows/tests/defects. Never exposed to the chatbot.
3. **Source Code / Engineering Knowledge** (`skills-agents/architecture/`, `.github/`, source repos) — architecture, implementation, infra, agents/skills/hooks. Never exposed to the chatbot.

## Backend Layering
```text
Controller → Service → Repository → Database
Request DTO → Mapper → Domain Model → Service
```

## Document-Grounded Response Pipeline
```text
User → API → Query validation → Query preprocessing → Embedding → Vector search →
Reranking → Context assembly → Evidence validation → System rules → Personality →
LLM → Response validation → Grounding validation → Response (or generic refusal)
```

## Cross-Cutting Principles
Strict document grounding; no hallucinated user information; no hardcoded domain-specific chatbot answers; personality derived from the approved source; modular architecture; separation of concerns; dependency injection; interface-driven design; automated testing; manual visual QA; security by design; observability; CI/CD; Copilot agent-driven development; living documentation; continuous regression testing.

## Governance
Significant changes must pass, in order: Architecture Validation → Security Validation → Unit Tests → Integration Tests → Lint → Build → Visual QA → Documentation Validation. See `ArchitectureValidationHook` and `SolutionArchitectAgent`.
