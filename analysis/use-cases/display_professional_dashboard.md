# Use Case: Display Professional Dashboard

---

**Use Case ID:** UC002
**Use Case Name:** Display Professional Dashboard After Authentication
**Actors:** Authenticated User, Auraskill System
**Goal:** Present the authenticated user with their personalized professional dashboard, displaying key profile information.

---

## Preconditions

*   The user has successfully authenticated via Keycloak (UC001 completed successfully).
*   The Auraskill System has received a valid Access Token for the user.
*   The user has an existing professional profile registered in the Auraskill System.

---

## Postconditions

*   **Successful:** The user's personalized "Dashboard" screen is displayed, showing their professional name, photo, biography, and top 3 items for education/certifications, professional experience, and awards/recognitions.
*   **Unsuccessful:** The user is redirected to a profile creation screen or an error message is displayed indicating the absence of a professional profile.

---

## Main Flow (Happy Path)

1.  The Auraskill System receives the authenticated user's session (after successful Keycloak login).
2.  The Auraskill System verifies if the user (identified by `keycloak_user_id`) has a valid professional profile registered.
3.  The Auraskill System identifies an existing professional profile for the user.
4.  The Auraskill System retrieves the professional's information.
5.  The Auraskill System displays the "Dashboard" screen, presenting:
    *   Professional's Name
    *   Professional's Photo
    *   Professional's Biography
    *   Top 3 Education/Certification items
    *   Top 3 Professional Experience items
    *   Top 3 Awards or Recognition items
6.  The Auraskill System also displays all menus accessible to the user based on their roles/permissions.

---

## Alternative Flows

*   **AF1: User Lacks Professional Profile (Step 2):**
    *   2a. The Auraskill System verifies the user's authentication but identifies that no professional profile is registered for the `keycloak_user_id`.
    *   2b. The Auraskill System redirects the user to a "Create Professional Profile" screen.
    *   2c. The user can then proceed to create their professional profile.

---

## Exception Flows

*   **EF1: Data Retrieval Error (Step 4):**
    *   4a. The Auraskill System encounters an error while attempting to retrieve the professional's information.
    *   4b. The Auraskill System displays an error message (e.g., "Could not load profile data. Please try again later.")
    *   4c. The user remains on a loading screen or is redirected to a generic error page.

---

## Non-Functional Requirements (Optional, if specific to this UC)

*   **Performance:** The dashboard and professional information should load quickly to provide a responsive user experience.
*   **Security:** Professional data displayed must be accurate and accessible only to the authenticated user.
*   **Usability:** The dashboard layout should be clear, intuitive, and easy to navigate.