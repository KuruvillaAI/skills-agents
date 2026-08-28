# Debug Grounding

## Purpose
Diagnose why the chatbot is refusing or over-answering incorrectly.

## Required Agents
GroundingAgent, HallucinationDetectionAgent, ContextAssemblyAgent

## Required Skills
GroundingValidation, HallucinationDetection, ContextManagement

## Required Hooks
GroundingValidationHook, HallucinationDetectionHook

## Usage
```text
@workspace Use the debug-grounding prompt to: diagnose why the chatbot is refusing or over-answering incorrectly.
```

## Steps
1. Inspect retrieved evidence for the query.
2. check the grounding threshold.
3. check hallucination-detection logic.
4. verify the refusal message is generic, not question-specific.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
