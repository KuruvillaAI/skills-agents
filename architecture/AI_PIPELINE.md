# AI Pipeline Architecture

## Stages and Owning Agents

| Stage | Agent | Notes |
|---|---|---|
| Upload / ingest | `DocumentIngestionAgent`, `DocumentValidationAgent`, `DocumentProcessingAgent` | Validates, parses, cleans, chunks, versions |
| Profile source | `ProfileIngestionAgent` | Fetches public LinkedIn profile and bounded explicit public links; labels sources and creates a knowledge document |
| Embed | `EmbeddingAgent` | Configurable embedding provider (mock/local default, OpenAI optional) |
| Index | `VectorDatabaseAgent` | FAISS (default, local) or Pinecone (optional), behind one interface |
| Retrieve | `RetrievalAgent` | Query preprocessing, embedding, Top-K semantic search |
| Rerank | `RerankingAgent` | Relevance scoring, low-quality filtering |
| Assemble context | `ContextAssemblyAgent` | Dedup, size limits, source attribution |
| Enforce rules | `PromptEngineeringAgent`, `GroundingAgent` | System prompt cannot be overridden by user input |
| Apply personality | `PersonalityAgent` | Style only — never overrides grounding |
| Generate | `ResponseGenerationAgent`, `AIModelAgent`, `AIProviderAgent` | LLM call through a swappable provider interface |
| Validate response | `HallucinationDetectionAgent`, `GroundingAgent` | Reject/regenerate unsupported claims; refuse if evidence insufficient |

Before retrieval, `ConversationAgent` classifies exact generic conversational intents such as
greetings. These responses contain no knowledge claims, are marked ungrounded but not refused,
and do not weaken grounding for factual questions. All other messages continue through the full
retrieval, grounding, generation, and hallucination-validation pipeline.

## Provider Abstraction
`AIProviderAgent` defines `EmbeddingProvider` and `LLMProvider` interfaces. The backend ships with:
- A **mock/local provider** (deterministic, offline, no API key required) used by default and in tests.
- An **OpenAI-compatible provider** enabled via environment variables when an API key is supplied.

## Vector Database Abstraction
`VectorDatabaseAgent` defines a `VectorStore` interface implemented by:
- `FAISSVectorStore` (default, local, file-backed).
- `PineconeVectorStore` (optional, requires API key/environment configuration).

Switching backends is a configuration change only; no business logic depends on the concrete implementation.

## Grounding Guarantee
No factual response may skip `GroundingAgent`. If assembled context does not clear the relevance threshold, the pipeline short-circuits directly to the generic refusal without calling the LLM for content generation. The only pre-retrieval exception is an exact generic conversational intent, such as `hi` or `hello`; it may return a non-factual conversational response with no evidence.
