---
trigger: always_on
description: Guidelines for using, tracking, and improving workflows.
---

# Workflow Usage and Enhancement Guidelines

## 1. Workflow Execution

*   **Follow Instructions:** Adhere strictly to the steps outlined in each workflow markdown file (`.windsurf/workflows/`).
*   **Tool Usage:** Utilize the specified tools as described. Pay attention to `// turbo` and `// turbo-all` annotations for automated command execution.
*   **Parameter Provision:** Ensure all required parameters for workflow steps or tool calls are accurately provided.

### 1.1. Workflow Execution Tracking

*   **Purpose:** To maintain a record of executed workflows for visibility and auditing.
*   **File:** A checklist of completed workflows **MUST** be maintained in `docs/workflow-checklist.md`.
*   **Action upon Workflow Completion:**
    1.  After successfully completing all steps of a workflow defined in `.windsurf/workflows/`, you **MUST** update the `docs/workflow-checklist.md` file.
    2.  If `docs/workflow-checklist.md` does not exist, you **MUST** create it first using the `write_to_file` tool. If creating for the first time, include a title, e.g., `# Workflow Execution Checklist`, and ensure subsequent entries are appended as list items.
    3.  **Checklist Entry Format:** Each entry in the checklist **MUST** be a markdown list item and include:
        *   The full path to the workflow file (e.g., `/.windsurf/workflows/01-generate-business-plan.md`).
        *   The date and time of completion (ISO 8601 format, e.g., `YYYY-MM-DDTHH:MM:SSZ`).
        *   A status, typically `Completed`.
        *   (Optional) A brief note or reference to the USER request if relevant.
        *   **Example Entry:**
            ```markdown
            - `/.windsurf/workflows/01-generate-business-plan.md` - Completed on YYYY-MM-DDTHH:MM:SSZ - Initial business plan generation.
            ```
    4.  Use the `edit_file` tool (or `replace_file_content` by targeting the end of the file or a placeholder) to append new entries to `docs/workflow-checklist.md`. Ensure the file remains a valid markdown list. Do not overwrite existing entries unless correcting an error made in the current session.


## 2. Identifying Friction and Enhancements

During the execution of any workflow (`.windsurf/workflows/*.md`), if you encounter:

*   **Ambiguity:** Unclear instructions or steps.
*   **Missing Information:** Lack of necessary details to proceed confidently.
*   **Inefficiency:** Steps that are cumbersome, could be automated, or are prone to errors.
*   **Errors:** Tool errors, unexpected outputs, or failures in the workflow logic.
*   **User Input Issues:** Difficulties in interpreting user requests or mapping them to workflow inputs.
*   **Tool Limitations:** Situations where existing tools are insufficient or not ideal for a task within the workflow.
*   **Tool Limitations:** Situations where existing tools are insufficient or not ideal for a task within the workflow.
*   **Tool Limitations:** Situations where existing tools are insufficient or not ideal for a task within the workflow.
*   **Outdated Information:** Workflows referencing old practices, deprecated tools, or incorrect file paths.
*   **Unexpected Pre-existence:** Finding that a file, directory, or code implementation that the workflow intended to create already exists. This indicates potential redundancy in the workflow and should be logged as an enhancement opportunity to streamline the workflow.

You **MUST** document these observations.

## 3. Documenting Workflow Enhancements

*   **File:** All observations regarding workflow friction or potential enhancements **MUST** be logged in the `docs/workflow-enhancements.md` file.
*   **Format:** For each observation, create a new entry with:
    *   A clear title describing the issue or enhancement.
    *   The name of the workflow file (e.g., `/05a-setup-api-application.md`).
    *   A detailed description of the friction point or the proposed enhancement.
    *   Specific examples if applicable.
    *   Suggestions for improvement.
*   **Action:**
    1.  First, attempt to complete the current USER task to the best of your ability.
    2.  Then, **IMMEDIATELY AFTER** addressing the USER's primary request (or as soon as the friction is identified and understood), use the `edit_file` or `write_to_file` (if `docs/workflow-enhancements.md` doesn't exist) tool to add your observations to `docs/workflow-enhancements.md`.
    3.  If `docs/workflow-enhancements.md` exists, append new entries. Do not overwrite existing content unless you are correcting a previous entry you made in the current session.

## 4. Proposing Workflow Modifications

*   While `docs/workflow-enhancements.md` is the primary log for issues, if you identify a straightforward and safe improvement to a workflow file itself, you MAY propose this change directly to the USER or, if confident and the change is minor (e.g., fixing a typo, clarifying a command), make the edit to the workflow `.md` file.
*   Major changes to workflow logic should first be discussed or noted in `docs/workflow-enhancements.md`.

## 5. Creating New Workflows

*   When asked to create a new workflow, follow the standard format: YAML frontmatter (`description`) and markdown steps.
*   Store new workflows in `.windsurf/workflows/` with a descriptive kebab-case filename (e.g., `deploy-to-production.md`).
*   Ensure new workflows also adhere to these guidelines for future enhancements.

By consistently documenting areas for improvement, we can iteratively refine our workflows, making them more robust, efficient, and easier to use.