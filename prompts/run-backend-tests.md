# Run Backend Tests

## Purpose
Run the full backend automated test suite.

## Required Agents
BackendTestingAgent, BackendIntegrationTestingAgent

## Required Skills
UnitTesting, IntegrationTesting

## Required Hooks
UnitTestHook, IntegrationTestHook

## Usage
```text
@workspace Use the run-backend-tests prompt to: run the full backend automated test suite.
```

## Steps
1. Install backend dependencies.
2. run pytest for unit tests.
3. run pytest for integration tests.
4. report pass/fail and coverage.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
