# Deploy Development

## Purpose
Deploy the full stack to a local/development environment.

## Required Agents
DeploymentAgent, DockerComposeAgent

## Required Skills
DevOpsDeployment, DockerCompose

## Required Hooks
DeploymentHook, CICDHook

## Usage
```text
@workspace Use the deploy-development prompt to: deploy the full stack to a local/development environment.
```

## Steps
1. Build images.
2. run docker-compose up.
3. wait for health checks.
4. run a Visual QA smoke test.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
