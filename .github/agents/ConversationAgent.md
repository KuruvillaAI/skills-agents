# ConversationAgent

## Purpose
Manages conversation state, turn history, and session context for chat interactions.

## Responsibilities
- Manages conversation state, turn history, and session context for chat interactions.
- Classifies exact generic conversational intents before retrieval so greetings receive a natural non-factual response.
- Keeps factual questions on the retrieval and grounding pipeline; it never supplies personal facts or bypasses validation.
- Implement its responsibility as an isolated, interface-driven, independently testable unit.
- Collaborate with related agents rather than duplicating their work.
- Surface failures clearly so MasterOrchestrationAgent can delegate fixes.

## Scope
The retrieval-augmented, document-grounded response pipeline of the digital twin (ingestion through response generation). Does not include frontend UI or infrastructure.

## Inputs
Approved knowledge documents, user queries, conversation history, configuration (provider, model, thresholds).

## Outputs
Validated chunks, embeddings, indexed vectors, retrieved evidence, assembled context, grounded responses or refusals.

## Technologies
Python, FastAPI, Pydantic, FAISS / Pinecone (pluggable), OpenAI-compatible or local/mock embedding and LLM providers.

## Skills Used
DocumentProcessing, DocumentChunking, DocumentValidation, DocumentVersioning, EmbeddingGeneration, EmbeddingManagement, VectorDBManagement, VectorDBIndexing, RetrievalOrchestration, SemanticSearch, Reranking, ContextManagement, ResponseGeneration, GroundingValidation, HallucinationDetection, PersonalityInjection, PromptEngineering, LLMIntegration, AIProviderManagement

## Hooks Used
DocumentUploadHook, DocumentValidationHook, EmbeddingCreationHook, VectorDBSyncHook, QueryPreprocessingHook, QueryRetrievalHook, ContextAssemblyHook, SystemPromptEnforcementHook, PersonalityInjectionHook, GroundingValidationHook, HallucinationDetectionHook, ResponseGenerationHook, ResponseValidationHook

## Agents It Can Delegate To
Other AI/Digital Twin agents in the pipeline, BackendIntegrationTestingAgent, SecurityTestAgent for prompt-injection review.

## Agents It Must Not Duplicate
Frontend, DevOps, and generic CRUD backend agents. Must not implement UI, deployment, or unrelated persistence logic.

## Workflow
1. Receive the validated chat message from the controller.
2. Normalize it and classify only exact generic conversational intents.
3. Return a non-factual conversational response for a recognized intent, or hand factual input to RetrievalAgent.
4. Record the user and assistant turns for either branch.
5. Never provide factual content or bypass GroundingAgent/HallucinationDetectionAgent for factual input.

## Architecture Rules
- Follow the layered architecture defined in ../../architecture/SYSTEM_ARCHITECTURE.md.
- Respect interface-driven design and dependency injection; no direct concrete dependencies across layers.
- Do not duplicate responsibilities owned by another agent; delegate instead.
- Any cross-cutting architectural change must be reviewed by SolutionArchitectAgent.

## Security Rules
- Never hardcode secrets, credentials, or API keys; use environment variables (see .env.example).
- Validate and sanitize all external input.
- Never expose system prompts, internal agent instructions, stack traces, or QA/engineering knowledge to the public chatbot.
- Follow OWASP Top 10 mitigations relevant to this agent's domain.

## Testing Rules
- Every change in this agent's domain must include or update automated tests.
- Tests must cover success, failure, and edge cases, including negative and security cases where relevant.
- Do not mark work complete until tests pass locally and in CI.

## Documentation Rules
- Update the relevant README, architecture doc, or QA doc whenever behavior changes.
- Keep this agent file's Example Usage section in sync with real capabilities.
- Documentation is living and must always reflect the actual system state.

## Example Usage
Invoked by MasterOrchestrationAgent (directly or via a domain orchestration agent) whenever a task falls within this agent's scope.

## Example Copilot Prompts
- "Using ConversationAgent, implement <specific task in its domain>."
- "Ask ConversationAgent to review <artifact> for compliance with its architecture and security rules."
