# AI-Assisted Coding Template

## Overview

This project provides a comprehensive, AI-optimized template designed to accelerate the planning and development of modern web applications. It leverages a structured, workflow-driven approach to guide you from initial business ideation through product definition to full-stack implementation, with explicit integration points for Artificial Intelligence at every stage.

The template is architected as a monorepo managed with Bun, adhering to industry best practices for code organization, security, performance, and documentation. It enforces consistent coding standards and architectural patterns to foster maintainable, high-quality code, ready for AI-assisted development and collaboration.

## Why This Template?

-   **Accelerated Development**: Streamline your development lifecycle with pre-defined workflows and AI assistance.
-   **Consistency & Quality**: Enforce best practices and coding standards from the outset.
-   **AI-Powered Efficiency**: Leverage AI for tasks like code generation, testing, documentation, and analysis.
-   **Scalable Foundation**: Build upon a modern, robust technology stack and project structure.
-   **Comprehensive Guidance**: Benefit from detailed rules and guidelines covering all aspects of development.

## Who Is This For?

-   **Developers & Teams**: Looking to rapidly prototype and build new applications with AI assistance.
-   **Startups**: Needing a structured approach to move quickly from idea to MVP.
-   **Organizations**: Aiming to standardize development practices and effectively integrate AI tools into their workflows.

## Key Features

-   **Guided Workflows**: Step-by-step processes in `.windsurf/workflows/` covering the entire project lifecycle, from business planning to deployment preparation.
-   **Integrated AI Assistance**: Explicit prompts and strategies for using AI tools effectively and ethically throughout development.
-   **Modern Technology Stack**: A curated selection of robust technologies for frontend, backend, and database development.
-   **Comprehensive Best Practices**: In-depth guidelines in `.windsurf/rules/` for project structure, coding conventions, security, performance, logging, error handling, testing, accessibility, ethical AI, prompt engineering, and AI tool selection.
-   **Monorepo Structure**: Organized using Bun for efficient management of multiple packages (`api`, `web`, `core`, `db`).
-   **Documentation-First Approach**: Templates and guidelines for business, product, and technical documentation.

## Technology Stack

### Frontend (`packages/web`)
-   **Framework**: React with Vite
-   **Language**: TypeScript
-   **Styling**: Tailwind CSS
-   **UI Components**: Shadcn UI (as per `frontend_guidelines.md`)
-   **State Management**: Zustand (or other, as needed)
-   **Routing**: React Router

### Backend (`packages/api`)
-   **Framework**: Hono
-   **Language**: TypeScript
-   **Runtime**: Node.js (managed via Bun)

### Database (`packages/db`)
-   **Database System**: PostgreSQL
-   **ORM**: Drizzle ORM

### Development Tools
-   **Package Manager & Runtime**: Bun
-   **Linting & Formatting**: Biome (configured for the project)
-   **Testing**: Vitest, React Testing Library

## Project Structure

This project follows a monorepo structure detailed in `.windsurf/rules/project_structure.md`. A high-level overview:

```
/
├── packages/
│   ├── api/         # Backend API (Hono, TypeScript)
│   ├── web/         # Frontend Application (React, TypeScript, Vite)
│   ├── core/        # Shared types, utilities, and business logic
│   └── db/          # Database schema (Drizzle ORM), migrations, seeds
├── docs/            # Project documentation (business, product, technical)
└── .windsurf/
    ├── rules/       # Guidelines and standards for development
    └── workflows/   # Step-by-step procedures for project tasks
```
Refer to `.windsurf/rules/project_structure.md` for detailed directory and file naming conventions.

## Core Concepts

### 1. AI-Assisted Development
This template is built with AI assistance in mind. Guidelines like `prompt_engineering_guidelines.md`, `ethical_ai_development_guidelines.md` provide a framework for leveraging AI tools responsibly and effectively.

### 2. Workflows (`.windsurf/workflows/`)
Workflows are step-by-step guides for various development phases and tasks. They often include suggested AI prompts and CLI commands. Adherence to these workflows ensures consistency and leverages the template's full potential. See `.windsurf/rules/workflows_guidelines.md` for usage details.

### 3. Rules & Guidelines (`.windsurf/rules/`)
These documents define the standards for the project, covering everything from coding conventions to security and performance. They are essential references throughout the development process.

## Getting Started

1.  **Clone the Repository**:
    ```bash
    git clone <repository-url>
    cd ai-coding-template
    ```
2.  **Install Dependencies**:
    ```bash
    bun install
    ```
3.  **Configure Environment**:
    Copy the example environment file and update it with your specific settings (e.g., database credentials):
    ```bash
    cp .env.example .env
    # Edit .env with your details
    ```
4.  **Follow Detailed Instructions**:
    Open and follow the [INSTRUCTIONS.md](./INSTRUCTIONS.md) file for a comprehensive guide to using this template.

## Navigating the Documentation

-   **[INSTRUCTIONS.md](./INSTRUCTIONS.md)**: Your primary guide for using this template, from planning to development.
-   **`.windsurf/rules/`**: Contains all the specific guidelines and standards for the project. Start by reviewing `project_structure.md` and `coding_conventions.md`.
-   **`.windsurf/workflows/`**: Holds the step-by-step workflows. `workflows_guidelines.md` explains how to use and enhance them.
-   **`docs/`**: This directory will house your project-specific documentation as you follow the workflows (e.g., `docs/product/business_plan.md`).

## Contributing

We welcome contributions to improve this template! Please see [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines on how to propose changes, report issues, or suggest new rules and workflows.

## License
Please see [LICENSE](./LICENSE) for details.
    