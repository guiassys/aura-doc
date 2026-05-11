# Use Case: Manage Professional Social Links

---

**Use Case ID:** UC014
**Use Case Name:** Manage Professional Social Links
**Actors:** Authenticated User, Auraskill System
**Goal:** Allow an authenticated user to add, edit, and delete their professional social media and portfolio links within their profile.

---

## Preconditions

*   The user is authenticated in the Auraskill System.
*   The user has an existing professional profile.
*   The "Manage Social Links" functionality is accessible to the user.

---

## Postconditions

*   **Successful:** The user's professional social link entries are updated (added, edited, or deleted) in their profile.
*   **Unsuccessful:** The professional social link entries are not updated, and an error message is displayed.

---

## Main Flow (Happy Path)

1.  The Authenticated User navigates to the "Manage Social Links" section of their profile.
2.  The Auraskill System displays a list of the user's current social link entries (e.g., LinkedIn, GitHub, Personal Website, Portfolio), along with options to "Add New Link", "Edit" an existing link, or "Delete" an existing link.

### Sub-Flow: Add New Link

2.1. The User clicks "Add New Link".
2.2. The Auraskill System displays a form for entering new social link details (e.g., Platform (LinkedIn, GitHub, etc.), URL).
2.3. The User fills in the required details and clicks "Save".
2.4. The Auraskill System validates the entered information (e.g., required fields, valid URL format).
2.5. The Auraskill System adds the new social link to the user's profile.
2.6. The Auraskill System displays a success message and updates the list of social links.

### Sub-Flow: Edit Existing Link

2.1. The User selects an existing social link and clicks "Edit".
2.2. The Auraskill System displays a form pre-filled with the details of the selected link.
2.3. The User modifies the desired details and clicks "Save".
2.4. The Auraskill System validates the entered information.
2.5. The Auraskill System updates the selected social link in the user's profile.
2.6. The Auraskill System displays a success message and updates the list of social links.

### Sub-Flow: Delete Existing Link

2.1. The User selects an existing social link and clicks "Delete".
2.2. The Auraskill System displays a confirmation prompt (e.g., "Are you sure you want to delete this link? This action cannot be undone.").
2.3. The User confirms the deletion.
2.4. The Auraskill System permanently removes the selected social link from the user's profile.
2.5. The Auraskill System displays a success message and updates the list of social links.

---

## Alternative Flows

*   **AF1: Incomplete/Invalid Information (Sub-Flows Add/Edit Step 2.4):**
    *   2.4a. The Auraskill System identifies missing required fields or invalid data format during validation.
    *   2.4b. The Auraskill System displays specific validation error messages next to the respective fields on the form.
    *   2.4c. The User corrects the information and re-submits the form (return to Sub-Flow Step 2.3).
*   **AF2: User Cancels Operation (Sub-Flows Add/Edit/Delete):**
    *   X.a. The User decides to cancel the current operation (add, edit, or delete).
    *   X.b. The Auraskill System discards any unsaved changes or pending actions.
    *   X.c. The Auraskill System returns the User to the list of social links without making changes.

---

## Exception Flows

*   **EF1: System Error During Save/Delete (Sub-Flows Add/Edit/Delete Step 2.5/2.4):**
    *   X.a. The Auraskill System encounters an unexpected technical error while attempting to save or delete a social link.
    *   X.b. The Auraskill System displays a generic error message (e.g., "An unexpected error occurred. Please try again later.").
    *   X.c. The operation is not completed, and the user may be prompted to retry or contact support.
*   **EF2: Link Not Found (Sub-Flows Edit/Delete Step 2.1):**
    *   2.1a. The Auraskill System cannot find the selected social link (e.g., due to a data corruption or concurrent deletion).
    *   2.1b. The Auraskill System displays an error message (e.g., "The selected link could not be found.").
    *   2.1c. The list of social links is refreshed, and the user can try again.

---

## Non-Functional Requirements (Optional, if specific to this UC)

*   **Usability:** The interface for managing social links should be intuitive, allowing users to easily add, edit, and delete entries.
*   **Data Integrity:** Ensure all social link data is stored correctly, consistently, and adheres to defined data models.
*   **Security:** User-provided social link data must be protected from unauthorized access, modification, or disclosure.
*   **Performance:** Operations (add, edit, delete) should be processed efficiently, with minimal delays.