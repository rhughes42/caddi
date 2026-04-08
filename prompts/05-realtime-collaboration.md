# Prompt 5: Real-time Collaboration and Team Features

## Objective

Add multi-user support — invite team members to projects, share tasks, and enable real-time data synchronization using Firestore's real-time listeners.

## Tasks

### 1. Extend the Project model for collaboration

- Add a `memberIds: string[]` field to the `Project` interface.
- Add a `members` subcollection or map that tracks each member's role (`owner`, `editor`, `viewer`).

### 2. Build the invitation system

- Create an `Invitation` type:
  ```
  interface Invitation {
    id: string;
    projectId: string;
    invitedEmail: string;
    invitedBy: string;
    status: 'pending' | 'accepted' | 'declined';
    role: 'editor' | 'viewer';
    createdAt: Timestamp;
  }
  ```
- Create a `src/services/invitations.ts` module to send, accept, and decline invitations.
- When an invitation is accepted, add the user to the project's `memberIds`.

### 3. Build team management UI

- Add a "Team" tab or section on the project detail page.
- Show current members with their roles.
- Include an "Invite" button that opens a form to invite by email.
- Allow the project owner to change roles or remove members.

### 4. Enable real-time Firestore listeners

- Refactor the projects and tasks stores to use `onSnapshot` instead of one-time `getDocs` queries.
- When a team member updates a task or project, all connected users should see the change immediately.
- Handle listener cleanup on component unmount and logout.

### 5. Update Firestore security rules

- Allow project members (not just the owner) to read the project and its tasks.
- Only editors and owners can write tasks.
- Only the owner can manage team membership.
- Only the owner can delete the project.

### 6. Add task assignment

- Update the task creation/edit form to allow assigning a task to a project member (dropdown of member emails/names).
- Show the assignee avatar/name on task cards.
- Add a "My Tasks" view on the dashboard that aggregates tasks assigned to the current user across all projects.
