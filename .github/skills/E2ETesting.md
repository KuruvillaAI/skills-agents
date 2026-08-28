# E2ETesting

## Purpose
Testing complete user workflows end to end.

## Description
This skill packages the domain knowledge and conventions required to testing complete user workflows end to end. It is invoked by its related agents whenever a task falls within this scope, and should be referenced by GitHub Copilot Chat when working on related files.

## Workflow
1. Identify that the current task matches this skill's purpose.
2. Apply the relevant conventions, patterns, and quality bars for this domain.
3. Produce or modify the artifact (code, config, or documentation).
4. Hand off to the related testing/QA agent for verification.

## Inputs
Task description, existing related code/config/docs, project conventions (see architecture/ and instructions/).

## Outputs
Implemented or updated artifact, plus any tests/documentation required by the change.

## Related Agents
E2ETestAgent

## Related Hooks
E2ETestHook

## Example
"Apply the E2ETesting skill to implement/update <specific artifact> following this project's conventions."
