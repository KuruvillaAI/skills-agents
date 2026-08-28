# Add New Chat Feature

## Purpose
Add a new capability to the chat pipeline (e.g. citations, streaming) without hardcoding answers.

## Required Agents
ResponseGenerationAgent, ContextAssemblyAgent, GroundingAgent, ChatUIAgent, FrontendAPIIntegrationAgent

## Required Skills
ResponseGeneration, ContextManagement, GroundingValidation, ChatUI

## Required Hooks
ResponseGenerationHook, GroundingValidationHook, ChatUIHook

## Usage
```text
@workspace Use the add-new-chat-feature prompt to: add a new capability to the chat pipeline (e.g. citations, streaming) without hardcoding answers.
```

## Steps
1. Design the pipeline change behind an interface.
2. ensure GroundingAgent still governs the output.
3. update the API contract.
4. wire the frontend.
5. add tests and run VisualQAAgent.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
