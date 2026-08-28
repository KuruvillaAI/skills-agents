# Upgrade Dependencies

## Purpose
Perform a broader dependency upgrade pass across a repository.

## Required Agents
DependencyUpgradeAgent, DependencySecurityAgent

## Required Skills
DependencyUpgrade, DependencySecurity

## Required Hooks
DependencySecurityHook, LibraryUpgradeHook

## Usage
```text
@workspace Use the upgrade-dependencies prompt to: perform a broader dependency upgrade pass across a repository.
```

## Steps
1. Scan for outdated/vulnerable dependencies.
2. prioritize by risk.
3. upgrade incrementally.
4. run tests after each batch.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
