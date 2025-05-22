---
description: Build all application packages (core, db, api, web) and attempt to autofix errors.
---

This workflow builds all essential packages in the monorepo. If build errors occur, Cascade can attempt to diagnose and fix them.

**Steps:**

1.  **Ensure Dependencies are Installed:**
    Make sure all dependencies are up to date.
    ```bash
    bun install
    ```
    *Command should be run from the project root directory.*

2.  **Build Core Package:**
    Builds the `core` package. This is often a prerequisite for other packages.
    ```bash
    bun run --cwd packages/core build
    ```

3.  **Build DB Package:**
    Builds the `db` package.
    ```bash
    bun run --cwd packages/db build
    ```

4.  **Build API Package:**
    Builds the `api` package with environment variables loaded from the root .env file.
    ```bash
    bun run --cwd packages/api --env-file ../../.env build
    ```
    *This ensures environment variables like DATABASE_URL are correctly loaded.*

5.  **Build Web Package:**
    Builds the `web` package.
    ```bash
    bun run --cwd packages/web build
    ```

6.  **Review Build Output:**
    Check the output for any build errors.

7.  **AI-Assisted Error Fixing (If Necessary):**
    If there are build errors:
    *   Provide the error messages to Cascade.
    *   Cascade will attempt to diagnose the cause and propose solutions or apply fixes directly.
