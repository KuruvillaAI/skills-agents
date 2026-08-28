# Knowledge Separation

The project maintains three completely separate information domains. Mixing them is a security and correctness defect.

| Domain | Contains | Consumed By | Never Exposed To |
|---|---|---|---|
| **Digital Twin Knowledge** | The single approved knowledge document about the user | The public chatbot's retrieval pipeline | N/A (this is the public-facing domain, but only via retrieval — never verbatim system internals) |
| **QA Knowledge** (`skills-agents/qa/`) | Features, UI catalog, workflows, test cases, defects, regression matrix, execution history | `VisualQAAgent`, `QAAgent`, developers | The public chatbot |
| **Source Code / Engineering Knowledge** (`skills-agents/architecture/`, `.github/`, source repos) | Architecture, implementation, infra, agents/skills/hooks | Developers, Copilot agents | The public chatbot |

Any pipeline or feature that could cause QA or engineering knowledge to be retrievable by the chatbot's grounding pipeline is a **BLOCKER** severity defect.
