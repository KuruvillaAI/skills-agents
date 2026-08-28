# GroundingValidationHook

## Trigger
A candidate response is generated

## Purpose
Verify the response is supported by retrieved evidence; force a generic refusal if not.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): GroundingAgent.
3. Apply the relevant skill(s): GroundingValidation.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
GroundingAgent

## Required Skills
GroundingValidation

## Example
"Trigger GroundingValidationHook after a candidate response is generated and report the result."
