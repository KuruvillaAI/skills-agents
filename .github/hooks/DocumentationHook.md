# DocumentationHook

## Trigger
Behavior-affecting code changes

## Purpose
Update the relevant README/architecture/QA documentation.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): DocumentationAgent.
3. Apply the relevant skill(s): DocumentationWriting.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
DocumentationAgent

## Required Skills
DocumentationWriting

## Example
"Trigger DocumentationHook after behavior-affecting code changes and report the result."
