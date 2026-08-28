# VectorDBIndexing

## Purpose
Handles index synchronization and re-indexing when embeddings change.

## Description
This skill packages the domain knowledge and conventions required to handles index synchronization and re-indexing when embeddings change. It is invoked by its related agents whenever a task falls within this scope, and should be referenced by GitHub Copilot Chat when working on related files.

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
VectorDatabaseAgent

## Related Hooks
VectorDBSyncHook

## Example
"Apply the VectorDBIndexing skill to implement/update <specific artifact> following this project's conventions."
