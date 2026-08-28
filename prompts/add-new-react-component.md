# Add New React Component

## Purpose
Add a new, accessible, tested React component to the frontend.

## Required Agents
ReactAgent, ComponentAgent, TypeScriptAgent, FrontendTestingAgent

## Required Skills
ReactDevelopment, TypeScriptDevelopment, Accessibility

## Required Hooks
FrontendBuildHook, FrontendTestHook, AccessibilityHook

## Usage
```text
@workspace Use the add-new-react-component prompt to: add a new, accessible, tested React component to the frontend.
```

## Steps
1. Define the component's props/interfaces.
2. implement it with semantic HTML and design tokens.
3. add unit tests.
4. verify accessibility and responsive behavior.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
