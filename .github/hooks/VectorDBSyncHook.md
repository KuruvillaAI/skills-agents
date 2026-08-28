# VectorDBSyncHook

## Trigger
Embeddings are created, updated, or deleted

## Purpose
Synchronize the vector index so retrieval reflects the latest approved knowledge.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): VectorDatabaseAgent.
3. Apply the relevant skill(s): VectorDBManagement, VectorDBIndexing.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
VectorDatabaseAgent

## Required Skills
VectorDBManagement, VectorDBIndexing

## Example
"Trigger VectorDBSyncHook after embeddings are created, updated, or deleted and report the result."
