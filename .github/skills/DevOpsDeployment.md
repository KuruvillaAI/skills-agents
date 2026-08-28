# DevOpsDeployment

## Purpose
General DevOps and deployment practices.

## Description
This skill packages the project's current free deployment flow: separate GitHub repositories in `KuruvillaAI`, Render Static Site hosting for the Vite frontend, and a Render Docker Web Service for the FastAPI backend.

## Workflow
1. Identify the affected repository and Render service.
2. Validate tests, lint, and build artifacts.
3. Configure deployment through `render.yaml`, Dockerfile, and Render environment variables.
4. Confirm deployment, health, CORS, and frontend rendering.
5. Hand off to `PostDeploymentQAHook` and record the result.

## Inputs
Task description, existing related code/config/docs, project conventions (see architecture/ and instructions/).

## Outputs
Updated deployment configuration, deployed service URLs, health-check evidence, and any required tests/documentation.

## Related Agents
DeploymentAgent, GitHubActionsAgent, VisualQAAgent

## Related Hooks
DeploymentHook, PostDeploymentQAHook

## Example
"Apply DevOpsDeployment to deploy the backend Docker service and frontend static site from the KuruvillaAI repositories on Render, then verify health and CORS."
