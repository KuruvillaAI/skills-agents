# Add New Database Table

## Purpose
Add a new table/model with a migration and repository.

## Required Agents
DatabaseAgent, SQLAgent, MigrationAgent, RepositoryAgent

## Required Skills
DatabaseDevelopment, SQLDevelopment, RepositoryDevelopment

## Required Hooks
DatabaseMigrationHook, BackendTestHook

## Usage
```text
@workspace Use the add-new-database-table prompt to: add a new table/model with a migration and repository.
```

## Steps
1. Design the schema.
2. write a migration.
3. add the ORM model.
4. implement the repository interface + implementation.
5. write unit/integration tests.

## Notes
- This prompt must be executed under `MasterOrchestrationAgent` coordination when it spans more than one repository.
- Do not skip test/QA steps even for small changes.
