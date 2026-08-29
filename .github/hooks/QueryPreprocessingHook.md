# QueryPreprocessingHook

## Trigger
A user submits a chat query

## Purpose
Normalize the query and classify exact generic conversational intents before embedding and retrieval.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke `ConversationAgent` to classify exact generic conversational intents.
3. If no conversational intent is found, invoke `RetrievalAgent`.
4. Apply the relevant skill(s): `ConversationalIntent` and, for factual input, `RetrievalOrchestration`.
5. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
ConversationAgent, RetrievalAgent

## Required Skills
ConversationalIntent, RetrievalOrchestration

## Example
"Trigger QueryPreprocessingHook after a user submits a chat query and report the result."
