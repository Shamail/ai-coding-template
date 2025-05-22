---
trigger: always_on
---

# Technology Stack Guidelines

## 1. Introduction

This document outlines the official technology stack for the Homing.io project. Adherence to this stack is crucial for maintaining consistency, ensuring compatibility, streamlining onboarding, and facilitating efficient development and collaboration, especially when leveraging AI-assisted coding tools.

## 2. Core Technology Stack

The following technologies have been selected to build and support our platform:

### 2.1. Frontend (packages/web)

*   **Framework/Library:** React (with Vite for build tooling)
*   **Language:** TypeScript
*   **Styling:** Tailwind CSS
*   **State Management:** Zustand
*   **Routing:** React Router
*   **Logging:** Custom `Logger` class (as per `logging_guidelines.md`)

### 2.2. Backend (packages/api)

*   **Framework:** Hono
*   **Language:** TypeScript
*   **Runtime:** Node.js (managed via Bun)
*   **Logging:** Pino (as per `logging_guidelines.md`)
*   **Authentication:** JWT-based (details in `security_guidelines.md`)

### 2.3. Database (packages/db)

*   **Database System:** PostgreSQL
*   **ORM:** Drizzle ORM
*   **Migration Management:** Drizzle Kit

### 2.5. Build, Test & Development Tools

*   **Package Manager & Runtime:** Bun
*   **Version Control:** Git
*   **Linting & Formatting:** Biome
*   **Testing Frameworks:** Vitest
*   **API Documentation:** OpenAPI/Swagger

### 2.6. Shared Logic (packages/core)

*   **Language:** TypeScript
*   **Purpose:** Shared types, utility functions, constants, and core business logic used across `api` and `web` packages.

## 3. Rationale for Standardization

Standardizing our technology stack offers several key benefits:

*   **Consistency:** Uniform tools and patterns across the codebase make it easier to understand, maintain, and extend.
*   **Collaboration:** Team members can work more effectively together, sharing knowledge and skills. AI tools can also be more effectively guided.
*   **Efficiency:** Reduces cognitive load and speeds up development by leveraging a common set of well-understood technologies.
*   **Onboarding:** New developers can get up to speed more quickly.
*   **Tooling & Automation:** Enables consistent setup for build pipelines, testing, linting, and AI-assisted development workflows.
*   **Security & Performance:** Allows focused effort on securing and optimizing a known set of technologies.

## 4. Adherence and Proposing Changes

*   **Strict Adherence:** All new development **MUST** use the technologies specified in this document. Avoid introducing new libraries or frameworks for existing functionalities without approval.
*   **Proposing Changes:**
    1.  If a new technology or a significant version upgrade is deemed necessary or highly beneficial, a proposal **MUST** be submitted.
    2.  The proposal should include:
        *   The problem the new technology solves or the benefit it provides over the current stack.
        *   An analysis of its impact (learning curve, integration effort, security, performance, licensing).
        *   Alternatives considered.
    3.  Proposals will be reviewed by the lead development team/architect.
    4.  Approved changes will result in an update to this document.

## 5. Quick Reference: Key Technologies

*   **Frontend:** React, TypeScript, Vite, Tailwind CSS
*   **Backend:** Hono, TypeScript, Node.js (Bun), Pino
*   **Database:** PostgreSQL, Drizzle ORM
*   **Build/Dev:** Bun, Git, Biome

This document will be reviewed periodically and updated as the project evolves.
