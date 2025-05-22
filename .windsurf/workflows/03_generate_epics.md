---
description: Epic Generation
---

# Epic Generation Workflow

## Overview
This workflow breaks down your product plan into manageable epics, each representing a significant feature or functionality area.

## Prerequisites
- Completed product plan (docs/product/product_plan.md)
- Understanding of major product functionalities

## Steps

1. **Review Product Plan**
   - Analyze the product plan from the previous workflow
   - Identify the core functionalities that need to be implemented
   - Note any dependencies between different product areas

2. **Identify Major Feature Areas**
   - Group related functionalities into cohesive feature areas
   - Ensure each feature area represents a significant part of the product
   - Consider both user-facing and system-level features

3. **Generate Epics**
   - Use Windsurf AI to create epics for each major feature area
   - For each epic, define:
     - Title: Clear, concise name
     - Description: Overview of what the epic encompasses
     - Goals: What this epic aims to achieve
     - Scope: Boundaries of what is included/excluded
     - Dependencies: Relationships with other epics
     - Priority: Relative importance in the development sequence

4. **Review and Refine**
   - Evaluate the generated epics
   - Ensure they collectively cover all product functionalities
   - Adjust scope and boundaries to create well-sized epics

5. **Create Output Directories**
   - Ensure the output directory `docs/product/epics/` exists. If not, create it.
   - Command: `mkdir -p docs/product/epics`

6. **Document Epics**
   - Save each epic as a separate markdown document
   - Store at docs/product/epics/eX-[epic-name].md (where X is the epic number, e.g., e1-user-management.md)
   - Create an index file listing all epics at docs/product/epics.md

## Output
A collection of well-defined epics (docs/product/epics/) that will serve as the basis for user story generation in the next workflow.
