# CodeReviewHook

## Trigger
A pull request is ready for review

## Purpose
Perform automated/Copilot-assisted review against clean-code and architecture standards.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): CodeReviewAgent.
3. Apply the relevant skill(s): CodeReview, CleanCode.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
CodeReviewAgent

## Required Skills
CodeReview, CleanCode

## Example
"Trigger CodeReviewHook after a pull request is ready for review and report the result."
