# ProfileKnowledgeIngestion

## Purpose
Turn a user-supplied, publicly accessible professional profile URL into an evidence-only knowledge document.

## Workflow
1. Validate that the URL is HTTPS and publicly routable.
2. Fetch only the profile page and a bounded set of explicit external links found on it.
3. Extract readable page text and source URLs without bypassing authentication, paywalls, robots rules, or access controls.
4. Summarize the available facts through the configured LLM provider, preserving uncertainty and source boundaries.
5. Index the generated `.txt` knowledge document through the existing document-ingestion pipeline.

## Inputs
A public LinkedIn profile URL and configured fetch, summarization, and document-ingestion services.

## Outputs
An indexed knowledge document containing sourced profile facts, linked-site summaries, and source URLs.

## Related Agents
ProfileIngestionAgent, DocumentIngestionAgent, AIProviderAgent, SecurityAgent, BackendIntegrationTestingAgent

## Related Hooks
ProfileFetchHook, DocumentUploadHook, DocumentValidationHook, EmbeddingCreationHook, VectorDBSyncHook, GroundingValidationHook

## Example
"Use ProfileKnowledgeIngestion for a public LinkedIn URL and index its available profile and linked GitHub details without accessing private content."
