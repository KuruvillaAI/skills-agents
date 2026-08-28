# CloudDeployment

## Purpose
Provider-agnostic cloud deployment guidance.

## Description
This skill packages provider-agnostic deployment guidance while documenting the current Render implementation used by this project.

## Workflow
1. Identify the target provider and service type.
2. Validate the provider's free-tier limits, runtime, build, health-check, and secret behavior.
3. Configure the service from the repository without embedding credentials.
4. Verify public URL, health, CORS, and user-facing behavior.
5. Record provider-specific limitations and hand off to post-deployment QA.

## Inputs
Task description, existing related code/config/docs, project conventions (see architecture/ and instructions/).

## Outputs
Implemented or updated artifact, plus any tests/documentation required by the change.

## Related Agents
CloudAgent, DeploymentAgent, AzureAgent, AWSAgent

## Related Hooks
DeploymentHook, PostDeploymentQAHook

## Example
"Apply CloudDeployment to configure the FastAPI Docker service and Vite static site on Render's free plan, including health checks and environment variables."
