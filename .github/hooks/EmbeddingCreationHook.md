# EmbeddingCreationHook

## Trigger
New or changed document chunks exist

## Purpose
Generate embeddings for chunks and hand them to the vector database.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): EmbeddingAgent.
3. Apply the relevant skill(s): EmbeddingGeneration, EmbeddingManagement.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
EmbeddingAgent

## Required Skills
EmbeddingGeneration, EmbeddingManagement

## Example
"Trigger EmbeddingCreationHook after new or changed document chunks exist and report the result."
