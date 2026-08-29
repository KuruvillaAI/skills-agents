# ProfileFetchHook

## Trigger
A user chooses to import their authenticated LinkedIn profile for knowledge-document creation.

## Purpose
Coordinate official LinkedIn OAuth/OIDC authorization before profile import and indexing.

## Preconditions
- LinkedIn OAuth client credentials and an exact callback URI are configured.
- ProfileIngestionAgent and ProfileKnowledgeIngestion are available.
- No authentication or access-control bypass is required.

## Actions
1. Redirect the user to LinkedIn's authorization endpoint with a short-lived state value.
2. Validate state against the HTTP-only browser cookie and exchange the authorization code server-side.
3. Retrieve only fields permitted by the configured LinkedIn OAuth scopes.
4. Create a source-labelled knowledge document and index it through DocumentUploadHook.
5. Record the import outcome without logging tokens or profile contents.

## Failure Behavior
Reject invalid callbacks, expired state, unauthenticated imports, or unconfigured provider credentials with a structured client-safe error. Never collect passwords, expose tokens, or scrape authenticated pages.

## Responsible Agents
ProfileIngestionAgent, SecurityAgent, DocumentIngestionAgent

## Required Skills
ProfileKnowledgeIngestion, DocumentValidation, DocumentProcessing

## Example
"Trigger ProfileFetchHook after LinkedIn OAuth callback and report whether permitted profile data was indexed."
