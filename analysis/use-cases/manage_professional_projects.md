# Use Case: Manage Professional Projects

---

**Use Case ID:** UC012
**Use Case Name:** Manage Professional Projects
**Actors:** Authenticated User, Auraskill System
**Goal:** Allow an authenticated user to add, edit, and delete their professional project entries within their profile.

---

## Preconditions

*   The user is authenticated in the Auraskill System.
*   The user has an existing professional profile.
*   The "Manage Professional Projects" functionality is accessible to the user.

---

## Postconditions

*   **Successful:** The user's professional project entries are updated (added, edited, or deleted) in their profile.
*   **Unsuccessful:** The professional project entries are not updated, and an error message is displayed.

---

## Main Flow (Happy Path)

1.  The Authenticated User navigates to the "Manage Professional Projects" section of their profile.
2.  The Auraskill System displays a list of the user's current project entries, along with options to "Add New Project", "Edit" an existing project, or "Delete" an existing project.

### Sub-Flow: Add New Project

2.1. The User clicks "Add New Project".
2.2. The Auraskill System displays a form for entering new project details (e.g., Project Name, Role, Technologies Used, Start Date, End Date, Description, URL/Repository Link).
2.3. The User fills in the required details and clicks "Save".
2.4. The Auraskill System validates the entered information (e.g., required fields, date formats).
2.5. The Auraskill System adds the new professional project to the user's profile.
2.6. The Auraskill System displays a success message and updates the list of projects.

### Sub-Flow: Edit Existing Project

2.1. The User selects an existing project and clicks "Edit".
2.2. The Auraskill System displays a form pre-filled with the details of the selected project.
2.3. The User modifies the desired details and clicks "Save".
2.4. The Auraskill System validates the entered information.
2.5. The Auraskill System updates the selected professional project in the user's profile.
2.6. The Auraskill System displays a success message and updates the list of projects.

### Sub-Flow: Delete Existing Project

2.1. The User selects an existing project and clicks "Delete".
2.2. The Auraskill System displays a confirmation prompt (e.g., "Are you sure you want to delete this project? This action cannot be undone.").
2.3. The User confirms the deletion.
2.4. The Auraskill System permanently removes the selected professional project from the user's profile.
2.5. The Auraskill System displays a success message and updates the list of projects.

---

## Alternative Flows

*   **AF1: Incomplete/Invalid Information (Sub-Flows Add/Edit Step 2.4):**
    *   2.4a. The Auraskill System identifies missing required fields or invalid data format during validation.
    *   2.4b. The Auraskill System displays specific validation error messages next to the respective fields on the form.
    *   2.4c. The User corrects the information and re-submits the form (return to Sub-Flow Step 2.3).
*   **AF2: User Cancels Operation (Sub-Flows Add/Edit/Delete):**
    *   X.a. The User decides to cancel the current operation (add, edit, or delete).
    *   X.b. The Auraskill System discards any unsaved changes or pending actions.
    *   X.c. The Auraskill System returns the User to the list of professional projects without making changes.

---

## Exception Flows

*   **EF1: System Error During Save/Delete (Sub-Flows Add/Edit/Delete Step 2.5/2.4):**
    *   X.a. The Auraskill System encounters an unexpected technical error while attempting to save or delete a project.
    *   X.b. The Auraskill System displays a generic error message (e.g., "An unexpected error occurred. Please try again later.").
    *   X.c. The operation is not completed, and the user may be prompted to retry or contact support.
*   **EF2: Project Not Found (Sub-Flows Edit/Delete Step 2.1):**
    *   2.1a. The Auraskill System cannot find the selected project (e.g., due to a data corruption or concurrent deletion).
    *   2.1b. The Auraskill System displays an error message (e.g., "The selected project could not be found.").
    *   2.1c. The list of projects is refreshed, and the user can try again.

---

## Non-Functional Requirements (Optional, if specific to this UC)

*   **Usability:** The interface for managing projects should be intuitive, allowing users to easily add, edit, and delete entries.
*   **Data Integrity:** Ensure all project data is stored correctly, consistently, and adheres to defined data models.
*   **Security:** User-provided project data must be protected from unauthorized access, modification, or disclosure.
*   **Performance:** Operations (add, edit, delete) should be processed efficiently, with minimal delays.