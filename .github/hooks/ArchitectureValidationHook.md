# ArchitectureValidationHook

## Trigger
A significant design change is proposed

## Purpose
Validate the change against SYSTEM_ARCHITECTURE.md and SOLID/clean-architecture principles.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): SolutionArchitectAgent.
3. Apply the relevant skill(s): CodeQuality.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
SolutionArchitectAgent

## Required Skills
CodeQuality

## Example
"Trigger ArchitectureValidationHook after a significant design change is proposed and report the result."
