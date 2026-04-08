# Prompt 2: Firebase Authentication

## Objective

Implement full user authentication using Firebase Auth — email/password signup and login, persistent sessions, route guards, and a user profile foundation.

## Tasks

### 1. Configure Firebase Auth

- In `src/firebase/index.ts`, initialize and export the Firebase `Auth` instance using `getAuth()`.
- Create a `src/services/auth.ts` module that wraps Firebase Auth methods:
  - `signUp(email, password)` — creates a new user with `createUserWithEmailAndPassword`.
  - `logIn(email, password)` — signs in with `signInWithEmailAndPassword`.
  - `logOut()` — signs out the current user.
  - `onAuthChange(callback)` — subscribes to `onAuthStateChanged`.

### 2. Build the auth store

- Update `src/stores/auth.ts` to:
  - Call `onAuthChange` on app initialization to hydrate the `user` state.
  - Expose `signUp`, `logIn`, `logOut` actions that call the service layer.
  - Track loading and error states.

### 3. Create Login and Signup pages

- Build `src/pages/LoginPage.vue` with an email/password form, validation, error display, and a link to the signup page.
- Build `src/pages/SignupPage.vue` with an email/password/confirm-password form, validation, error display, and a link to the login page.
- Style both pages using Tailwind CSS and the `AuthLayout`.
- On successful login/signup, redirect to `/dashboard`.

### 4. Add route guards

- Create a `src/router/guards.ts` file.
- Implement a `beforeEach` navigation guard:
  - If the route requires auth (`meta.requiresAuth`) and the user is not authenticated, redirect to `/login`.
  - If the user is authenticated and tries to visit `/login` or `/signup`, redirect to `/dashboard`.
- Wait for the initial auth state to resolve before making guard decisions (avoid flicker).

### 5. Add a user menu to the app layout

- In `AppLayout.vue`, display the current user's email in the navbar/sidebar.
- Add a "Sign out" button that calls `logOut()` and redirects to `/`.

### 6. Error handling

- Display user-friendly error messages for common Firebase Auth errors (invalid email, wrong password, email already in use, weak password, etc.).
