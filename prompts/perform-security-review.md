# Perform Security Review

## Purpose
Review a proposed change for OWASP Top 10 and prompt-injection risks.

## Required Agents
SecurityAgent, ApplicationSecurityAgent, PromptInjectionAgent

## Required Skills
APISecurity, PromptInjectionProtection, DataProtection

## Required Hooks
SecurityScanHook, PromptInjectionHook

## Usage
```text
@workspace Use the perform-security-review prompt to: review a proposed change for OWASP Top 10 and prompt-injection risks.
```

## Steps
1. Check input validation, secrets handling, and auth.
2. check for prompt-injection resistance in any LLM-facing change.
3. block on BLOCKER/CRITICAL findings.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
