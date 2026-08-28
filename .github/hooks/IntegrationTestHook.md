# IntegrationTestHook

## Trigger
Cross-module/service changes

## Purpose
Ensure integration tests exist and pass for the change.

## Non-Negotiable Rule
Cross-module/service/API-boundary changes MUST add or update integration tests. After
adding/updating tests, the ENTIRE existing integration test suite for the affected repository
must be executed (not just the new/changed tests) and report zero failures before the change
is considered done. Never delete, skip, or weaken an existing test merely to make it pass.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): IntegrationTestAgent.
3. Apply the relevant skill(s): IntegrationTesting.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
IntegrationTestAgent

## Required Skills
IntegrationTesting

## Example
"Trigger IntegrationTestHook after cross-module/service changes and report the result."
