# Release Version

## Purpose
Cut and publish a new versioned release.

## Required Agents
ReleaseAgent, ReleaseManagementAgent

## Required Skills
ReleaseManagement

## Required Hooks
PullRequestHook

## Usage
```text
@workspace Use the release-version prompt to: cut and publish a new versioned release.
```

## Steps
1. Confirm all required tests and Visual QA pass.
2. bump version numbers.
3. tag the release.
4. publish release notes summarizing changes.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
