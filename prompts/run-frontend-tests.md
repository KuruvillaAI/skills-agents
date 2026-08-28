# Run Frontend Tests

## Purpose
Run the full frontend automated test suite.

## Required Agents
FrontendTestingAgent, FrontendIntegrationTestingAgent

## Required Skills
UnitTesting, IntegrationTesting

## Required Hooks
FrontendTestHook

## Usage
```text
@workspace Use the run-frontend-tests prompt to: run the full frontend automated test suite.
```

## Steps
1. Install frontend dependencies.
2. run unit tests.
3. run integration tests.
4. report pass/fail and coverage.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
