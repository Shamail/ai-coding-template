---
description: Project Scaffolding
---

# Project Scaffolding Workflow

## Overview
This workflow generates the complete monorepo structure for your project with all necessary configuration files and dependencies.

## Prerequisites
- Completed business plan, product plan, epics, and user stories
- User confirmation to proceed with scaffolding
- Optional: Any specific technology stack preferences or modifications

## Technology Stack
- **Backend API**: Hono with Bun
- **Database**: PostgreSQL with Drizzle ORM
- **Frontend**: React with Vite
- **Styling**: Tailwind CSS with Shadcn UI components
- **Routing**: React Router
- **Testing**: Bun Test
- **Package Management**: Bun

## Steps

1.  **Project Structure Guidance & Directory Creation Principle**
    -   This workflow generates the project's monorepo structure. The generation process **MUST** adhere to the guidelines defined in `.windsurf/rules/project_structure.md`.
    -   **Directory Creation Principle:** All specified directories in the subsequent steps will only be created if they do not already exist. The `.windsurf/` directory itself will not be targeted for creation or modification by this workflow.
    -   Before proceeding, ensure familiarity with `.windsurf/rules/project_structure.md`. This document is the source of truth for the overall directory layout, package-specific structures (API, Web, Core, DB), naming conventions, and file organization.
    -   Confirm the technology stack choices (listed in the "Technology Stack" section above) are compatible with the defined structure, or note any required minor adjustments.

2.  **Generate Root Project Structure and Core Directories**
    -   Create the primary root-level directories and the documentation structure:
        -   `packages/`
        -   `docs/`
            -   `docs/product/`
            -   `docs/product/epics/`
            -   `docs/product/user-stories/` (Further subdirectories like `[epic-name]/` within `user-stories/` will be created by the `/04-generate-user-stories` workflow as needed)
            -   `docs/api/`
            -   `docs/architecture/`
            -   `docs/guides/`
            -   `docs/todos/`
    -   These directories **MUST** be created as outlined in the "Monorepo Structure" and "Documentation Structure" sections of `.windsurf/rules/project_structure.md`.
    -   Generate root configuration files (these are files, not directories, and should be created after the root directories exist):
        -   `.env.example` - Environment variables template
        -   `package.json` - Root package with workspaces
        -   `tsconfig.base.json` - Base TypeScript configuration
        -   `README.md` - Project overview

3.  **Create API Package Directory (`packages/api`)**
    -   Create the `packages/api` directory.
    -   For detailed setup of the API package, including internal structure, configuration files, and essential entry points, refer to the `/05b-setup-api-application.md` workflow.

4.  **Create Web Package Directory (`packages/web`)**
    -   Create the `packages/web` directory.
    -   For detailed setup of the Web package, including internal structure, configuration files, UI library initialization (like Shadcn UI), and essential entry points, refer to the `/05c-setup-web-application.md` workflow.

5.  **Generate Core Package (`packages/core`)**
    -   Create the `packages/core` directory and its internal structure (including `src/` with subdirectories like `types/`, `utils/`, and `tests/`) as specified in the "Core Package Structure" section of `.windsurf/rules/project_structure.md`.
    -   Generate Core configuration files:
        -   `package.json` (dependencies as per Tech Stack guidelines and `project_structure.md`)
        -   `tsconfig.json` extending from base
    -   Ensure essential entry files like `packages/core/src/index.ts` are created.

6.  **Create DB Package Directory (`packages/db`)**
    -   Create the `packages/db` directory.
    -   For detailed setup of the DB package, including internal structure (schemas, migrations), configuration files, and essential entry points, refer to the `/05a-setup-db-package.md` workflow.

7. **Verify Root Project Structure**
   - Ensure all root-level directories and files are created correctly.
   - Verify that the root `package.json` has correct workspace configurations.
   - Detailed verification of individual packages (`api`, `web`, `db`, `core`) should be performed as part of their respective setup workflows.

## Output
A complete monorepo project structure with all necessary configuration files and dependencies, ready for development.