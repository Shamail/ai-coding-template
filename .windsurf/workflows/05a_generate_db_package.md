---
description: Generate DB Schema from User Stories
---

This workflow translates user stories into Drizzle ORM PostgreSQL schemas, aiming for well-structured, maintainable, and consistent DBs based on product requirements.

**User Stories Source:** All user story files (e.g., `*.md`) within the `docs/product/user-stories/` directory and its subdirectories.
**DB Schemas Location:** `packages/db/src/schema/`

## Workflow Steps:

1.  **Ensure DB Package Directory Structure**
    - **Ensure `packages/db/` exists.** If it does not, create it (e.g., by running `mkdir -p packages/db` if in a shell environment). This is crucial as subsequent steps depend on this base directory.
    - The root `packages/db/` directory is typically created by the `/05-generate-project-scaffold.md` workflow. However, you should verify its existence before proceeding.
    - Once `packages/db/` is confirmed, ensure the core internal directory structure for the DB package exists. Create the following directories if they are missing, adhering to `project_structure.md`:
        - `packages/db/src/`
        - `packages/db/src/schema/`
        - `packages/db/src/migrations/`
        - `packages/db/src/utils/`
        - `packages/db/tests/`
    - Also, ensure the main entry point `packages/db/src/index.ts` and `packages/db/package.json` are created if they don't exist. Minimal content for `package.json` should define the package name (e.g., `@homing/db-package`) and any core dependencies like `drizzle-orm`, `pg`, `nanoid`. `index.ts` can initially just export from `./schema`.

2.  **Context & Story Selection:**
    *   Review project goals, epics (`docs/product/epics/`), existing DB schemas (`packages/db/src/schema/`).
    *   Note key guidelines: `project_structure.md`, `logging_guidelines.md`, `security_guidelines.md`.
    *   Collect all user story files (e.g., `*.md`) from the `docs/product/user-stories/` directory and all its subdirectories. These files will be the basis for data needs analysis.

2.  **Analyze Stories for Data Needs:**
    *   Identify key entities (e.g., User, Job).
    *   List attributes per entity (e.g., User: `firstName`, `email`).
    *   Define data types (e.g., `text`, `timestamp`, `integer`).
    *   Identify relationships (1:1, 1:N, N:N); specify FKs, join tables.
    *   Note constraints (`NOT NULL`, `UNIQUE`, defaults).
    *   Identify enums (e.g., `UserRole`, `JobStatus`).

3.  **Design Enum Schemas (if applicable):**
    *   **File:** `packages/db/src/schema/_enums.ts`
    *   For each enum:
        *   Define `pgEnum` (Drizzle ORM).
        *   Name: PascalCase (e.g., `UserRoleEnum`).
        *   Values: lowercase_snake_case (e.g., `'office_admin'`).
        *   Export `pgEnum`.
    *   **Example:** See `userRoleEnum` in `_enums.ts`.
    *   Create `_enums.ts` if needed; add `import { pgEnum } from 'drizzle-orm/pg-core';`.

4.  **Design Table Schemas:**
    *   **File:** `packages/db/src/schema/[entity-name].ts` (singular kebab-case).
    *   **SQL Table Name:** plural_snake_case (in `pgTable` call, e.g., `jobs`).
    *   **Drizzle Object Name:** pluralCamelCase (e.g., `jobs`).
    *   **Standard Columns (MUST HAVE):**
        *   `id`: `text('id').primaryKey().$defaultFn(() => nanoid())` (import `nanoid`).
        *   `createdAt`: `timestamp('created_at', { withTimezone: true }).defaultNow().notNull()`.
        *   `updatedAt`: `timestamp('updated_at', { withTimezone: true }).defaultNow().notNull().$onUpdate(() => new Date())`.
    *   **Columns:**
        *   Define per attributes using Drizzle `pg-core` types.
        *   Apply constraints (`.notNull()`, `.default()`, `.unique()`).
        *   For enum FKs, use enum object directly (e.g., `userRole: userRoleEnum('user_role').notNull()`).
    *   **Relationships (`relations` helper):**
        *   Define after `pgTable` (use `relations` from `drizzle-orm`).
        *   Define 1:1, 1:N, N:N clearly.
        *   **Example:** See `users`, `companies` schemas.
    *   **Indexes:** For frequently queried/joined columns (esp. FKs), use `index('idx_name').on(table.column)`.
    *   **Type Exports:** Export `Select` & `Insert` types (e.g., `export type Job = typeof jobs.$inferSelect;`).
    *   **Imports:** Ensure necessary imports (`drizzle-orm`, `pg-core`, `nanoid`, related schemas).

5.  **Update Schema Index File:**
    *   **File:** `packages/db/src/schema/index.ts`
    *   Export new table schemas, their `Select`/`Insert` types, and new enums.
    *   Sort exports alphabetically.

6.  **Review and Verify:**
    *   Check schemas vs. stories for all requirements.
    *   Verify naming: kebab-case files, plural_snake_case SQL tables, pluralCamelCase Drizzle objects, PascalCase enums.
    *   Verify relationships are correct and sensible.
    *   Check consistency with existing schemas.

7.  **Summarize & Next Steps:**
    *   Summarize files created/modified.
    *   Remind USER: Generate migrations (`bun run packages/db/migrate` or `bunx drizzle-kit generate:pg`).
    *   Then: Review SQL migration, then apply (`bun run packages/db/db:push`).

## Guiding Principles:

*   **Examples:** `user.ts`, `company.ts` in `packages/db/src/schema/` for structure, names, std cols, relations.
*   **Atomicity:** Normalized tables; avoid redundant data.
*   **Clarity:** Descriptive table/column names.
*   **Consistency:** Follow `packages/db` patterns.
*   **Security:** Secure sensitive data (e.g., hash passwords). Consider sensitivity in column definitions.
*   **Performance:** Index frequently queried/joined columns.

Follow these steps to generate robust, accurate DB schemas for the app's data layer.
