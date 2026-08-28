# skills-agents

Copilot agent/skill/hook knowledge base and living documentation for the **document-grounded digital twin** project. This repository is built **first**, before `backend`, `frontend`, and `infra`, per [documentation/DEVELOPMENT_ORDER.md](./documentation/DEVELOPMENT_ORDER.md).

## What lives here

```text
skills-agents/
├── .github/
│   ├── agents/          # ~150 Copilot custom agent definitions
│   ├── skills/           # Reusable domain-knowledge skills
│   ├── hooks/            # Lifecycle hooks (trigger → action → agent)
│   ├── instructions/     # applyTo-scoped Copilot instructions
│   └── workflows/        # CI that validates this knowledge base's structure
├── prompts/               # Reusable, agent/skill/hook-tagged task prompts
├── qa/                     # Internal QA knowledge base (never exposed to the chatbot)
├── architecture/           # System/AI-pipeline architecture docs
├── documentation/          # Cross-cutting living documentation
├── templates/              # Blank templates for new agents/skills/hooks/ADRs
└── checklists/             # Definition of done, security, PR, QA sign-off
```

## Start here
1. Read [architecture/SYSTEM_ARCHITECTURE.md](./architecture/SYSTEM_ARCHITECTURE.md) and [architecture/AI_PIPELINE.md](./architecture/AI_PIPELINE.md).
2. Read [documentation/KNOWLEDGE_SEPARATION.md](./documentation/KNOWLEDGE_SEPARATION.md) — this rule is non-negotiable.
3. For any new task, start from `.github/agents/MasterOrchestrationAgent.md`.
4. Use `prompts/` for common tasks (e.g. `add-new-api-endpoint.md`, `run-visual-qa.md`).

## Governing principle
> The approved knowledge document is the single source of truth for everything the chatbot is allowed to say about the user. No hallucination, no hardcoded chatbot answers, no exceptions.

## Contributing to the knowledge base
- New agents/skills/hooks must follow the templates in `templates/`.
- CI (`.github/workflows/validate-knowledge-base.yml`) validates that every agent/skill/hook file contains its required sections.
- Keep `qa/` and `architecture/` strictly separate from what the chatbot can retrieve — see `documentation/KNOWLEDGE_SEPARATION.md`.
