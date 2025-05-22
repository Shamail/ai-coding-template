---
description: AI-Driven Project Estimation
---

# AI-Driven Project Estimation Workflow

## Overview
This workflow leverages AI to assist in analyzing tasks, estimating complexity, and providing data-informed suggestions for effort estimation. Human expertise remains crucial for final adjustments and commitments.

## Prerequisites
- Well-defined user stories or tasks (e.g., from `/04-generate-user-stories` workflow) with clear descriptions, acceptance criteria, and technical notes.
- Access to approved AI assistant tools.
- Familiarity with `prompt_engineering_guidelines.md`.

## Steps

1.  **Gather Data for AI:**
    *   Compile all relevant information for each user story/task: text, acceptance criteria, technical notes, dependencies, UI/UX mockups.
    *   (Optional) Gather historical data from similar completed tasks for context.

2.  **AI Complexity Analysis:**
    *   Use AI to perform a qualitative complexity analysis (e.g., Very Low to Very High) with justification.
    *   Prompt AI to identify key factors contributing to complexity.

3.  **AI Effort Estimation (Time/Story Points):**
    *   Prompt AI for a rough effort estimate (e.g., ideal developer-days, story points) based on complexity.
    *   AI can also break down stories into sub-tasks with rough estimates.
    *   Treat AI estimates as suggestions; specify developer skill level for time-based estimates; use ranges.

4.  **Human Review and Adjustment:**
    *   Development team reviews AI's complexity analysis and effort estimates.
    *   Critically evaluate AI's justification.
    *   Factor in human elements: team knowledge, experience, risks, dependencies.
    *   Adjust AI suggestions and reach consensus on the final estimate (e.g., using Planning Poker).

5.  **Document Estimates and Assumptions:**
    *   Record the final estimate, initial AI suggestion (for reference), and key assumptions made.

## Output
- Documented project/task estimates that combine AI insights with team expertise.
- Clear record of assumptions made during estimation.
- A basis for comparing estimates to actuals for future learning and refinement of the estimation process.
