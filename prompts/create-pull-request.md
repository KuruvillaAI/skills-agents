# Create Pull Request

## Purpose
Open a pull request for a completed, tested change.

## Required Agents
PullRequestAgent, GitManagementAgent, CommitMessageAgent

## Required Skills
PullRequestManagement, GitManagement

## Required Hooks
PullRequestHook, CommitValidationHook

## Usage
```text
@workspace Use the create-pull-request prompt to: open a pull request for a completed, tested change.
```

## Steps
1. Ensure tests pass and docs are updated.
2. create a feature branch with conventional commits.
3. open a PR with a clear description linking affected repositories/features.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
