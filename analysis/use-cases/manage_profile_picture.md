# Use Case: Manage Professional Profile Picture

---

**Use Case ID:** UC016
**Use Case Name:** Manage Professional Profile Picture
**Actors:** Authenticated User, Auraskill System
**Goal:** Allow an authenticated user to upload, change, or remove their professional profile picture.

---

## Preconditions

*   The user is authenticated in the Auraskill System.
*   The user has an existing professional profile.
*   The "Manage Profile Picture" functionality is accessible to the user.

---

## Postconditions

*   **Successful:** The user's professional profile picture is updated or removed.
*   **Unsuccessful:** The professional profile picture is not updated or removed, and an error message is displayed.

---

## Main Flow (Happy Path)

1.  The Authenticated User navigates to the "Manage Profile Picture" section of their profile.
2.  The Auraskill System displays the user's current profile picture (if any) and options to "Upload New Picture" or "Remove Picture".

### Sub-Flow: Upload New Picture

2.1. The User clicks "Upload New Picture".
2.2. The Auraskill System displays a file upload interface.
2.3. The User selects an image file from their local device and initiates the upload.
2.4. The Auraskill System validates the uploaded file (e.g., file type, size, dimensions).
2.5. The Auraskill System processes the image (e.g., resizing, cropping) and stores it.
2.6. The Auraskill System updates the user's profile with the new profile picture.
2.7. The Auraskill System displays a confirmation message (e.g., "Profile picture updated successfully!") and updates the displayed picture.

### Sub-Flow: Remove Picture

2.1. The User clicks "Remove Picture".
2.2. The Auraskill System displays a confirmation prompt (e.g., "Are you sure you want to remove your profile picture?").
2.3. The User confirms the removal.
2.4. The Auraskill System removes the profile picture from the user's profile and storage.
2.5. The Auraskill System displays a confirmation message (e.g., "Profile picture removed successfully!") and updates the displayed picture to a default avatar.

---

## Alternative Flows

*   **AF1: Invalid File Upload (Sub-Flow Upload Step 2.4):**
    *   2.4a. The Auraskill System identifies that the uploaded file is not a valid image type, exceeds size limits, or has incorrect dimensions.
    *   2.4b. The Auraskill System displays a specific validation error message (e.g., "Invalid file type. Please upload a JPG, PNG, or GIF image.").
    *   2.4c. The User selects a different file and re-attempts the upload (return to Sub-Flow Upload Step 2.3).
*   **AF2: User Cancels Operation (Sub-Flows Upload/Remove):**
    *   X.a. The User decides to cancel the current operation (upload or remove).
    *   X.b. The Auraskill System discards any pending changes.
    *   X.c. The Auraskill System returns the User to the "Manage Profile Picture" section without making changes.

---

## Exception Flows

*   **EF1: System Error During Upload/Removal (Sub-Flows Upload/Remove Step 2.6/2.4):**
    *   X.a. The Auraskill System encounters an unexpected technical error while attempting to save or remove the profile picture.
    *   X.b. The Auraskill System displays a generic error message (e.g., "An unexpected error occurred. Please try again later.").
    *   X.c. The operation is not completed, and the user may be prompted to retry or contact support.

---

## Non-Functional Requirements (Optional, if specific to this UC)

*   **Usability:** The interface for managing the profile picture should be intuitive, providing clear options for upload and removal.
*   **Data Integrity:** Ensure profile pictures are stored securely and associated correctly with the user's profile.
*   **Security:** Uploaded images must be scanned for malicious content. Access to profile pictures must be controlled.
*   **Performance:** Image upload, processing, and display should be efficient.
*   **Storage:** Efficient storage mechanisms for image files should be used.