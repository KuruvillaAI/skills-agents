# Ingest Document

## Purpose
Ingest a new approved knowledge document into the digital twin.

## Required Agents
DocumentIngestionAgent, DocumentValidationAgent, EmbeddingAgent, VectorDatabaseAgent

## Required Skills
DocumentProcessing, DocumentValidation, EmbeddingGeneration, VectorDBManagement

## Required Hooks
DocumentUploadHook, DocumentValidationHook, EmbeddingCreationHook, VectorDBSyncHook

## Usage
```text
@workspace Use the ingest-document prompt to: ingest a new approved knowledge document into the digital twin.
```

## Steps
1. Validate the document.
2. parse/clean/chunk it.
3. generate embeddings.
4. upsert into the vector database.
5. confirm ingestion status via /health or logs.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
