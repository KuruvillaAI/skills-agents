# Run Integration Tests

## Purpose
Run cross-repository integration tests (backend API + AI pipeline).

## Required Agents
IntegrationTestAgent, BackendIntegrationTestingAgent

## Required Skills
IntegrationTesting

## Required Hooks
IntegrationTestHook

## Usage
```text
@workspace Use the run-integration-tests prompt to: run cross-repository integration tests (backend API + AI pipeline).
```

## Steps
1. Start the backend in test mode.
2. run the integration suite covering ingestion, retrieval, grounding, and API contracts.
3. report results.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
