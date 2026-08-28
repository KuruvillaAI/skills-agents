# Run End-to-End Tests

## Purpose
Run full end-to-end tests covering upload through grounded chat response.

## Required Agents
E2ETestAgent

## Required Skills
E2ETesting

## Required Hooks
E2ETestHook

## Usage
```text
@workspace Use the run-e2e-tests prompt to: run full end-to-end tests covering upload through grounded chat response.
```

## Steps
1. Start backend and frontend.
2. run E2E tests for upload -> ingest -> embed -> index -> ask -> retrieve -> ground -> generate -> display.
3. report results.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
