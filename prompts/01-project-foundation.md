# Prompt 1: Project Foundation — Routing, State Management, and Developer Tooling

## Objective

Establish the core project infrastructure: client-side routing, centralized state management, code quality tooling, and a basic page layout system. This sets the foundation every subsequent prompt builds on.

## Tasks

### 1. Install and configure Vue Router

- Install `vue-router@4`.
- Create a `src/router/index.ts` file with route definitions.
- Define at least these initial routes:
  - `/` → Landing page (existing `Landing.vue`)
  - `/login` → Login page (create placeholder)
  - `/signup` → Signup page (create placeholder)
  - `/dashboard` → Dashboard page (create placeholder, protected route)
- Wire the router into `main.ts` and replace the static `<Landing>` import in `App.vue` with `<RouterView>`.

### 2. Install and configure Pinia for state management

- Install `pinia`.
- Create a `src/stores/` directory.
- Create a `src/stores/auth.ts` store with placeholder state: `user`, `isAuthenticated`, `isLoading`.
- Register Pinia in `main.ts`.

### 3. Set up ESLint and Prettier

- Install `eslint`, `@typescript-eslint/parser`, `@typescript-eslint/eslint-plugin`, `eslint-plugin-vue`, and `prettier`.
- Create `.eslintrc.cjs` and `.prettierrc` config files following Vue 3 + TypeScript best practices.
- Add `"lint"` and `"format"` scripts to `package.json`.
- Run the formatter across all existing files to normalize code style.

### 4. Create an app shell layout

- Create a `src/layouts/` directory.
- Create `AppLayout.vue` — an authenticated layout with a sidebar/navbar shell and a `<RouterView>` slot for page content.
- Create `AuthLayout.vue` — a minimal centered layout for login/signup pages.
- Update the router so each route uses the appropriate layout.

### 5. Clean up

- Remove the unused `HelloWorld.vue` component.
- Rename `src/firebase/index.js` to `src/firebase/index.ts` for TypeScript consistency.
- Ensure `npm run build` passes with zero errors and zero warnings.
