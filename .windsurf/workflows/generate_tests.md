---
description: AI-Assisted Test Generation
---

# AI-Assisted Test Generation Workflow

## Overview
This workflow guides users on leveraging AI assistants to generate initial boilerplate and test cases for unit, integration, and End-to-End (E2E) tests. The aim is to accelerate test creation and improve coverage, allowing developers to focus on refining test logic and complex scenarios.

## Prerequisites
- Code for the function, component, module, or user story to be tested is available.
- Project's testing framework (e.g., Vitest) and conventions are established (refer to `testing_guidelines.md`).
- Access to approved AI coding assistant tools.
- Familiarity with `prompt_engineering_guidelines.md`.

## Steps

1.  **Identify Test Scope and Type:**
    *   Determine what needs testing and the appropriate test type:
        *   **Unit Tests:** For isolated functions, methods, or components.
        *   **Integration Tests:** For interactions between components, services, or modules.
        *   **E2E Tests:** For complete user flows through the application UI.

2.  **Prepare Context for AI:**
    *   Gather necessary information for the AI based on test type:
        *   **Unit Tests:** The specific code snippet/function.
        *   **Integration Tests:** Code for interacting components, expected interaction patterns, API contracts.
        *   **E2E Tests:** User story, acceptance criteria, UI flow description.
    *   Include relevant parts of `testing_guidelines.md` or project-specific test patterns.

3.  **Prompt AI for Test Cases and Boilerplate:**
    *   Use AI to generate test ideas and initial test code.
    *   **Unit Test Prompt Example:** "Generate Vitest unit tests for this TypeScript function: [code snippet]. Include tests for [happy path, edge cases, error handling]."
    *   **Integration Test Prompt Example:** "Draft Vitest integration tests for Service A calling Service B's endpoint `[endpoint]` with `[payload]`. Service A code: [snippet A], Service B relevant code: [snippet B]. Mock external dependencies."
    *   **E2E Test Prompt Example:** "Outline Playwright/Cypress E2E test cases for this user story: '[User Story]'. Acceptance Criteria: [ACs]. Then, generate boilerplate for the main success scenario."

4.  **Review and Refine AI-Generated Tests:**
    *   **Critically Review:** Do not assume AI output is perfect.
    *   **Correctness & Completeness:** Verify test logic, assertions, and coverage of important scenarios (including edge cases AI might miss).
    *   **Adherence to Standards:** Ensure tests meet project guidelines, naming conventions, and patterns.
    *   **Mocks & Stubs:** Validate correct implementation and usage of mocks.
    *   **Selectors (E2E):** Replace placeholder UI selectors with robust, actual ones.
    *   **Augment Logic:** Implement complex assertions or setup/teardown logic that AI couldn't fully generate.

5.  **Integrate and Run Tests:**
    *   Add the refined tests to the appropriate test files (co-located as per `project_structure.md`).
    *   Run tests locally to ensure they pass and behave as expected.
    *   Commit tests and ensure they run successfully in the CI pipeline. Debug any failures.

## Output
- Generated test files (e.g., `[filename].test.ts`) added to the project.
- Increased test coverage for the targeted code or features.
- A suite of AI-assisted, human-verified tests that contribute to quality assurance.