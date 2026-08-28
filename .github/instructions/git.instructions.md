---
applyTo: "**"
---

# Git Instructions

- Use conventional commits (`feat:`, `fix:`, `test:`, `docs:`, `chore:`, `refactor:`, `ci:`, `security:`) scoped to the affected repository when helpful, e.g. `feat(backend): add /chat streaming support`.
- Branch naming: `feature/<short-desc>`, `fix/<short-desc>`, `chore/<short-desc>`, `security/<short-desc>`.
- Never commit `.env` files, API keys, credentials, or other secrets. Only `.env.example` with placeholder values is committed.
- A pull request must only be opened once required automated tests pass and, for UI/workflow-affecting changes, `VisualQAAgent` has completed a verification pass.
- Keep each repository's own Git history focused on that repository's concerns; cross-repository changes should be called out clearly in the PR description with the coordinated change set.
- Never force-push, rewrite published history, or delete branches/tags without explicit user confirmation.
