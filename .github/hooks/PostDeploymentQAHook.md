# PostDeploymentQAHook

## Trigger
After Render reports a frontend or backend deployment as live.

## Purpose
Open the deployed frontend, verify its connection to the deployed backend, and run the applicable smoke tests.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Open the Render frontend URL.
2. Confirm the page renders and the health badge reaches `Backend online` after any free-tier cold start.
3. Open the backend `/health` URL and verify HTTP 200.
4. Verify CORS allows the deployed frontend origin.
5. Test upload, greeting, supported chat, and unsupported-question grounding when approved knowledge content is available.
6. Invoke `VisualQAAgent` and record pass/fail evidence in the QA documents.

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
VisualQAAgent, DeploymentAgent

## Required Skills
VisualQualityAssurance, CloudDeployment

## Example
"Trigger PostDeploymentQAHook after Render reports the deployment live and record frontend, backend, CORS, and chat smoke-test results."
