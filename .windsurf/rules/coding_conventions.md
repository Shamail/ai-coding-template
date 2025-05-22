---
trigger: glob
description: Defines core coding conventions for TypeScript and JavaScript
globs: **/*.{ts,tsx,js,jsx}
---

# Coding Conventions

## TypeScript Standards

### General TypeScript Rules
1.  **Strict Config:** Use `"strict": true`; avoid `any`; explicit return types; use utility types.
2.  **Type Definitions:** Shared types in dedicated files; local types co-located. Interfaces for object shapes, types for unions/intersections. Descriptive names. Export shared types from core.
3.  **Nullability:** Prefer `undefined` over `null`. Use `?.` and `??`. Avoid `!`.

### Object-Oriented Programming (OOP)
1.  **Class Structure:** Classes for stateful items. Prefer composition over inheritance. Enforce encapsulation. Small, single-responsibility classes.
2.  **Method Organization:** Group by functionality. Public before private. Short, focused methods.

### Functional Programming (FP)
1.  **Pure Functions:** Prefer pure, side-effect-free functions. Immutable data. Use `map`, `filter`, `reduce`.
2.  **Function Composition:** Compose for complex ops. Higher-order functions for reuse. Arrow functions for inline ops.

## Code Style

1.  **Formatting:** 2-space indent; 100-char line limit; semicolons; single quotes; template literals.
2.  **Naming:** `camelCase` for vars/funcs; `PascalCase` for classes/interfaces/types/React components; `UPPER_SNAKE_CASE` for constants. Descriptive names. Boolean prefixes: `is`, `has`, `should`. Private members: `_`.
3.  **Comments/Docs:** JSDoc for public APIs/complex funcs. Comment "why", not "what". Update comments with code. `TODO` for temp solutions.

## Error Handling

1.  **Error Patterns:** `try/catch` for error-prone code. Custom error classes. Meaningful messages. Log appropriately.
2.  **Async Errors:** `async/await` with error handling. Avoid nested promises/callbacks. `Promise.all` for parallel ops.

## Import/Export

1.  **Module Org:** Named exports for multiple items. Default export for main item/file. Group imports: external, then internal. Avoid circular dependencies.

## Performance Considerations

1.  **Optimization:** Avoid premature optimization. Memoize expensive computations. Mind array op performance on large data. Use appropriate data structures.

## Security Practices

1.  **Input Validation:** Always validate user input. Parameterized DB queries. Never trust client data.
2.  **Output Encoding:** Encode output (prevent XSS). Use Content Security Policies.

## Accessibility

1.  **A11y Reqs:** Accessible UI. Semantic HTML. Image `alt` text. Keyboard nav. Color contrast.

## AI-Assisted Convention Adherence

AI tools aid convention adherence. See `prompt_engineering_guidelines.md`.

### 10.1. Convention Checking & Explanation
*   **AI Action:** Query AI on code adherence or rule explanations.
*   **AI Prompt Hint:** E.g., check naming conventions (Sec 2.2), explain composition (Sec 1.3.1).
*   **Benefit:** Fast deviation ID & rule clarification.

### 10.2. Boilerplate Generation
*   **AI Action:** Ask AI for boilerplate (funcs, classes) per conventions.
*   **AI Prompt Hint:** E.g., class structure per OOP rules (Sec 1.3).
*   **Benefit:** Convention-aligned starting code.

### 10.3. Code Style Review
*   **AI Action:** Submit code for AI style review (Sec 2).
*   **AI Prompt Hint:** E.g., review component style (formatting, naming).
*   **Benefit:** Initial style feedback.

### 10.4. Refactoring Alignment
*   **AI Action:** Ask AI for refactoring suggestions for conventions.
*   **AI Prompt Hint:** E.g., refactor func for FP guidelines (Sec 1.4).
*   **Benefit:** Modernize/align inconsistent code.

### 10.5. Documentation Assistance (JSDoc)
*   **AI Action:** Ask AI for JSDoc from code.
*   **AI Prompt Hint:** E.g., JSDoc for func (params, return) (Sec 2.3).
*   **Benefit:** Speeds up JSDoc, ensures consistency.