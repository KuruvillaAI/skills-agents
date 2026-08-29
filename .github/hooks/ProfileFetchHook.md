# ProfileFetchHook

## Trigger
A user submits a LinkedIn profile URL for knowledge-document creation.

## Purpose
Coordinate safe public profile retrieval before summarization and indexing.

## Preconditions
- URL is supplied by the user.
- ProfileIngestionAgent and ProfileKnowledgeIngestion are available.
- No authentication or access-control bypass is required.

## Actions
1. Validate HTTPS URL and public network destination.
2. Fetch the profile with size, timeout, content-type, redirect, and page-count limits.
3. Follow only explicit public external links, with a strict bounded allowlist.
4. Extract source-labelled text and invoke evidence-only summarization.
5. Index the generated text through DocumentUploadHook and record sources/counts.

## Failure Behavior
Reject unsafe or inaccessible URLs with a structured client-safe error. Never fall back to private access, scrape credentials, or continue after a security validation failure.

## Responsible Agents
ProfileIngestionAgent, SecurityAgent, DocumentIngestionAgent

## Required Skills
ProfileKnowledgeIngestion, DocumentValidation, DocumentProcessing

## Example
"Trigger ProfileFetchHook for the supplied public LinkedIn URL and report whether the sourced knowledge document was indexed."
