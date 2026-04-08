# Prompt 6: Notifications, Activity Feed, and User Settings

## Objective

Add a notification system, project activity history, and user profile/settings so users stay informed and can personalize their experience.

## Tasks

### 1. Build the notification system

- Create a `Notification` type:
  ```
  interface Notification {
    id: string;
    userId: string;
    type: 'task_assigned' | 'task_updated' | 'invitation_received' | 'project_updated';
    message: string;
    read: boolean;
    relatedProjectId?: string;
    relatedTaskId?: string;
    createdAt: Timestamp;
  }
  ```
- Create `src/services/notifications.ts` with methods to list, mark-as-read, and delete notifications.
- Create `src/stores/notifications.ts` with a real-time listener for unread notifications.

### 2. Build the notification UI

- Add a bell icon to the app layout navbar with an unread count badge.
- Clicking the bell opens a dropdown or slide-over panel listing recent notifications.
- Each notification links to the relevant project/task.
- Include a "Mark all as read" action.

### 3. Build the activity feed

- Create an `ActivityEvent` type to log actions (task created, status changed, member added, etc.).
- Store activity events as a subcollection under each project.
- Display a chronological activity feed on the project detail page.
- Show who did what and when, with human-readable descriptions.

### 4. Build user settings page

- Create a route `/settings` with a `SettingsPage.vue`.
- Sections:
  - **Profile**: Display name, email (read-only), avatar upload (Firebase Storage).
  - **Password**: Change password form.
  - **Notifications**: Toggle email notifications on/off (store preference in Firestore user profile doc).
  - **Danger Zone**: Delete account.

### 5. Create the user profile document

- On signup, create a Firestore document in a `users` collection:
  ```
  interface UserProfile {
    uid: string;
    email: string;
    displayName: string;
    avatarUrl?: string;
    notificationsEnabled: boolean;
    createdAt: Timestamp;
  }
  ```
- Update the auth store to load the user profile on auth state change.

### 6. Trigger notifications on key events

- When a task is assigned to someone, create a notification for the assignee.
- When a user is invited to a project, create a notification.
- When a task status changes, notify the project owner (if someone else changed it).
