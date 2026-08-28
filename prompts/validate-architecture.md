# Validate Architecture

## Purpose
Validate a proposed or existing change against system architecture rules.

## Required Agents
SolutionArchitectAgent, CleanArchitectureAgent, SOLIDAgent

## Required Skills
CodeQuality

## Required Hooks
ArchitectureValidationHook

## Usage
```text
@workspace Use the validate-architecture prompt to: validate a proposed or existing change against system architecture rules.
```

## Steps
1. Review layering, dependency direction, and interface usage.
2. check for duplicated agent/service responsibilities.
3. record the decision in architecture/ docs.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
