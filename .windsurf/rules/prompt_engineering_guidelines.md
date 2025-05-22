---
description: Guidelines for crafting effective prompts for AI code generation, explanation, and analysis.
---

# Prompt Engineering Guidelines

## 1. Introduction
Effective prompts are key to maximizing AI benefits in development, leading to accurate, relevant AI responses, saving time, and improving code quality.

## 2. Core Principles
- **Clarity:** Be specific, unambiguous.
- **Context:** Provide relevant code, project goals, constraints, patterns.
- **Constraints:** Define limitations (language features, performance, style).
- **Desired Output Format:** Specify format (code block, list, JSON).
- **Conciseness:** Provide context but avoid irrelevant info.

## 3. Persona-Based Prompting
Instruct AI to adopt a persona for better output.
- **Example:** "Act as a senior security engineer. Review this Hono middleware for vulnerabilities."
- **Example:** "You are a QA engineer. Generate test cases for this user story: [Details]."

## 4. Task-Specific Prompt Templates

### 4.1. Generating New Code
- **Structure:**
  ```
  Generate a [lang/framework] [item] named '[Name]' that:
  1. [Step 1]
  ...
  Constraints: [Constraint 1 (e.g., pure function)], [Constraint 2 (e.g., SOLID)]
  Input(s): [Describe inputs/types]
  Output: [Describe output/type]
  Example Usage (optional): [Example]
  ```
- **Example:** "Generate TypeScript function `calculateDiscount(price: number, discountPercent: number): number` for `packages/core/src/utils/`. Returns discounted price. `discountPercent` must be 0-100, else throw error."

### 4.2. Explaining Existing Code
- **Structure:**
  ```
  Explain this [lang/framework] code:
  [Code Snippet]
  Focus on: Purpose, logic flow, complex parts, side effects, improvements (optional).
  ```

### 4.3. Generating Test Cases
- **Structure:**
  ```
  Generate [unit/integration/E2E] tests for:
  [Code Snippet or User Story]
  Cover: Happy paths, edge cases, errors, performance, security.
  Format: [Testing framework, e.g., Vitest].
  ```

### 4.4. Refactoring Code
- **Structure:**
  ```
  Refactor this [lang/framework] code for [readability/performance/etc.]:
  [Code Snippet]
  Focus on: [Aspect 1], [Aspect 2].
  Provide refactored code & explanation. Maintain functionality.
  ```

### 4.5. Debugging Assistance
- **Structure:**
  ```
  Error in this [lang/framework] code:
  [Code Snippet]
  Error: [Message]
  Expected: [Behavior]
  Actual: [Behavior]
  To Reproduce: [Steps]
  Help identify cause & suggest fix.
  ```

### 4.6. Generating Documentation
- **Structure:**
  ```
  Generate [comments/JSDoc/Swagger/README section] for:
  [Code Snippet or API Endpoint]
  Include: Purpose, params/request, return/response, example.
  ```

## 5. Iterative Prompt Refinement
AI responses may need iteration.
- **Analyze Output:** Identify issues if response is unexpected.
- **Add Specificity:** If generic, add specific instructions/constraints.
- **Provide Examples (Few-Shot):** Show AI desired input/output format.
  - **Example:** "Translate Python to TypeScript. E.g., Py: `def add(a,b): return a+b` TS: `function add(a:number,b:number):number{return a+b;}` Now translate: [Your Py Code]"
- **Break Down Complex Tasks:** Split into smaller sub-prompts.

## 6. Specifying Constraints
Clearly state constraints.
- **Examples:** "Use only React functional components." "Time complexity O(n log n) or better." "Adhere to DRY." "PostgreSQL 15 compatible SQL." "Avoid external libraries if possible."

## 7. Handling Ambiguity & Requesting Clarification
Ask AI for clarification if response is unclear.
- **Example:** "Elaborate on why you chose that approach?"
- **Example:** "Explain [part of AI response] differently?"

## 8. Common Pitfalls & Avoidance
- **Overly Broad Prompts:** Generic responses. *Fix: Be specific.*
- **Insufficient Context:** AI can't guess. *Fix: Provide background/code.*
- **Implicit Assumptions:** AI doesn't know project conventions. *Fix: State explicitly.*
- **Ignoring AI Limitations:** AI errs. *Fix: Critically review AI content.*
- **Not Iterating:** Expecting perfection first time. *Fix: Refine prompts.*

Follow these guidelines to enhance AI interactions for efficient development and quality software.
