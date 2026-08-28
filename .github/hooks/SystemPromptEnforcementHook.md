# SystemPromptEnforcementHook

## Trigger
Before every LLM call

## Purpose
Enforce the system prompt/rules so grounding and security constraints cannot be overridden by user input.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): PromptEngineeringAgent, GroundingAgent.
3. Apply the relevant skill(s): PromptEngineering, GroundingValidation.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
PromptEngineeringAgent, GroundingAgent

## Required Skills
PromptEngineering, GroundingValidation

## Example
"Trigger SystemPromptEnforcementHook after before every LLM call and report the result."
