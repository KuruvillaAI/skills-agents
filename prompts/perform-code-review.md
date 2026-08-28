# Perform Code Review

## Purpose
Review a proposed change for quality, architecture, and convention compliance.

## Required Agents
CodeReviewAgent, CleanCodeAgent, SolidAgent

## Required Skills
CodeReview, CleanCode, CodeQuality

## Required Hooks
CodeReviewHook

## Usage
```text
@workspace Use the perform-code-review prompt to: review a proposed change for quality, architecture, and convention compliance.
```

## Steps
1. Review the diff against clean-code and SOLID standards.
2. check for architecture violations.
3. check tests exist and pass.
4. leave actionable feedback.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
