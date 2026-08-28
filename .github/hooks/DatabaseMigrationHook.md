# DatabaseMigrationHook

## Trigger
A database schema change is proposed

## Purpose
Generate/review a migration and validate it against existing data.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): MigrationAgent, SQLAgent.
3. Apply the relevant skill(s): SQLDevelopment, DatabaseDevelopment.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
MigrationAgent, SQLAgent

## Required Skills
SQLDevelopment, DatabaseDevelopment

## Example
"Trigger DatabaseMigrationHook after a database schema change is proposed and report the result."
