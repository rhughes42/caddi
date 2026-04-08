# Prompt 3: Firestore Data Layer and Project Management

## Objective

Set up Firestore as the data backend and build the core "Project" data model — the central entity users will interact with in the dashboard.

## Tasks

### 1. Configure Firestore

- In `src/firebase/index.ts`, initialize and export the Firestore instance using `getFirestore()`.
- Create `src/services/firestore.ts` with generic CRUD helpers:
  - `createDocument(collection, data)` — adds a document.
  - `getDocument(collection, id)` — gets a single document.
  - `listDocuments(collection, queryConstraints)` — queries with filters/ordering.
  - `updateDocument(collection, id, data)` — updates fields.
  - `deleteDocument(collection, id)` — deletes a document.

### 2. Define the Project model

- Create `src/types/project.ts` with a TypeScript interface:
  ```
  interface Project {
    id: string;
    name: string;
    description: string;
    ownerId: string;
    status: 'active' | 'archived' | 'completed';
    createdAt: Timestamp;
    updatedAt: Timestamp;
  }
  ```

### 3. Build the projects store

- Create `src/stores/projects.ts` using Pinia.
- Implement actions: `fetchProjects`, `createProject`, `updateProject`, `deleteProject`.
- All queries should be scoped to the authenticated user's `ownerId`.
- Handle loading and error states.

### 4. Build the Dashboard page

- Replace the placeholder `DashboardPage.vue` with a real page that:
  - Lists the user's projects in a card grid or table.
  - Shows project name, status, and last updated date.
  - Includes an "empty state" when the user has no projects.
  - Has a "New Project" button that opens a creation dialog or navigates to a creation page.

### 5. Build the Project creation flow

- Create a `NewProjectPage.vue` or modal component with a form for project name and description.
- On submit, create the project in Firestore and redirect to the dashboard.
- Validate that the project name is not empty.

### 6. Build the Project detail page

- Create a route `/projects/:id` that loads and displays a single project.
- Show the project's name, description, status, and timestamps.
- Include an "Edit" button to update the project name/description.
- Include a "Delete" button with a confirmation dialog.

### 7. Firestore security rules (documentation)

- Create a `firestore.rules` file in the project root with rules that:
  - Allow authenticated users to read/write only their own projects.
  - Deny all access to unauthenticated users.
  - Validate required fields on writes.
