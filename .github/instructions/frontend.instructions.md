---
applyTo: "frontend/**"
---

# Frontend Instructions

- Stack: React + Vite + TypeScript (do not introduce Next.js alongside it — pick one stack and stay consistent). Strict TypeScript (`strict: true`); no `any` without justification.
- Structure: `src/components`, `src/services`, `src/interfaces`, `src/mappers`, `src/hooks`, `src/store`, `src/pages`, `src/utils`, `src/app`.
- The frontend must never generate, infer, or fabricate chatbot content. It only sends requests to the backend `/chat` API and renders whatever the backend returns (including refusal messages) — no client-side canned answers.
- `services/` call the backend API; `mappers/` convert backend DTOs to frontend view models; components consume view models only, never raw DTOs.
- Use Context API or Redux Toolkit for state (per `StateManagementAgent`); choose one pattern per concern and be consistent.
- The Chat UI must implement: message input, send, history, loading state, error state, retry, a distinct refusal-state rendering, handling of long responses, and responsive/accessible markup. Optional streaming must degrade gracefully if unsupported.
- Follow semantic HTML and WCAG accessibility practices (labels, roles, keyboard navigation, focus management, sufficient contrast).
- Every new component/service/hook requires unit tests; cross-component chat workflows require integration tests under `tests/integration/`.
- Never hardcode secrets or API base URLs — use `.env`/`.env.example` and Vite's `import.meta.env`.
