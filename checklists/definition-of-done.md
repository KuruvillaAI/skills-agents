# Definition of Done Checklist

- [ ] Requirement/acceptance criteria clarified
- [ ] Correct repository/repositories identified and built in order (skills-agents → backend → frontend → infra)
- [ ] Implementation follows architecture rules (layering, DI, interfaces)
- [ ] No hardcoded chatbot answers introduced
- [ ] Unit tests added/updated for every new/changed file where feasible
- [ ] Integration tests added/updated and passing (if boundary-crossing)
- [ ] The FULL existing automated test suite (not just new tests) was run and passes with
      zero failures for every repository touched -- see UnitTestHook / IntegrationTestHook /
      RegressionTestingHook. A previously-passing test that now fails must be fixed, not
      deleted, skipped, or weakened.
- [ ] Security review passed (no secrets, input validated, OWASP checks)
- [ ] Grounding/prompt-injection review passed (if AI pipeline touched)
- [ ] Lint/format passing
- [ ] Documentation updated (README/architecture/QA)
- [ ] Visual QA passed (if UI/workflow affected)
- [ ] Regression areas identified and re-tested
- [ ] No unresolved BLOCKER/CRITICAL defects
