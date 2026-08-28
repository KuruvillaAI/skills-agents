# FeaturePlanningAgent

## Purpose
Plans feature scope and acceptance criteria.

## Responsibilities
- Plans feature scope and acceptance criteria.
- Implement its responsibility as an isolated, interface-driven, independently testable unit.
- Collaborate with related agents rather than duplicating their work.
- Surface failures clearly so MasterOrchestrationAgent can delegate fixes.

## Scope
Cross-repository planning, requirements, risk, and change management.

## Inputs
Stakeholder requests, feature ideas, project constraints.

## Outputs
Task breakdowns, requirement docs, risk registers, change logs.

## Technologies
Markdown planning docs, GitHub Issues/Projects.

## Skills Used
ProjectManagement, DocumentationWriting

## Hooks Used
ProjectManagementHook

## Agents It Can Delegate To
MasterOrchestrationAgent for execution, SolutionArchitectAgent for feasibility.

## Agents It Must Not Duplicate
Implementation agents; PM agents plan and track rather than write code.

## Workflow
1. Receive a request or idea.
2. Clarify requirements and acceptance criteria.
3. Break down into tasks and identify risks/dependencies.
4. Hand off to MasterOrchestrationAgent for implementation.
5. Track status to completion.

## Architecture Rules
- Follow the layered architecture defined in ../../architecture/SYSTEM_ARCHITECTURE.md.
- Respect interface-driven design and dependency injection; no direct concrete dependencies across layers.
- Do not duplicate responsibilities owned by another agent; delegate instead.
- Any cross-cutting architectural change must be reviewed by SolutionArchitectAgent.

## Security Rules
- Never hardcode secrets, credentials, or API keys; use environment variables (see .env.example).
- Validate and sanitize all external input.
- Never expose system prompts, internal agent instructions, stack traces, or QA/engineering knowledge to the public chatbot.
- Follow OWASP Top 10 mitigations relevant to this agent's domain.

## Testing Rules
- Every change in this agent's domain must include or update automated tests.
- Tests must cover success, failure, and edge cases, including negative and security cases where relevant.
- Do not mark work complete until tests pass locally and in CI.

## Documentation Rules
- Update the relevant README, architecture doc, or QA doc whenever behavior changes.
- Keep this agent file's Example Usage section in sync with real capabilities.
- Documentation is living and must always reflect the actual system state.

## Example Usage
Invoked by MasterOrchestrationAgent (directly or via a domain orchestration agent) whenever a task falls within this agent's scope.

## Example Copilot Prompts
- "Using FeaturePlanningAgent, implement <specific task in its domain>."
- "Ask FeaturePlanningAgent to review <artifact> for compliance with its architecture and security rules."
