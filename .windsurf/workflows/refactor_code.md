---
description: AI-Assisted Code Refactoring & Optimization
---

# AI-Assisted Code Refactoring and Optimization Workflow

## Overview
This workflow details using AI to identify refactoring opportunities, suggest optimizations (performance, readability, maintainability), and assist in applying changes. It emphasizes human oversight and testing to ensure correctness.

**Note:** This is a foundational workflow. Advanced refactoring patterns and specific AI techniques will be expanded in future updates.

## Prerequisites
- Codebase or specific code sections identified for refactoring.
- Clear objectives for refactoring (e.g., improve performance by X%, reduce complexity, adhere to new coding standards).
- Existing tests (ideally comprehensive) to verify behavior post-refactoring (see `/ai-generate-tests.md`).
- Access to approved AI coding assistant tools.
- Familiarity with `prompt_engineering_guidelines.md` and project `coding_conventions.md`.

## Steps

1.  **Identify Refactoring Candidates & Goals:**
    *   Pinpoint code sections needing improvement (e.g., complex functions, duplicated logic, performance bottlenecks).
    *   Define clear, measurable goals for the refactoring effort.

2.  **AI-Assisted Analysis & Suggestion:**
    *   Provide AI with the target code and refactoring goals.
    *   **Prompt Examples:**
        *   "Analyze this code for potential refactorings to improve readability and maintainability: [code snippet]. Suggest specific changes."
        *   "Identify performance bottlenecks in this function: [code snippet]. How can it be optimized?"
        *   "Refactor this legacy JavaScript code to modern ES6+ syntax and patterns: [code snippet]."
        *   "Does this code adhere to SOLID principles? If not, suggest refactorings."
    *   AI can help identify code smells, anti-patterns, or suggest alternative implementations.

3.  **Evaluate AI Suggestions:**
    *   Critically review AI's proposed changes. Consider:
        *   Impact on readability, maintainability, performance.
        *   Potential risks or introduction of new bugs.
        *   Alignment with overall architecture and project standards.
    *   Not all AI suggestions will be optimal or appropriate.

4.  **Implement Refactoring (Iteratively):**
    *   Apply chosen refactorings in small, manageable steps.
    *   AI can assist in generating the refactored code, but human developers MUST carefully review and integrate it.
    *   **Example:** "Apply the suggested refactoring to extract this logic into a separate function: [details]."

5.  **Test Thoroughly:**
    *   After each incremental refactoring, run all relevant tests (unit, integration) to ensure no existing functionality is broken.
    *   If tests are lacking, use `/ai-generate-tests.md` to create them *before* major refactoring.
    *   Perform manual testing for critical paths if necessary.

6.  **Review and Commit:**
    *   Review the refactored code (ideally by another team member, potentially with AI assistance as per `/ai_assisted_code_review_workflow.md`).
    *   Commit changes with clear messages explaining the refactoring.

## Output
- Refactored code that meets the defined goals (e.g., improved performance, better readability).
- Updated test suite confirming the behavior of refactored code.
- Potentially, a safer, more maintainable, and efficient codebase.
