# Perform Regression Test

## Purpose
Run regression tests for areas affected by a recent change.

## Required Agents
RegressionTestAgent, VisualQAAgent

## Required Skills
RegressionTesting

## Required Hooks
RegressionTestingHook

## Usage
```text
@workspace Use the perform-regression-test prompt to: run regression tests for areas affected by a recent change.
```

## Steps
1. Identify the changed feature.
2. consult qa/REGRESSION_MATRIX.md for related areas.
3. run targeted tests.
4. expand to broader regression if needed.
5. update the matrix.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
