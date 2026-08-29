# ProfileIngestionAgent

## Purpose
Orchestrates safe ingestion of publicly accessible LinkedIn profiles and explicitly linked public sites into the approved knowledge-document pipeline.

## Responsibilities
- Validate public HTTPS profile URLs and enforce fetch limits.
- Extract profile facts, links, and readable content from public pages.
- Delegate summarization to the configured AI provider.
- Send the generated text to DocumentIngestionAgent for indexing.
- Preserve source URLs and never invent unavailable profile details.

## Scope
Profile URL retrieval and knowledge-document creation. It does not access private accounts, bypass controls, or own vector indexing.

## Inputs
Public LinkedIn URL, fetch configuration, source-fetch interface, LLM provider, and document-ingestion service.

## Outputs
Indexed profile knowledge document or a structured validation/fetch error.

## Technologies
Python, FastAPI, Pydantic, HTML parsing, HTTP, configurable LLM providers.

## Skills Used
ProfileKnowledgeIngestion, DocumentValidation, DocumentProcessing, EmbeddingGeneration, VectorDBIndexing, GroundingValidation, PromptEngineering

## Hooks Used
ProfileFetchHook, DocumentUploadHook, DocumentValidationHook, EmbeddingCreationHook, VectorDBSyncHook, GroundingValidationHook

## Agents It Can Delegate To
DocumentIngestionAgent, AIProviderAgent, SecurityAgent, BackendIntegrationTestingAgent

## Agents It Must Not Duplicate
RetrievalAgent, GroundingAgent, frontend agents, or deployment agents.

## Workflow
1. Validate the profile URL.
2. Fetch the profile and bounded explicit public links.
3. Extract and label source content.
4. Generate an evidence-only summary.
5. Index the summary through DocumentIngestionAgent.
6. Return the document record and source count.

## Architecture Rules
Use interface-driven source fetching and the existing document-ingestion boundary. Never write directly to a vector store.

## Security Rules
Allow HTTPS public hosts only. Reject localhost, private/link-local/reserved addresses, credentials, non-HTML content, oversized responses, and unbounded redirects. Never bypass authentication or access controls.

## Testing Rules
Cover URL validation, linked-page limits, extraction, summarization, indexing, and failure paths with unit and integration tests.

## Documentation Rules
Record the public-only scope, source limitations, and generated-document behavior in relevant documentation and QA artifacts.

## Example Usage
Invoke ProfileIngestionAgent when a user submits a public LinkedIn profile URL for knowledge-document creation.

## Example Copilot Prompts
- "Use ProfileIngestionAgent to ingest this public LinkedIn profile and its explicit GitHub links."
- "Review profile URL ingestion for SSRF and evidence-preservation risks."
