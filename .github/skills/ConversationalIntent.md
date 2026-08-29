# ConversationalIntent

## Purpose
Classify exact generic conversational intents before document retrieval so common greetings receive a natural response.

## Workflow
1. Normalize the validated chat message.
2. Match only a finite set of exact generic intents such as `hi`, `hello`, and time-of-day greetings.
3. Return a non-factual conversational response with no knowledge evidence for a match.
4. Hand every other message to retrieval and grounding.
5. Add unit and integration coverage for recognized intents and factual-question preservation.

## Inputs
A validated chat message and the existing conversation session.

## Outputs
A conversational response, or an explicit no-match result that continues to retrieval.

## Related Agents
ConversationAgent, RetrievalAgent, GroundingAgent, BackendTestingAgent

## Related Hooks
QueryPreprocessingHook, GroundingValidationHook, PostDeploymentQAHook

## Example
"Apply ConversationalIntent to ensure `hello` is answered conversationally while an unsupported factual question still receives the generic grounding refusal."
