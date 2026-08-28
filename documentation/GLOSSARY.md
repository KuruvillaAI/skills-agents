# Glossary

- **Digital Twin**: The chatbot persona that answers as a virtual version of the user, grounded strictly in the approved knowledge document.
- **Grounding**: The requirement that every chatbot claim be supported by retrieved evidence from the approved document.
- **Refusal**: The generic, non-question-specific message returned when insufficient evidence exists to answer.
- **Hallucination**: A generated claim not supported by retrieved evidence.
- **Chunk**: A segment of a source document sized for embedding and retrieval.
- **Top-K**: The number of highest-scoring chunks retrieved for a query.
- **Reranking**: Re-scoring retrieved chunks for relevance before context assembly.
- **QA Knowledge**: Internal application/feature/test/defect knowledge, never exposed to the chatbot.
- **Visual QA**: Manual, browser-based verification performed by `VisualQAAgent`.
