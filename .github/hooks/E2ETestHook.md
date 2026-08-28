# E2ETestHook

## Trigger
A full workflow is added or changed

## Purpose
Run end-to-end tests covering the complete workflow.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): E2ETestAgent.
3. Apply the relevant skill(s): E2ETesting.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
E2ETestAgent

## Required Skills
E2ETesting

## Example
"Trigger E2ETestHook after a full workflow is added or changed and report the result."
