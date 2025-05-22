---
description: Guide for setting up and extending the web application (React, Vite, Tailwind).
---

This workflow outlines common tasks for setting up and extending the `packages/web` application after initial project scaffolding.

**Key Areas for Setup & Development:**

0.  **Ensure Web Package Directory Structure**
    - This workflow assumes the root `packages/web/` directory has been created (typically by `/05-generate-project-scaffold.md`).
    - Before proceeding, ensure the core internal directory structure for the Web package exists. Create the following directories if they are missing, adhering to `project_structure.md`:
        - `packages/web/src/`
        - `packages/web/src/components/`
        - `packages/web/src/components/ui/`
        - `packages/web/src/pages/`
        - `packages/web/src/routes/`
        - `packages/web/src/hooks/`
        - `packages/web/src/utils/`
        - `packages/web/src/assets/`
        - `packages/web/src/styles/`
        - `packages/web/src/types/`
        - `packages/web/tests/`
    - Also, ensure essential entry files like `packages/web/src/main.tsx`, `packages/web/src/app.tsx`, and `packages/web/package.json` are created if they don't exist. `package.json` should define the package name (e.g., `@homing/web-app`) and dependencies like `react`, `react-dom`, `vite`, `tailwindcss`, `react-router-dom`. `main.tsx` and `app.tsx` can have minimal React setup initially.

1.  **Routing (`packages/web/src/routes/`):
    *   Define application routes using React Router (`react-router-dom`).
    *   Create route configuration files (e.g., `index.tsx` or `app-routes.tsx` in `src/routes/`).
    *   Implement public routes, protected routes (requiring authentication), and potentially role-based routes.
    *   Consider lazy loading for page components to improve initial load time.
    *   Set up a "Not Found" (404) page.

2.  **Layout Components (`packages/web/src/components/`):
    *   Establish a main layout component (e.g., `layout.tsx`) that includes common UI elements like a header, footer, and navigation.
    *   Ensure the layout adapts responsively to different screen sizes.

3.  **Core UI Components (`packages/web/src/components/ui/`):
    *   Develop or integrate reusable UI components (buttons, forms, modals, etc.). This project uses `shadcn/ui` conventions, so components would typically be added via its CLI or manually created following its patterns.
    *   Ensure components are well-styled with Tailwind CSS and are accessible.

4.  **Pages (`packages/web/src/pages/`):
    *   Create components for each page defined in your routes.
    *   Organize pages logically, perhaps in subdirectories for different features or sections of the app.

5.  **State Management (`packages/web/src/stores/` or using Zustand hooks):
    *   Set up Zustand stores for global state (e.g., authentication, user profile, theme).
    *   Define actions and selectors for interacting with the stores.

6.  **API Service Integration (`packages/web/src/services/` or `packages/web/src/hooks/`):
    *   Create functions or custom hooks to fetch data from the backend API.
    *   Handle API request/response states (loading, success, error).
    *   Use types from `@homing-io/core/types` and `packages/web/src/types/` for data consistency.

7.  **Styling (`packages/web/src/styles/`):
    *   Configure Tailwind CSS (`tailwind.config.js`, `postcss.config.js`).
    *   Define global styles or Tailwind base layers in `index.css` or `app.css`.
    *   Add any custom CSS or utility classes as needed.

8.  **Assets (`packages/web/src/assets/`):
    *   Place static assets like images, fonts, and icons in this directory.

9.  **Environment Variables:
    *   Use Vite's environment variable handling (e.g., `.env` files with `VITE_` prefix) for configuration like API base URLs.
    *   Ensure sensitive keys are not committed to the repository.

10. **Type Checking and Linting:**
    *   Regularly run `bun run typecheck` and `bun run lint` (or use the `/format-lint-fix` workflow) within `packages/web` or from the root to maintain code quality.

**Example Initial Setup Steps:**

*   **Define basic routes:** Create `home-page.tsx`, `login-page.tsx`, `not-found-page.tsx`.
*   **Set up React Router:** Configure routes in `app.tsx` or a dedicated routing file.
*   **Create `Layout` component:** Add `header.tsx` and `app-footer.tsx` (or a similarly named footer component) to `packages/web/src/components/` and integrate them into a `layout.tsx`.
*   **Basic Styling:** Ensure Tailwind is correctly configured and apply basic styles to `index.html` and `main.tsx`.

This workflow is a guide. The specific order and tasks will depend on the feature being implemented.

11. **Running the Application:**
    *   To start the web application development server, navigate to the `packages/web` directory and run the appropriate command.
    *   Typically, this command is `bun run dev` (as Vite is used).
    *   // turbo
    *   `cd packages/web bun run dev`
    *   Ensure the application starts successfully and is accessible in your browser (e.g., `http://localhost:5173` or as configured by Vite).