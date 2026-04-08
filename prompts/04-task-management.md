# Prompt 4: Task Management Within Projects

## Objective

Add a task/to-do system within each project — the core productivity feature. Users should be able to create, assign, prioritize, and track tasks inside their projects.

## Tasks

### 1. Define the Task model

- Create `src/types/task.ts`:
  ```
  interface Task {
    id: string;
    projectId: string;
    title: string;
    description: string;
    status: 'todo' | 'in_progress' | 'done';
    priority: 'low' | 'medium' | 'high';
    assigneeId?: string;
    dueDate?: Timestamp;
    createdAt: Timestamp;
    updatedAt: Timestamp;
  }
  ```

### 2. Build the tasks service and store

- Create `src/services/tasks.ts` with Firestore CRUD operations for tasks scoped to a project.
- Create `src/stores/tasks.ts` with actions: `fetchTasks(projectId)`, `createTask`, `updateTask`, `deleteTask`, `updateTaskStatus`.

### 3. Build the Kanban board view

- Create a `TaskBoard.vue` component that displays tasks in three columns: To Do, In Progress, Done.
- Each task appears as a card showing title, priority badge, and due date.
- Allow dragging tasks between columns to change status (use a library like `vuedraggable` or implement simple click-to-move).
- Integrate this into the project detail page.

### 4. Build a task creation/edit form

- Create a `TaskForm.vue` component (modal or slide-over) with fields for title, description, status, priority, and due date.
- Reuse for both creating new tasks and editing existing ones.

### 5. Add task list view

- Create a `TaskList.vue` component as an alternative table/list view of tasks.
- Include sortable columns (title, status, priority, due date).
- Include filters for status and priority.
- Allow toggling between board view and list view on the project detail page.

### 6. Update Firestore rules

- Extend `firestore.rules` so that tasks are readable/writable only by the project owner.
- Tasks should be stored as a subcollection under each project: `projects/{projectId}/tasks/{taskId}`.
