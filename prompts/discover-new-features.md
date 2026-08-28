# Discover New Features

## Purpose
Detect and document functionality missing from the QA knowledge base.

## Required Agents
VisualQAAgent

## Required Skills
FeatureDiscovery

## Required Hooks
FeatureDiscoveryHook

## Usage
```text
@workspace Use the discover-new-features prompt to: detect and document functionality missing from the QA knowledge base.
```

## Steps
1. Explore the running application.
2. compare against qa/APPLICATION_FEATURES.md.
3. add missing features, UI elements, workflows, and test cases.
4. add regression coverage.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
