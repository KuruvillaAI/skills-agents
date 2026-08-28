# PostDeploymentQAHook

## Trigger
After a deployment completes

## Purpose
Open the deployed app, run smoke tests, verify backend/chatbot/grounding, and report status.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): VisualQAAgent, DeploymentAgent.
3. Apply the relevant skill(s): VisualQualityAssurance.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
VisualQAAgent, DeploymentAgent

## Required Skills
VisualQualityAssurance

## Example
"Trigger PostDeploymentQAHook after after a deployment completes and report the result."
