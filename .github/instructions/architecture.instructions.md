---
applyTo: "backend/**,frontend/**,infra/**,skills-agents/**"
---

# Architecture Instructions

- Follow the mandated development order: `skills-agents` → `backend` → `frontend` → `infra`. Do not build backend features before the relevant skill/agent exists; do not build frontend before the backend API contract is established; do not build infra before backend and frontend exist.
- Backend follows `Controller → Service → Repository → Database` and `Request DTO → Mapper → Domain Model → Service`. Never let a controller talk directly to a repository or the database.
- Apply SOLID, dependency inversion, interface-driven design, and constructor/provider-based dependency injection everywhere. Concrete implementations must be swappable behind interfaces (e.g. `VectorDatabaseAgent`'s FAISS/Pinecone abstraction, `AIProviderAgent`'s provider abstraction).
- Maintain strict separation between the three knowledge domains: (1) approved digital-twin knowledge used by the public chatbot, (2) internal QA knowledge (`skills-agents/qa/`), and (3) engineering/source knowledge. Never let QA or engineering knowledge leak into the chatbot's public knowledge path.
- No agent, service, or module may duplicate another's responsibility — delegate instead. Consult `.github/agents/` to find the right owner before implementing something new.
- Any change with architectural significance (new layer, new cross-cutting concern, new external dependency direction) must be validated against `architecture/SYSTEM_ARCHITECTURE.md` before implementation, per `ArchitectureValidationHook`.
- Never hardcode domain-specific chatbot answers (no `if question == "...": return "..."`, no FAQ maps, no canned biography text). All chatbot answers must flow through retrieval → grounding → generation.
