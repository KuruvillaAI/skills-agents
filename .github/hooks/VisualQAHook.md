# VisualQAHook

## Trigger
After application startup/build

## Purpose
Open the app in the VS Code integrated browser and run a visual smoke test plus critical workflows.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): VisualQAAgent.
3. Apply the relevant skill(s): VisualQualityAssurance, ManualBrowserTesting.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
VisualQAAgent

## Required Skills
VisualQualityAssurance, ManualBrowserTesting

## Example
"Trigger VisualQAHook after after application startup/build and report the result."
