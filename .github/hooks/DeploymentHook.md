# DeploymentHook

## Trigger
Render starts an automatic deployment after a commit reaches the configured `main` branch, or a deployment is started manually.

## Purpose
Coordinate Render deployment of the frontend Static Site and backend Docker Web Service, then verify the public application contract.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Identify the affected `KuruvillaAI` repository and Render service.
2. Invoke `DeploymentAgent` and apply `ContinuousDeployment`, `CloudDeployment`, and `DevOpsDeployment`.
3. Confirm the Render deployment is live.
4. Check backend `GET /health`, frontend HTTP 200, and CORS from the frontend origin.
5. Record URLs, deployment logs, status, and free-tier limitations.

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
DeploymentAgent

## Required Skills
ContinuousDeployment, CloudDeployment, DevOpsDeployment

## Example
"Trigger DeploymentHook after Render deploys the main branch and report health, CORS, frontend, and backend results."
