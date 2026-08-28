# ErrorHandlingHook

## Trigger
An unhandled error occurs

## Purpose
Translate the error into a safe structured response and log it for observability.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): BackendErrorHandlingAgent.
3. Apply the relevant skill(s): BackendDevelopment.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
BackendErrorHandlingAgent

## Required Skills
BackendDevelopment

## Example
"Trigger ErrorHandlingHook after an unhandled error occurs and report the result."
