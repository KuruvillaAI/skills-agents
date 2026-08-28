# Security Checklist

- [ ] No hardcoded secrets, API keys, or credentials
- [ ] All external input validated and sanitized
- [ ] File uploads restricted by type/size and safely stored
- [ ] CORS configured restrictively (no wildcard in production)
- [ ] Rate limiting applied to public endpoints where appropriate
- [ ] Prompt injection resistance verified for any LLM-facing change
- [ ] No system prompts, internal instructions, or QA/engineering knowledge exposed to the chatbot or API responses
- [ ] Errors return safe, structured messages (no stack traces/paths leaked)
- [ ] Logs contain no secrets, document content, or PII beyond operational necessity
- [ ] Dependencies scanned for known vulnerabilities
