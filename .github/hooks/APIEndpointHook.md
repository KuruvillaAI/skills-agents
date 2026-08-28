# APIEndpointHook

## Trigger
A new or changed API endpoint is added

## Purpose
Validate the endpoint against API contract, DI, and OpenAPI documentation standards.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): FastAPIAgent, ControllerAgent.
3. Apply the relevant skill(s): APIDevelopment, ControllerDevelopment.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
FastAPIAgent, ControllerAgent

## Required Skills
APIDevelopment, ControllerDevelopment

## Example
"Trigger APIEndpointHook after a new or changed API endpoint is added and report the result."
