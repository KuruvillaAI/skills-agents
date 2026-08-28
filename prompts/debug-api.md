# Debug API

## Purpose
Diagnose and fix a failing or misbehaving backend API endpoint.

## Required Agents
FastAPIAgent, BackendArchitectureAgent, BackendTestingAgent

## Required Skills
FastAPIDevelopment, BackendDevelopment

## Required Hooks
BackendTestHook

## Usage
```text
@workspace Use the debug-api prompt to: diagnose and fix a failing or misbehaving backend API endpoint.
```

## Steps
1. Reproduce the failure.
2. inspect logs/errors.
3. isolate the failing layer (controller/service/repository).
4. fix and add a regression test.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
