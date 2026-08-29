---
applyTo: "backend/app/**"
---

# Grounding Instructions

- The approved knowledge document is the single source of truth for everything the chatbot says about the user. If a claim is not supported by retrieved evidence, it must not be stated.
- Response pipeline order is mandatory: query validation → preprocessing → embedding → vector search → reranking → context assembly → evidence validation → system rules → personality → LLM → response validation → grounding validation → response.
- Priority order when rules conflict: Security > Grounding > System Rules > Evidence > Personality > Presentation. Personality must never override grounding or security.
- Exact generic conversational intents (for example, `hi`, `hello`, or `good morning`) may receive a non-factual conversational response before retrieval. These responses must contain no claims about the user, must be marked ungrounded rather than refused, and must not change the factual-question pipeline.
- If retrieved evidence is insufficient, return the generic refusal implemented once in `GroundingAgent` (e.g. "I'm sorry, but I don't have enough information in my knowledge document to answer that."). This must be a single, generic mechanism — never implement a question-specific refusal.
- Never implement hardcoded chatbot answers, FAQ dictionaries, or canned biography responses. All answers must be produced dynamically from retrieved context.
- `HallucinationDetectionAgent` must check every generated response against the retrieved evidence before it is returned; reject or regenerate on unsupported claims.
- Generic infrastructure/system messages (e.g. "the server is unavailable," "please try again") are allowed and are not considered hardcoded chatbot answers.
