---
description: Guide for setting up and extending the API application (Hono, Node.js).
---

This workflow outlines common tasks for setting up and extending the `packages/api` application after initial project scaffolding.

**Key Areas for Setup & Development:**

0.  **Ensure API Package Directory Structure**
    - This workflow assumes the root `packages/api/` directory has been created (typically by `/05-generate-project-scaffold.md`).
    - Before proceeding, ensure the core internal directory structure for the API package exists. Create the following directories if they are missing, adhering to `project_structure.md`:
        - `packages/api/src/`
        - `packages/api/src/routes/`
        - `packages/api/src/middleware/`
        - `packages/api/src/services/`
        - `packages/api/src/utils/`
        - `packages/api/src/types/`
        - `packages/api/tests/`
    - Also, ensure the main entry point `packages/api/src/index.ts` and `packages/api/package.json` are created if they don't exist. Minimal content for `package.json` should define the package name (e.g., `@homing/api-service`) and core dependencies like `hono`, `pino`. `index.ts` can be a minimal Hono app setup initially.

1.  **Hono App Initialization (`packages/api/src/index.ts`):
    *   Set up the main Hono application instance.
    *   Integrate essential global middleware (e.g., `correlationIdMiddleware`, `requestLoggerMiddleware`, CORS handling, error handling).
    *   Refer to `logging_guidelines.md` for logger setup (Pino) and request logging.
    *   Refer to `security_guidelines.md` for security best practices.

2.  **Route Definitions (`packages/api/src/routes/`):
    *   Organize routes by domain/feature (e.g., `packages/api/src/routes/auth/`, `packages/api/src/routes/users/`).
    *   Each domain should have its own Hono router instance, which is then mounted onto the main app.
    *   Implement route handlers that call services for business logic.
    *   Use Zod schemas (from `packages/api/src/types/`) for request validation (body, query params, path params).

3.  **Middleware (`packages/api/src/middleware/`):
    *   Create custom middleware for concerns like authentication, authorization (RBAC), specific input validation, etc.
    *   `correlation-id.ts`: Ensures every request has a unique ID for tracing.
    *   `request-logger.ts`: Logs request and response details.
    *   `auth-middleware.ts`: Verifies JWTs and attaches user context to requests.

4.  **Services (`packages/api/src/services/`):
    *   Implement business logic within service classes or functions.
    *   Services interact with the database (via `packages/db`) and perform core operations.
    *   Keep services focused on specific domains.

5.  **Types and Schemas (`packages/api/src/types/`):
    *   Define API-specific types (request payloads, response DTOs) and Zod schemas for validation.
    *   Import core domain types from `@homing-io/core/types`.

6.  **Database Integration:
    *   Access Drizzle ORM and schema from `packages/db` to perform database operations within services.
    *   Ensure database connection management is handled correctly (e.g., using a connection pool if not managed by Drizzle/Postgres.js directly for serverless functions).

7.  **Environment Variables:
    *   Use environment variables for configuration (database connection strings, JWT secrets, API keys, log levels).
    *   Load environment variables (e.g., using `dotenv` for local development ).
    *   Refer to `.env.example` for required variables.
    *   copy .env.example to a new .env file

8.  **Error Handling:
    *   Implement a global error handler middleware to catch unhandled exceptions and return consistent JSON error responses.
    *   Define custom error classes if needed for specific error types (e.g., `NotFoundError`, `ValidationError`, `UnauthorizedError`).

9.  **Testing (`packages/api/tests/`):
    *   Write unit tests for services and middleware.
    *   Write integration tests for API routes (e.g., using `hono/testing` or Supertest).

10. **Type Checking and Linting:**
    *   Regularly run `bun run typecheck` and `bun run lint` (or use the `/format-lint-fix` workflow) within `packages/api` or from the root.

**Example Initial Setup Steps:**

*   **Basic Hono App:** In `src/index.ts`, initialize Hono, add correlation ID and logger middleware.
*   **Health Check Route:** Create a simple `/health` endpoint in `src/routes/health.routes.ts`.
*   **Auth Routes:** Implement basic authentication routes (`/auth/login`, `/auth/register`) using Zod schemas for validation and JWTs for token generation.

This workflow is a guide. The specific order and tasks will depend on the feature being implemented.

11. **Building for Production:**
    *   The `package.json` in `packages/api` is configured to use `bun build` for creating a production-ready build, as confirmed in its `scripts` section.
    *   The command is `bun run build`.
    *   This command typically compiles the TypeScript source (e.g., `src/index.ts`) into an output directory (e.g., `./dist`) targeting the Bun runtime.

12. **Running the Application:**
    *   To start the API development server, navigate to the `packages/api` directory and run the appropriate command.
    *   Typically, this command is `bun run dev`.
    *   // turbo
    *   `cd packages/api && bun run dev`
    *   Ensure the application starts successfully and is accessible (e.g., `http://localhost:3000` or as configured).