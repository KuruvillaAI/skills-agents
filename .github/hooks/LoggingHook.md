# LoggingHook

## Trigger
Any request/operation completes

## Purpose
Emit structured, safe logs without leaking secrets or document content.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): LoggingAgent, BackendLoggingAgent.
3. Apply the relevant skill(s): Logging.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
LoggingAgent, BackendLoggingAgent

## Required Skills
Logging

## Example
"Trigger LoggingHook after any request/operation completes and report the result."
