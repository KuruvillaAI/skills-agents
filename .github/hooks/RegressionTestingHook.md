# RegressionTestingHook

## Trigger
After a feature is modified

## Purpose
Identify affected areas and run targeted, then broader, regression tests as needed.

## Non-Negotiable Rule
After any feature is modified, run the FULL automated test suite (unit + integration, both
backend and frontend where applicable) -- not only the tests related to the modified area.
Any previously-passing test that now fails is a regression and blocks completion until fixed.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): RegressionTestAgent, VisualQAAgent.
3. Apply the relevant skill(s): RegressionTesting.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
RegressionTestAgent, VisualQAAgent

## Required Skills
RegressionTesting

## Example
"Trigger RegressionTestingHook after after a feature is modified and report the result."
