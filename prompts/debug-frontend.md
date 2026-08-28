# Debug Frontend

## Purpose
Diagnose and fix a failing or misbehaving frontend feature.

## Required Agents
ReactAgent, TypeScriptAgent, FrontendTestingAgent

## Required Skills
ReactDevelopment, TypeScriptDevelopment

## Required Hooks
FrontendTestHook

## Usage
```text
@workspace Use the debug-frontend prompt to: diagnose and fix a failing or misbehaving frontend feature.
```

## Steps
1. Reproduce the failure in the browser.
2. inspect console/network errors.
3. isolate the failing component/service.
4. fix and add a regression test.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
