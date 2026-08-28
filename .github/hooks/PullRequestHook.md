# PullRequestHook

## Trigger
A pull request is opened/updated

## Purpose
Validate PR description, linked issues, and CI status before merge.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): PullRequestAgent.
3. Apply the relevant skill(s): PullRequestManagement.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
PullRequestAgent

## Required Skills
PullRequestManagement

## Example
"Trigger PullRequestHook after a pull request is opened/updated and report the result."
