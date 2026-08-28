---
applyTo: "**/*.md"
---

# Documentation Instructions

- Documentation is living: update the relevant README, architecture doc, or QA doc in the same change that alters behavior — do not defer documentation to a later task.
- Every agent `.md` file must follow the standard template (Purpose, Responsibilities, Scope, Inputs, Outputs, Technologies, Skills Used, Hooks Used, Agents It Can Delegate To, Agents It Must Not Duplicate, Workflow, Architecture Rules, Security Rules, Testing Rules, Documentation Rules, Example Usage, Example Copilot Prompts).
- Every skill `.md` file must define its purpose, workflow, inputs, outputs, related agents, related hooks, and an example.
- Every hook `.md` file must define its trigger, purpose, preconditions, actions, failure behavior, responsible agents, required skills, and an example.
- Keep repository-level READMEs accurate: setup steps, environment variables, how to run tests, and how to start the service must always match reality.
- Never document QA knowledge or engineering/architecture internals inside content that is retrievable by the public chatbot's knowledge base.
