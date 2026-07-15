---
name: liquibase-migration
description: >
  Creates formatted SQL Liquibase database migration scripts with tables, 
  constraints, and foreign keys from the entity model. Use when the user
  asks to "create a migration", "generate SQL scripts", "set up database tables",
  "write a Liquibase migration", or mentions schema migration, DB migration,
  database versioning, or SQL migration files.
tags:
  - developer
  - database
  - backend
---

# Liquibase Migration

## Instructions

Create Liquibase formatted SQL database migration scripts based on the entity model and use cases.
By default, primary keys should use UUIDs unless specified otherwise.
Always include an explicit rollback script/statement for every changeset.

## DO NOT

- Forget the `--liquibase formatted sql` header at the top of the file.
- Skip foreign key constraints defined in the entity model.
- Create migrations that drop existing tables without explicit user confirmation.

## File Naming Convention

Liquibase versioned migrations in this project follow this naming pattern (e.g., inside `db/changelog/postgresql/`):

```
001-create-me-istanza.sql
002-create-me-utente-account.sql
003-create-me-documento.sql
```

## Example Migration

```sql
--liquibase formatted sql

--changeset <author>:003-create-me-documento context:postgresql
--comment: UC-003 - creates me_documento table for storing uploaded document metadata
CREATE TABLE me_documento (
    id                  UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    istanza_id          UUID NOT NULL,
    nome_file_originale VARCHAR(500) NOT NULL,
    size_bytes          BIGINT,
    repository          VARCHAR(50),
    external_id         VARCHAR(200),
    tipo_documento      VARCHAR(50) NOT NULL,
    mime_type           VARCHAR(100),
    file_hash           VARCHAR(256),
    trascrizione_testo  TEXT,
    
    CONSTRAINT fk_me_documento_istanza FOREIGN KEY (istanza_id) REFERENCES me_istanza(id)
);

--rollback DROP TABLE me_documento;
```

## Workflow

1. Read `docs/entity_model.md`
2. Read existing migrations to determine the next version number
3. Create sequence definitions for each entity **only** if the entity uses numeric IDs. (For UUID primary keys, skip this and use `DEFAULT gen_random_uuid()`).
4. Create table definitions with columns, constraints, and foreign keys
5. Order tables so that referenced tables are created before referencing tables
6. Add Liquibase preconditions (`--precondition-sql-check` or similar) where applicable to make migrations safe and idempotent.
7. Validate the migration:
    - Verify all entities from the entity model have corresponding tables
    - Verify all foreign keys reference tables that are created in the same or earlier migration
    - Verify sequence names follow the pattern `{table_name}_seq` (if applicable)
    - Verify the SQL syntax is valid for the target database
8. Write the corresponding `--rollback` statements at the bottom for every changeset.
9. Ensure each changeset is atomic; do not bundle unrelated schema changes into a single changeset.
10. Remind the user to include this new file in the main `db.changelog-master.yaml` if it doesn't auto-include files from the directory.


