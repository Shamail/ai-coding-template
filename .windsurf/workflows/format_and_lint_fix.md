---
description: Format codebase and apply lint fixes using Biome.
---

This workflow helps maintain code quality by formatting and linting the entire monorepo.

**Steps:**

1.  **Format Code:**
    Formats all supported files in the project using Biome.
    ```bash
    bun run format
    ```
    *Command should be run from the project root directory.*

2.  **Lint and Auto-fix Code:**
    Checks for linting errors and automatically applies fixes where possible using Biome.
    ```bash
    bun run lint
    ```
    *Command should be run from the project root directory.*

3.  **Review Changes:**
    After the commands complete, review any changes made by Biome and address any lint errors that could not be automatically fixed.
