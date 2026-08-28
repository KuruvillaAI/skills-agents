# SecurityScanHook

## Trigger
Before merge / on schedule

## Purpose
Run OWASP-focused static checks across changed code.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): SecurityAgent, ApplicationSecurityAgent.
3. Apply the relevant skill(s): APISecurity, DataProtection.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
SecurityAgent, ApplicationSecurityAgent

## Required Skills
APISecurity, DataProtection

## Example
"Trigger SecurityScanHook after before merge / on schedule and report the result."
