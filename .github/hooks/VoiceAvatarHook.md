# VoiceAvatarHook

## Trigger
Voice or avatar features are modified

## Purpose
Verify optional voice/avatar features never bypass grounding or security.

## Preconditions
- The relevant repository is present and its dependencies are installed.
- Any upstream hooks required before this one have completed successfully.

## Actions
1. Detect that the trigger condition has occurred.
2. Invoke the responsible agent(s): VoiceUIAgent, AvatarAgent.
3. Apply the relevant skill(s): VoiceIntegration, AvatarIntegration.
4. Record the outcome (pass/fail) and any artifacts (logs, reports, evidence).

## Failure Behavior
- On failure, halt the current task and report the failure to `MasterOrchestrationAgent`.
- Do not proceed to dependent hooks/stages until the failure is resolved.
- Delegate the fix to the responsible specialist agent, then re-run this hook.

## Responsible Agents
VoiceUIAgent, AvatarAgent

## Required Skills
VoiceIntegration, AvatarIntegration

## Example
"Trigger VoiceAvatarHook after voice or avatar features are modified and report the result."
