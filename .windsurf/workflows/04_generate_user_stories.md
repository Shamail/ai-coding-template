---
description: User Story Generation with Enhanced Detailing
---

# User Story Generation Workflow

## Overview
This workflow transforms epics into detailed user stories. It includes optional steps for interactive requirement elicitation to improve story quality and a review stage before finalization.

## Prerequisites
- Completed epics (`docs/product/epics/`)
- Understanding of user personas from the product plan

## Steps

1.  **Select and Review Epic**
    - USER selects an Epic to work on.
    - AI Assistant (Cascade) reviews the Epic's content, understanding its scope, goals, and target user personas.

2.  **Interactive Requirement Elicitation (Optional - Per Epic)**
    - Before generating stories for the selected Epic, the AI assistant will ask the USER:
      "For Epic '[Epic Name]', choose a story generation mode:
      A. **Standard Mode**: Generate stories with default detail.
      B. **Enhanced Mode**: Provide more input for detailed stories."
    - If USER chooses **Enhanced Mode (B)**:
        -   AI will ask: "Select Detail Level for this Epic's stories:
            1.  _Basic_: Core acceptance criteria.
            2.  _Moderate_: More ACs, common edge cases.
            3.  _High_: Extensive ACs, multiple scenarios, NFR hints."
            (USER provides choice 1, 2, or 3)
        -   AI will ask: "Optional: To guide Acceptance Criteria, do you have an image (UI sketch, wireframe)?
            - If yes, provide instructions for AI to access it (e.g., 'View file path/to/image.png', or paste text description of the image).
            - If no, type 'NONE'."
            (USER provides image instructions or 'NONE')

3.  **Identify Next User Story Focus**
    - Based on the Epic and previous stories (if any), AI proposes a focus for the next user story (e.g., "Next, let's detail the 'Admin Password Reset' feature.").
    - USER confirms or suggests an alternative focus for the current story.

4.  **Generate User Story Draft**
    - Based on the Epic, focus from Step 3, persona(s), and any inputs from Step 2, the AI assistant drafts one user story.
    - **Format Guide:**
        -   **Title:** Clear, concise (e.g., US00X: Admin Password Reset via Email)
        -   **User Persona:** (e.g., System Administrator, Owner/Manager)
        -   **Description:** "As a [persona], I want [feature/goal] so that [benefit/value]."
        -   **Acceptance Criteria:** MUST be a Markdown checklist. (e.g., `- [ ] User receives an email with a password reset link.`)
        -   **Priority:** (e.g., Must Have, Should Have, Could Have)
        -   **Epic Link:** Relative path to the parent epic markdown file.
        -   **Dependencies:** (Optional, e.g., US00Y)
    - AI uses the selected detail level and image (if any from Step 2) to tailor the story, especially the Acceptance Criteria.

5.  **Review and Approve Story Draft**
    - AI assistant presents the drafted user story to the USER.
    - USER reviews and responds with one of the following commands:
        -   `APPROVE`: The story is finalized. Proceed to Step 7.
        -   `MODIFY [your specific feedback/changes]`: AI revises based on feedback and presents the new draft (repeat Step 5).
        -   `DISCARD`: This story draft is abandoned. Return to Step 3 to focus on a new story or refine the current focus.

6.  **Create Output Directories (If Needed)**
    - This step is typically run once or checked before saving the first story for an epic.
    - Ensure `docs/product/user-stories/` exists.
    - Ensure `docs/product/user-stories/[epic-name-kebab-case]/` exists. Create if not.
    - Example: `mkdir -p docs/product/user-stories/[epic-name-kebab-case]/`

7.  **Document Approved User Story**
    - Save the *approved* user story to: `docs/product/user-stories/[epic-name-kebab-case]/[story-name-kebab-case].md`.
      (e.g., `docs/product/user-stories/01-user-management/US001-admin-registration.md`).
    - Update the main index file `docs/product/user-stories.md` to list and link to the new story under its epic.

8.  **Continue or Conclude**
    - AI asks: "Do you want to generate another story for Epic '[Epic Name]' or select a new Epic? (Another Story / New Epic / End)"
    - If "Another Story", return to Step 3.
    - If "New Epic", return to Step 1.
    - If "End", the workflow concludes.

## Output
A collection of well-defined, user-approved user stories in `docs/product/user-stories/`, organized by epic.