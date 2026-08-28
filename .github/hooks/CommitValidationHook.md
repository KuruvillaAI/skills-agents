# CommitValidationHook

## Trigger
A commit is created

## Purpose
Enforce conventional commit message standards.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): CommitMessageAgent.
3. Apply the relevant skill(s): GitManagement.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
CommitMessageAgent

## Required Skills
GitManagement

## Example
"Trigger CommitValidationHook after a commit is created and report the result."
