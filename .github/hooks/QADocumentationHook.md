# QADocumentationHook

## Trigger
After every QA execution

## Purpose
Update test history, feature status, UI catalog, regression matrix, defect log, changelog, and QA report.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): VisualQAAgent, QAAgent.
3. Apply the relevant skill(s): QADocumentation.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
VisualQAAgent, QAAgent

## Required Skills
QADocumentation

## Example
"Trigger QADocumentationHook after after every QA execution and report the result."
