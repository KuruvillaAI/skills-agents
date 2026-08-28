# AccessibilityHook

## Trigger
UI components are added or changed

## Purpose
Verify WCAG-relevant accessibility properties (labels, roles, contrast, keyboard nav).

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): FrontendAccessibilityAgent.
3. Apply the relevant skill(s): Accessibility, AccessibilityTesting.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
FrontendAccessibilityAgent

## Required Skills
Accessibility, AccessibilityTesting

## Example
"Trigger AccessibilityHook after uI components are added or changed and report the result."
