# Upgrade Library

## Purpose
Upgrade a single dependency to a newer version safely.

## Required Agents
LibraryUpgradeAgent

## Required Skills
DependencyUpgrade

## Required Hooks
LibraryUpgradeHook

## Usage
```text
@workspace Use the upgrade-library prompt to: upgrade a single dependency to a newer version safely.
```

## Steps
1. Check changelog for breaking changes.
2. bump the version.
3. run the full test suite.
4. fix any breakage.
5. update lockfiles.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
