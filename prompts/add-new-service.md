# Add New Service

## Purpose
Add a new backend service class implementing a defined interface.

## Required Agents
ServiceLayerAgent, DependencyInjectionAgent, BackendTestingAgent

## Required Skills
ServiceDevelopment, DependencyInjection

## Required Hooks
BackendValidationHook, BackendTestHook

## Usage
```text
@workspace Use the add-new-service prompt to: add a new backend service class implementing a defined interface.
```

## Steps
1. Define the service interface.
2. implement it.
3. register it via dependency injection.
4. write unit tests with mocked repositories/collaborators.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
