# ResponseGenerationHook

## Trigger
Assembled context and rules are ready

## Purpose
Invoke the LLM provider to generate the candidate response.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): ResponseGenerationAgent, AIProviderAgent.
3. Apply the relevant skill(s): ResponseGeneration, LLMIntegration.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
ResponseGenerationAgent, AIProviderAgent

## Required Skills
ResponseGeneration, LLMIntegration

## Example
"Trigger ResponseGenerationHook after assembled context and rules are ready and report the result."
