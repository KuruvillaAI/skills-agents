# ProfileKnowledgeIngestion

## Purpose
Turn a user-supplied, publicly accessible professional profile URL into an evidence-only knowledge document.

## Workflow
1. Redirect the user to official LinkedIn OAuth/OIDC and validate the callback state server-side.
2. Exchange the one-time authorization code only on the backend and fetch permitted userinfo fields.
3. Create a secure application session without exposing provider tokens to the frontend.
4. Create and index a source-labelled knowledge document containing only the permitted returned fields.
5. Use a user-uploaded LinkedIn export for experience, projects, skills, certifications, and other data not granted by LinkedIn scopes.

## Inputs
An authenticated LinkedIn OAuth session, configured official LinkedIn client, and document-ingestion service.

## Outputs
An indexed knowledge document containing source-labelled, LinkedIn-permitted profile facts.

## Related Agents
ProfileIngestionAgent, DocumentIngestionAgent, AIProviderAgent, SecurityAgent, BackendIntegrationTestingAgent

## Related Hooks
ProfileFetchHook, DocumentUploadHook, DocumentValidationHook, EmbeddingCreationHook, VectorDBSyncHook, GroundingValidationHook

## Example
"Use ProfileKnowledgeIngestion to import only the authenticated LinkedIn member's fields approved by OAuth scopes."
