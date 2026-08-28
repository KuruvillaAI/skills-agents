# UnitTestHook

## Trigger
New/changed production code

## Purpose
Ensure unit tests exist and pass for the change.

## Non-Negotiable Rule
Every code change (new feature, bug fix, or refactor) MUST add or update unit tests that cover it.
After adding/updating tests, the ENTIRE existing unit test suite for the affected repository
must be executed (not just the new/changed tests). A change is not complete until the full
suite reports zero failures. A previously-passing test that starts failing because of your
change is a regression and must be fixed before the change is considered done -- never delete,
skip, or weaken an existing test merely to make it pass.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): UnitTestCreationAgent.
3. Apply the relevant skill(s): UnitTestCreation.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
UnitTestCreationAgent

## Required Skills
UnitTestCreation

## Example
"Trigger UnitTestHook after new/changed production code and report the result."
