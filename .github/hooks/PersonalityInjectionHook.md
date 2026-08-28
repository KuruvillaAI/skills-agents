# PersonalityInjectionHook

## Trigger
A response is about to be generated

## Purpose
Apply the derived personality/tone without altering factual content or grounding.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): PersonalityAgent.
3. Apply the relevant skill(s): PersonalityInjection.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
PersonalityAgent

## Required Skills
PersonalityInjection

## Example
"Trigger PersonalityInjectionHook after a response is about to be generated and report the result."
