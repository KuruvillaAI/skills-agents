---
applyTo: "backend/**,frontend/**,infra/**"
---

# Security Instructions

- Never hardcode API keys, credentials, tokens, or secrets anywhere in source control. Use environment variables and `.env.example` (with placeholder values only) in every repository.
- Validate and sanitize all external input: chat queries, uploaded documents, file names/sizes/types, and configuration values.
- Document upload must enforce: allowed file types, maximum size, content-type verification, and safe storage (no path traversal, no arbitrary code execution from parsed content).
- Apply rate limiting and CORS restrictions on backend APIs; do not use `allow_origins=["*"]` in production configuration.
- Treat every user chat message as untrusted input for prompt-injection purposes (see `grounding.instructions.md`). The system prompt and grounding rules must not be overridable by user input.
- Never expose in any API response or log: system prompts, internal agent instructions, raw stack traces, internal file paths, QA knowledge, or infrastructure secrets.
- Scan dependencies for known vulnerabilities as part of CI (`DependencySecurityHook`) and keep them current (`LibraryUpgradeHook`).
- Log safely: never log full document contents, embeddings of sensitive data, secrets, or personally identifying information beyond what is operationally necessary.
