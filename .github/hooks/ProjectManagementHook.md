# ProjectManagementHook

## Trigger
A new feature/requirement is captured

## Purpose
Break the requirement into tasks, risks, and dependencies for MasterOrchestrationAgent.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): ProjectManagementAgent.
3. Apply the relevant skill(s): ProjectManagement.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
ProjectManagementAgent

## Required Skills
ProjectManagement

## Example
"Trigger ProjectManagementHook after a new feature/requirement is captured and report the result."
