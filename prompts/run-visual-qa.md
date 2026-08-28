# Run Visual QA

## Purpose
Run a full VisualQAAgent manual verification pass.

## Required Agents
VisualQAAgent

## Required Skills
VisualQualityAssurance, ManualBrowserTesting

## Required Hooks
VisualQAHook

## Usage
```text
@workspace Use the run-visual-qa prompt to: run a full VisualQAAgent manual verification pass.
```

## Steps
1. Start the application.
2. open it in the VS Code integrated browser.
3. execute the Visual QA workflow.
4. update QA documentation.
5. report QA STATUS.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
