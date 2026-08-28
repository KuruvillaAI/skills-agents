# Deploy Production

## Purpose
Deploy the full stack to a production environment.

## Required Agents
DeploymentAgent, ReleaseManagementAgent, CICDAgent

## Required Skills
ContinuousDeployment, CloudDeployment

## Required Hooks
DeploymentHook, PostDeploymentQAHook

## Usage
```text
@workspace Use the deploy-production prompt to: deploy the full stack to a production environment.
```

## Steps
1. Run the full CI/CD pipeline.
2. deploy build artifacts.
3. run health checks.
4. run PostDeploymentQAHook.
5. confirm rollback plan.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
