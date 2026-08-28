# Validate Document Grounding

## Purpose
Verify the chatbot only answers from the approved knowledge document.

## Required Agents
GroundingAgent, HallucinationDetectionAgent, PromptInjectionAgent

## Required Skills
GroundingValidation, HallucinationDetection, PromptInjectionProtection

## Required Hooks
GroundingValidationHook, PromptInjectionHook

## Usage
```text
@workspace Use the validate-document-grounding prompt to: verify the chatbot only answers from the approved knowledge document.
```

## Steps
1. Ask a supported question and verify a grounded, cited answer.
2. ask an unsupported question and verify the generic refusal.
3. attempt prompt injection and verify grounding/security hold.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
