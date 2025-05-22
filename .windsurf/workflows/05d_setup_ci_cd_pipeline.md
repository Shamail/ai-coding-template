---
description: Setup CI/CD Pipeline (GitHub Actions)
---

# CI/CD Pipeline Setup (GitHub Actions)

## Overview
This workflow guides setting up a basic CI/CD pipeline using GitHub Actions for automated build, test, and optionally, AI-assisted failure summaries and deployment.

## Prerequisites
- Project hosted on GitHub.
- Familiarity with Git, GitHub (branches, PRs), and YAML.
- Bun installed locally (optional, as the pipeline installs it).
- (Optional) AI API key and/or Deployment service tokens, stored as GitHub Secrets.

## Steps

1.  **Create Workflow File:**
    *   Ensure the directory `.github/workflows/` exists at your project root.
        ```bash
        mkdir -p .github/workflows
        ```
    *   Create `main-ci.yml` (or a similar name) in this directory.

2.  **Define Basic CI Workflow (`main-ci.yml`):**
    *   Populate `main-ci.yml`. This example triggers on pushes and PRs to the `main` branch.
    ```yaml
    name: Main CI Pipeline

    on:
      push:
        branches: [ main ]
      pull_request:
        branches: [ main ]

    jobs:
      build_and_test:
        name: Build & Test
        runs-on: ubuntu-latest
        steps:
          - name: Checkout code
            uses: actions/checkout@v4

          - name: Setup Bun
            uses: oven-sh/setup-bun@v1
            with:
              bun-version: latest # Or pin to project's Bun version

          - name: Install dependencies
            run: bun install --frozen-lockfile

          - name: Lint and Format Check
            run: bun run format:check && bun run lint:check

          - name: Build all packages
            run: bun run build

          - name: Run all tests
            run: bun run test
    ```
    *   **Note:** Ensure your root `package.json` has `format:check`, `lint:check`, `build`, and `test` scripts. Adapt commands for your project/monorepo structure (e.g., using `bun --filter=...`).

3.  **(Optional) AI-Assisted Build Failure Summary:**
    *   Add this step to the end of the `build_and_test` job in `main-ci.yml`:
    ```yaml
          - name: Summarize Failure (AI Assisted)
            if: failure()
            env:
              AI_API_KEY: ${{ secrets.YOUR_AI_API_KEY_SECRET_NAME }}
            run: |
              echo "Build/tests failed. AI summary (implement script):"
              # ./scripts/summarize_failure.sh (collects logs, calls AI API)
              echo "AI Summary script not yet implemented."
    ```
    *   **Note:** You'll need to create the referenced script (e.g., `summarize_failure.sh`) and store your AI API key in GitHub Secrets.

4.  **(Optional) Add Deployment Step (Conceptual Example - Netlify):**
    *   Add a new job to `main-ci.yml` after `build_and_test`:
    ```yaml
    deploy_production:
      name: Deploy to Production
      if: github.ref == 'refs/heads/main' && github.event_name == 'push'
      needs: build_and_test
      runs-on: ubuntu-latest
      steps:
        - uses: actions/checkout@v4
        - uses: oven-sh/setup-bun@v1 # Setup Bun again for this job
          with: { bun-version: latest }
        # Install & Build specific package if needed, e.g., web
        - working-directory: ./packages/web # Adjust path
          run: bun install --frozen-lockfile && bun run build
        - name: Deploy to Netlify
          uses: netlify/actions/cli@master
          with:
            args: deploy --dir=packages/web/dist --prod # Adjust dir
          env:
            NETLIFY_AUTH_TOKEN: ${{ secrets.NETLIFY_AUTH_TOKEN }}
            NETLIFY_SITE_ID: ${{ secrets.NETLIFY_SITE_ID }}
    ```
    *   **Note:** Adapt for your deployment service (Vercel, AWS, etc.). Store necessary tokens/IDs in GitHub Secrets. Adjust `working-directory` and build commands if deploying a specific package from a monorepo.

5.  **Customize, Commit, and Iterate:**
    *   Tailor build, test, and deployment commands in `main-ci.yml` to your project.
    *   Consider GitHub Actions caching (`actions/cache`) for dependencies to speed up runs.
    *   Commit `main-ci.yml`, push/PR, and monitor in GitHub's "Actions" tab. Refine as needed.

6.  **Security Considerations:**
    *   Always store sensitive data (API keys, tokens) as encrypted GitHub Secrets.
    *   Review workflow permissions (`permissions` key in `main-ci.yml`) if needing to restrict default token access.

## Output
- A `main-ci.yml` file in `.github/workflows/`.
- Automated CI runs (build, lint, test) on `main` branch activity.
- Optional: AI-assisted failure summaries and automated deployments.
- An enhanced, more automated development lifecycle.
