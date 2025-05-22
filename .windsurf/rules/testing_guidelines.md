---
trigger: glob
description: Defines testing guidelines and best practices for the application
globs: **/*.{test,spec}.{ts,tsx,js,jsx}
---

# Testing Guidelines

This document outlines testing guidelines to ensure consistent and reliable testing. For AI-assisted test generation, see `.windsurf/workflows/ai-generate-tests.md`.

## 1. General Principles

*   **Co-location:** Test files (`[filename].test.ts(x)`) alongside source files.
*   **Coverage:** Aim for high coverage of critical paths, success/failure scenarios, and edge cases. Focus on behavior, not implementation.
*   **Independence:** Tests must be isolated. Reset state between tests. Mock external dependencies.
*   **Readability:** Use descriptive names (Arrange-Act-Assert pattern). Keep tests simple, focused on one behavior.

## 2. Unit Testing
    ```typescript
*   **Frontend Components (React Testing Library):** Test rendering, props, state, user interactions, lifecycle.
*   **Backend Functions/Services:** Test inputs/outputs, edge cases, error conditions. Mock dependencies.
*   **Structure:**
    ```typescript
    describe('ComponentName/FunctionName', () => {
      describe('when [condition/scenario]', () => {
        it('should [expected behavior]', () => {
          // Arrange
          // Act
          // Assert
        });
      });
    });
    ```
          // Assert
## 3. Integration Testing
## 3. Integration Testing
*   **API Endpoints:** Test end-to-end, request validation, response format/codes, error handling. Mock external services.
*   **Service Interactions:** Test interactions between services, database operations (use test containers or in-memory DBs if suitable), external service integrations.
*   **Frontend Compositions:** Test interactions between multiple components, page rendering, form submissions, routing.
*   **API Endpoints:** Test end-to-end, request validation, response format/codes, error handling. Mock external services.
## 4. End-to-End (E2E) Testing
*   **Implementation:** Use E2E tools (e.g., Playwright, Cypress), stable selectors, handle async operations, ensure proper cleanup.
*   **Scenarios:** Test critical user flows (auth, core features).
*   **Implementation:** Use E2E tools (e.g., Playwright, Cypress), stable selectors, handle async operations, ensure proper cleanup.

## 5. Test-Driven Development (TDD)

*   **Workflow:** Red (write failing test) -> Green (minimal code to pass) -> Refactor.
*   **Best Practices:** Start simple, incrementally add complexity, refactor tests with code.
*   **Database:** Use test-specific databases (in-memory or containerized), reset state, use transactions for isolation.
## 6. Mocking

*   **Implementation:** Mock external dependencies. Use realistic mock data (factories can help). Reset mocks between tests.
*   **Best Practices:** Mock at the appropriate level. Avoid excessive mocking. Verify mock interactions if crucial.
## 11. AI-Assisted Testing Enhancement
## 7. Testing Tools
    *   **Benefit:** Comprehensive scenario brainstorming.
*   **Test Runner:** Bun Test (primary).
*   **Component Testing:** React Testing Library (focus on user interactions, accessible selectors).
*   **API Mocking:** Mock Service Worker (MSW) for frontend API mocking.
    *   **Prompt:** "Generate Vitest boilerplate for a React component [Z] / Playwright E2E test for page [A]."
## 8. Test Data Management
    *   **Prompt:** "Failing test [code], component [code], error [msg]. Suggest causes."
*   **Creation:** Use factories/builders for realistic, non-hardcoded test data.
*   **Database:** Use test-specific databases (in-memory or containerized), reset state, use transactions for isolation.