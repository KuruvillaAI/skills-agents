# FrontendBuildHook

## Trigger
Frontend source changes / before commit

## Purpose
Run the frontend build (type-check + bundle) to catch build errors early.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): FrontendArchitectureAgent.
3. Apply the relevant skill(s): FrontendDevelopment.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
FrontendArchitectureAgent

## Required Skills
FrontendDevelopment

## Example
"Trigger FrontendBuildHook after frontend source changes / before commit and report the result."
