# Development Order

The digital-twin system must be implemented in this exact order:

```text
1. skills-agents  (agents, skills, hooks, instructions, prompts, QA/architecture docs)
2. backend        (API contract + document-grounded RAG pipeline)
3. frontend       (chat UI consuming the backend contract)
4. infra          (containerization, CI/CD, deployment, monitoring)
5. complete system startup
6. automated tests
7. Visual QA
8. regression testing
9. final verification
```

## Why
- Agents/skills/hooks must exist before Copilot can use them to guide backend/frontend/infra work.
- The backend API contract must be established before the frontend can be built against it.
- Infra packages and deploys backend + frontend, so it must come last.
- No repository is considered "done" until it has passed automated tests; the whole system isn't done until Visual QA, regression, and final verification pass.

`MasterOrchestrationAgent` enforces this order for any new feature that spans repositories.
