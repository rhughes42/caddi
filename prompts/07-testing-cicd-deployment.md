# Prompt 7: Testing, CI/CD, and Deployment

## Objective

Add a comprehensive testing setup, continuous integration pipeline, and deploy the application to Firebase Hosting.

## Tasks

### 1. Set up Vitest for unit testing

- Install `vitest`, `@vue/test-utils`, `jsdom`, and `@pinia/testing`.
- Create a `vitest.config.ts` file.
- Add a `"test"` script to `package.json`.
- Write unit tests for:
  - Auth store (mock Firebase Auth).
  - Projects store (mock Firestore).
  - Tasks store (mock Firestore).
  - At least one component (e.g., `TaskForm.vue` renders correctly, validates inputs).

### 2. Set up Cypress or Playwright for E2E testing

- Install Cypress (or Playwright) for end-to-end testing.
- Add an `"e2e"` script to `package.json`.
- Write E2E tests for:
  - Landing page renders correctly.
  - User can sign up and reach the dashboard.
  - User can create a project and add a task.

### 3. Configure GitHub Actions CI

- Create `.github/workflows/ci.yml` that runs on push and pull requests:
  - Install dependencies.
  - Run the linter (`npm run lint`).
  - Run type checking (`npx vue-tsc --noEmit`).
  - Run unit tests (`npm run test`).
  - Build the project (`npm run build`).

### 4. Set up Firebase Hosting

- Install `firebase-tools` as a dev dependency.
- Run `firebase init hosting` to generate `firebase.json` and `.firebaserc`.
- Configure rewrites so all routes serve `index.html` (SPA mode).
- Add a `"deploy"` script to `package.json`: `npm run build && firebase deploy --only hosting`.

### 5. Add a deployment GitHub Actions workflow

- Create `.github/workflows/deploy.yml` that triggers on pushes to `main`:
  - Builds the project.
  - Deploys to Firebase Hosting using a service account token (stored as a GitHub secret).

### 6. Add a pre-commit hook (optional but recommended)

- Install `husky` and `lint-staged`.
- Configure a pre-commit hook that runs the linter and formatter on staged files.
