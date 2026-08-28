# Reindex Document

## Purpose
Rebuild embeddings and the vector index for an already-ingested document (e.g. after an embedding model change).

## Required Agents
EmbeddingAgent, VectorDatabaseAgent

## Required Skills
EmbeddingManagement, VectorDBIndexing

## Required Hooks
EmbeddingCreationHook, VectorDBSyncHook

## Usage
```text
@workspace Use the reindex-document prompt to: rebuild embeddings and the vector index for an already-ingested document (e.g. after an embedding model change).
```

## Steps
1. Fetch existing chunks.
2. regenerate embeddings with the current provider/model.
3. replace vectors in the index.
4. verify retrieval still returns expected evidence.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
