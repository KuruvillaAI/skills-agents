# CICDHook

## Trigger
On push/PR

## Purpose
Run checkout, install, lint, unit tests, integration tests, security scan, build, and Docker build.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): CICDAgent, GitHubActionsAgent.
3. Apply the relevant skill(s): ContinuousIntegration.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
CICDAgent, GitHubActionsAgent

## Required Skills
ContinuousIntegration

## Example
"Trigger CICDHook after on push/PR and report the result."
