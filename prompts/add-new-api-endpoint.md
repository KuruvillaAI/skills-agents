# Add New API Endpoint

## Purpose
Add a new FastAPI endpoint following the project's layered architecture.

## Required Agents
APIArchitectureAgent, ControllerAgent, ServiceLayerAgent, FastAPIAgent, BackendTestingAgent

## Required Skills
APIDevelopment, ControllerDevelopment, ServiceDevelopment, FastAPIDevelopment

## Required Hooks
APIEndpointHook, BackendTestHook

## Usage
```text
@workspace Use the add-new-api-endpoint prompt to: add a new FastAPI endpoint following the project's layered architecture.
```

## Steps
1. Define the request/response DTOs.
2. add a controller route.
3. implement/extend the service.
4. add repository access if needed.
5. write unit + integration tests.
6. update OpenAPI docs.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
