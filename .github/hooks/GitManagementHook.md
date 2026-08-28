# GitManagementHook

## Trigger
A change is ready to commit

## Purpose
Enforce branch naming and repository hygiene rules.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): GitManagementAgent.
3. Apply the relevant skill(s): GitManagement.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
GitManagementAgent

## Required Skills
GitManagement

## Example
"Trigger GitManagementHook after a change is ready to commit and report the result."
