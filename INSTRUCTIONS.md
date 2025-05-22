# AI-Assisted Coding Template: Detailed Instructions

## Introduction

Welcome to the AI-Assisted Coding Template! This document provides comprehensive, step-by-step instructions to guide you through planning, building, and iterating on your web application using this template. It's designed to help you leverage AI effectively at each stage of the development lifecycle.

## Table of Contents

1.  [Prerequisites](#prerequisites)
2.  [Initial Setup](#initial-setup)
3.  [Core Concepts Explained](#core-concepts-explained)
    *   [The Monorepo Structure](#the-monorepo-structure)
    *   [Workflows (`.windsurf/workflows/`)](#workflows-windsurfworkflows)
    *   [Rules & Guidelines (`.windsurf/rules/`)](#rules--guidelines-windsurfrules)
    *   [AI Tooling & Ethics](#ai-tooling--ethics)
4.  [Phase 1: Project Planning & Definition](#phase-1-project-planning--definition)
    *   [Workflow 01: Business Plan Generation](#workflow-01-business-plan-generation)
    *   [Workflow 02: Product Plan Generation](#workflow-02-product-plan-generation)
    *   [Workflow 03: Epic Generation](#workflow-03-epic-generation)
    *   [Workflow 04: User Story Generation](#workflow-04-user-story-generation)
5.  [Phase 2: Project Implementation & Development](#phase-2-project-implementation--development)
    *   [Project Scaffolding & Package Setup](#project-scaffolding--package-setup)
    *   [Running the Applications](#running-the-applications)
    *   [Implementing Features](#implementing-features)
6.  [Phase 3: Development Support Workflows & Tasks](#phase-3-development-support-workflows--tasks)
    *   [Building the Applications](#building-the-applications)
    *   [Code Formatting and Linting](#code-formatting-and-linting)
    *   [Generating Tests (AI-Assisted)](#generating-tests-ai-assisted)
    *   [AI for Code Generation, Refactoring, and Debugging](#ai-for-code-generation-refactoring-and-debugging)
    *   [Generating Documentation Snippets](#generating-documentation-snippets)
7.  [Phase 4: CI/CD and Infrastructure (Guidance)](#phase-4-cicd-and-infrastructure-guidance)
8.  [Best Practices Checklist (Essential Rules)](#best-practices-checklist-essential-rules)
9.  [Workflow Tracking and Enhancement](#workflow-tracking-and-enhancement)
10. [Troubleshooting](#troubleshooting)
11. [Seeking Further Assistance](#seeking-further-assistance)

## Prerequisites

Before you begin, ensure you have the following installed:

-   [Bun](https://bun.sh/): For package management, script execution, and as a runtime.
-   [PostgreSQL](https://www.postgresql.org/): The database system used by this template. Ensure it's installed and running.
-   [Git](https://git-scm.com/): For version control.
-   [Windsurf](https://windsurfrs.com/): For AI coding assistance. 
-   Basic understanding of: TypeScript, React, Node.js, Hono, REST APIs, and general web development concepts.

## Initial Setup

1.  **Clone the Repository**:
    ```bash
    git clone <repository-url>
    cd ai-coding-template
    ```

2.  **Configure Environment Variables**:
    Copy the example environment file. This file is gitignored and will store your local secrets and configurations.
    ```bash
    cp .env.example .env
    ```
    Now, edit the newly created `.env` file in the project root. Fill in your `DATABASE_URL` (e.g., `postgresql://USER:PASSWORD@HOST:PORT/DATABASE_NAME`) and any other required variables.

## Core Concepts Explained

Understanding these core concepts is key to effectively using this template.

### The Monorepo Structure

This template uses a monorepo structure, managed by Bun workspaces, to organize different parts of your application (API, web frontend, shared core logic, database schema).
-   **`packages/api`**: Backend Hono application.
-   **`packages/web`**: Frontend React application.
-   **`packages/core`**: Shared TypeScript code (types, utilities) usable by both `api` and `web`.
-   **`packages/db`**: Drizzle ORM schema, migrations, and database-related utilities.
For a detailed breakdown of the directory structure and naming conventions, **you must refer to `.windsurf/rules/project_structure.md`**.

### Workflows (`.windsurf/workflows/`)

Workflows are markdown files located in the `.windsurf/workflows/` directory. They provide step-by-step instructions for various project phases and tasks, from initial planning to development support.
-   **Execution**: Most workflows are guides for manual execution. You'll copy prompts to your AI assistant, run CLI commands in your terminal, and create/edit files as instructed. Some steps might include `// turbo` or `// turbo-all` annotations, which are for specific AI environments that can automate command execution.
-   **AI Integration**: Workflows explicitly suggest when and how to use AI, often providing example prompts.
-   **Tracking**: As you complete workflows, track their execution in `docs/workflow-checklist.md`.
-   **Enhancement**: If you find friction or areas for improvement in any workflow, document your observations in `docs/workflow-enhancements.md`.
**Always consult `.windsurf/rules/workflows_guidelines.md` for detailed instructions on executing, tracking, and enhancing workflows.**

### Rules & Guidelines (`.windsurf/rules/`)

The `.windsurf/rules/` directory contains markdown files that define the standards, conventions, and best practices for this project. These cover:
-   Coding conventions (`coding_conventions.md`)
-   Frontend (`frontend_guidelines.md`) and Backend (`backend_guidelines.md`) specifics
-   Security (`security_guidelines.md`), Performance (`performance_guidelines.md`)
-   Logging (`logging_guidelines.md`), Error Handling (`error_handling_guidelines.md`)
-   Testing (`testing_guidelines.md`), Documentation (`documentation.md`), Accessibility (`accessibility_guidelines.md`)
-   And crucial AI-related guidelines (see next section).
**Consult these rules frequently throughout development to ensure consistency and quality.**

### AI Tooling & Ethics

This template encourages the responsible and effective use of AI. Key guidelines include:
-   **`.windsurf/rules/prompt_engineering_guidelines.md`**: Teaches you how to craft effective prompts for better AI responses.
-   **`.windsurf/rules/ethical_ai_development_guidelines.md`**: Outlines ethical considerations when using AI in development.
Familiarize yourself with these before heavily relying on AI tools.

## Phase 1: Project Planning & Definition

Follow these workflows sequentially to define your product. Outputs are typically stored in the `docs/product/` directory.

### Workflow 01: Business Plan Generation
-   **File**: `.windsurf/workflows/01-generate-business-plan.md`
-   **Purpose**: Guides you in creating a foundational business plan using AI assistance for drafting sections like executive summary, problem/solution, target market, etc.
-   **Output**: `docs/product/business_plan.md`

### Workflow 02: Product Plan Generation
-   **File**: `.windsurf/workflows/02-generate-product-plan.md`
-   **Purpose**: Helps define your product's vision, core functionalities, user personas, and success metrics, based on the business plan. AI assists in brainstorming and structuring.
-   **Output**: `docs/product/product_plan.md`

### Workflow 03: Epic Generation
-   **File**: `.windsurf/workflows/03-generate-epics.md`
-   **Purpose**: Breaks down the product plan into larger, manageable work items called epics. AI helps draft epic details including goals, scope, and potential user stories.
-   **Output**: `docs/product/epics.md` (index) and individual epic files in `docs/product/epics/eX-[epic-name].md`.

### Workflow 04: User Story Generation
-   **File**: `.windsurf/workflows/04-generate-user-stories.md`
-   **Purpose**: Creates detailed user stories from your epics, including descriptions, acceptance criteria, and priorities. This workflow offers different modes for AI-assisted story generation.
-   **Output**: Individual user story files in `docs/product/user-stories/[epic-name-kebab-case]/[story-name-kebab-case].md`.

## Phase 2: Project Implementation & Development

With planning complete, you can start building. This phase involves setting up the project packages and implementing features. While specific `.md` workflow files for initial scaffolding (e.g., `05-scaffold-project.md`) are not detailed in the provided file map, the general process is as follows:

### Project Scaffolding & Package Setup
1.  **Database Setup (`packages/db`)**:
    *   Define your database schema using Drizzle ORM in `packages/db/src/schema/`. Refer to `backend_guidelines.md` and Drizzle ORM documentation.
    *   Generate and apply migrations:
        ```bash
        bun --cwd packages/db run generate-migrations
        bun --cwd packages/db run migrate
        ```
2.  **API Setup (`packages/api`)**:
    *   Initialize your Hono routes, services, and middleware according to `backend_guidelines.md` and `project_structure.md`.
    *   Connect to the database using services from `packages/db`.
3.  **Web Frontend Setup (`packages/web`)**:
    *   Structure your React components, pages, hooks, and routes as per `frontend_guidelines.md` and `project_structure.md`.
    *   Set up state management (e.g., Zustand) and data fetching.
4.  **Core Package (`packages/core`)**:
    *   Place shared TypeScript types, interfaces, and utility functions here. This helps maintain consistency and reduces code duplication between the API and web packages.

### Running the Applications

-   **API Development Server**:
    ```bash
    bun --cwd packages/api run dev
    ```
    Ensure your `.env` file has the correct `API_PORT` and `DATABASE_URL`.

-   **Web Frontend Development Server**:
    ```bash
    bun --cwd packages/web run dev
    ```
    This will typically start Vite's dev server, often on `http://localhost:5173`.

### Implementing Features
1.  **Pick a User Story**: Select a user story from `docs/product/user-stories/`.
2.  **Understand Requirements**: Review the story's description and acceptance criteria.
3.  **Consult Guidelines**: Refer to relevant rules in `.windsurf/rules/` (e.g., `coding_conventions.md`, `security_guidelines.md`, `frontend_guidelines.md`, `backend_guidelines.md`).
4.  **Code Implementation**:
    *   Write code for the API, web frontend, and any shared core logic.
    *   Use AI for assistance (see "AI for Code Generation..." below).
5.  **Write Tests**: Implement unit, integration, and potentially E2E tests. See `testing_guidelines.md`.
6.  **Review and Refactor**: Ensure code quality, adherence to conventions, and performance.
7.  **Document**: Update or create necessary code comments and documentation as per `documentation.md`.

## Phase 3: Development Support Workflows & Tasks

Leverage these processes to maintain quality and efficiency.

### Building the Applications
To create production builds:
-   **API**:
    ```bash
    bun --cwd packages/api run build
    ```
-   **Web Frontend**:
    ```bash
    bun --cwd packages/web run build
    ```
Build outputs are typically placed in `dist/` directories within each package.

### Code Formatting and Linting
This template uses Biome for formatting and linting.
-   **Check formatting and linting**:
    ```bash
    bun check:all
    ```
-   **Apply formatting and lint fixes**:
    ```bash
    bun fix:all
    ```
    It's highly recommended to integrate Biome with your VS Code editor for real-time feedback and formatting on save.

### Generating Tests (AI-Assisted)
-   Refer to `.windsurf/rules/testing_guidelines.md` which mentions leveraging AI for test generation, potentially through a workflow like `/.windsurf/workflows/ai-generate-tests.md` (if this file exists or you create a similar process).
-   **Example AI Prompt**: "Generate Vitest unit tests for the following TypeScript function [paste function code], covering [specific scenarios like happy path, edge cases, error handling]."

### AI for Code Generation, Refactoring, and Debugging
-   Use your AI assistant to generate boilerplate code, suggest refactorings, explain complex code snippets, or help debug issues.
-   Always follow `prompt_engineering_guidelines.md` for effective AI interaction.

### Generating Documentation Snippets
-   AI can help draft JSDoc comments, README sections, or explain code for documentation purposes.
-   **Example AI Prompt**: "Generate JSDoc comments for this TypeScript function: [paste function code], including parameter descriptions, return type, and an example."
-   Refer to `documentation.md` for overall documentation standards.

## Phase 4: CI/CD and Infrastructure (Guidance)

-   **CI/CD Pipeline**: The original `INSTRUCTIONS.md` mentioned a workflow like `.windsurf/workflows/setup_ci_cd_pipeline.md`. If this exists, follow it to set up basic continuous integration/continuous deployment using GitHub Actions or a similar service. This typically includes steps for linting, testing, building, and deploying your application.

## Best Practices Checklist (Essential Rules)

Regularly consult these guidelines:

-   **Project Structure**: `.windsurf/rules/project_structure.md`
-   **Coding Conventions**: `.windsurf/rules/coding_conventions.md`
-   **Frontend Development**: `.windsurf/rules/frontend_guidelines.md`
-   **Backend Development**: `.windsurf/rules/backend_guidelines.md`
-   **Security**: `.windsurf/rules/security_guidelines.md`
-   **Performance**: `.windsurf/rules/performance_guidelines.md`
-   **Logging**: `.windsurf/rules/logging_guidelines.md`
-   **Error Handling**: `.windsurf/rules/error_handling_guidelines.md`
-   **Testing**: `.windsurf/rules/testing_guidelines.md`
-   **Documentation**: `.windsurf/rules/documentation.md`
-   **Accessibility**: `.windsurf/rules/accessibility_guidelines.md`
-   **Prompt Engineering**: `.windsurf/rules/prompt_engineering_guidelines.md`
-   **Ethical AI Development**: `.windsurf/rules/ethical_ai_development_guidelines.md`
-   **Workflow Usage**: `.windsurf/rules/workflows_guidelines.md`

## Workflow Tracking and Enhancement

As per `.windsurf/rules/workflows_guidelines.md`:
-   **Track completed workflows**: Update `docs/workflow-checklist.md` (create it if it doesn't exist) after finishing each workflow.
-   **Document enhancement ideas**: Log any issues, ambiguities, or improvement suggestions for workflows in `docs/workflow-enhancements.md` (create it if it doesn't exist).

## Troubleshooting

### Environment Variable Loading
If your application (especially the API) isn't picking up environment variables from the root `.env` file when run directly within a package directory:
-   **Bun Scripts**: When running scripts defined in a package's `package.json` from the root (e.g., `bun run --filter=@my-package/api dev`), Bun typically handles `.env` loading from the root.
-   **Direct Execution within Package**: If running a script directly from within a package directory (e.g., `cd packages/api && bun run src/index.ts`), you might need to explicitly point to the root `.env` file:
    ```bash
    bun --env-file=../../.env run src/index.ts
    ```
    Or, if using a `dev` script inside `packages/api/package.json` like `"dev": "bun run src/index.ts"`, you can modify it to:
    `"dev": "bun --env-file=../../.env run src/index.ts"`
    Then run `bun --cwd packages/api run dev`.
-   **VS Code Debugger (`launch.json`)**: For debugging sessions, ensure your `.vscode/launch.json` configurations load the environment file. Example:
    ```json
    {
      "version": "0.2.0",
      "configurations": [
        {
          "type": "node",
          "request": "launch",
          "name": "API Dev Server (Debug)",
          "runtimeExecutable": "bun",
          "runtimeArgs": ["run", "dev"],
          "cwd": "${workspaceFolder}/packages/api", // Important for relative paths in API code
          "envFile": "${workspaceFolder}/.env" // Loads from root .env
        },
        {
          "type": "chrome", // Or "msedge"
          "request": "launch",
          "name": "Web App Dev Server (Debug)",
          "url": "http://localhost:5173", // Adjust if your web dev port is different
          "webRoot": "${workspaceFolder}/packages/web",
          // "preLaunchTask": "bun: dev -w packages/web" // If you have a tasks.json setup
        }
      ]
    }
    ```
    For `preLaunchTask`, you might need a `.vscode/tasks.json`.

### Common Issues
1.  **Database Connection**: Verify PostgreSQL is running. Double-check credentials in `.env`. Ensure migrations are up-to-date (`bun --cwd packages/db run migrate`).
2.  **Build Errors**: Run `bun install` if you suspect dependency issues. Check TypeScript errors carefully. Use `bun fix:all` for linting/formatting issues.
3.  **Type Conflicts/Module Resolution**: Ensure `tsconfig.json` paths and references are correct, especially for the monorepo setup.

## Seeking Further Assistance

If you encounter issues not covered here or have suggestions for improving the template itself, please refer to [CONTRIBUTING.md](./CONTRIBUTING.md) for guidance on how to raise issues or propose changes.
```
    