# Debug Retrieval

## Purpose
Diagnose why retrieval is returning poor or no evidence for a query.

## Required Agents
RetrievalAgent, EmbeddingAgent, VectorDatabaseAgent

## Required Skills
RetrievalOrchestration, SemanticSearch, EmbeddingManagement

## Required Hooks
QueryRetrievalHook

## Usage
```text
@workspace Use the debug-retrieval prompt to: diagnose why retrieval is returning poor or no evidence for a query.
```

## Steps
1. Check query preprocessing/embedding.
2. inspect vector index health.
3. verify Top-K/threshold configuration.
4. test with known-good queries.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
