# QueryRetrievalHook

## Trigger
A preprocessed query is ready

## Purpose
Execute semantic search and Top-K retrieval against the vector database.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): RetrievalAgent.
3. Apply the relevant skill(s): SemanticSearch.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
RetrievalAgent

## Required Skills
SemanticSearch

## Example
"Trigger QueryRetrievalHook after a preprocessed query is ready and report the result."
