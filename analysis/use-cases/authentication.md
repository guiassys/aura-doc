# Use Case: User Authentication via Keycloak

---

**Use Case ID:** UC001
**Use Case Name:** User Authentication via Keycloak
**Actors:** User, Auraskill System, Keycloak Identity Provider
**Goal:** Allow a user to securely log in to the Auraskill system using Keycloak.

---

## Preconditions

*   The user has an active account in Keycloak.
*   The Auraskill system is running and accessible.
*   Keycloak is configured as the Identity Provider for Auraskill.

---

## Postconditions

*   **Successful:** The user is authenticated and redirected to the application's home screen with appropriate access tokens and user information displayed.
*   **Unsuccessful:** The user remains unauthenticated, and an error message (if applicable) is displayed or the user is prompted to try again.

---

## Main Flow (Happy Path)

1.  The User accesses the Auraskill application's initial screen.
2.  The Auraskill System checks if the User is authenticated.
3.  The Auraskill System determines the User is not authenticated and redirects the User's browser to the Keycloak authentication screen.
4.  The User enters valid credentials (username and password) on the Keycloak authentication screen.
5.  Keycloak authenticates the User.
6.  Keycloak redirects the User's browser back to the Auraskill application's initial screen, including an Access Token.
7.  The Auraskill System validates the Access Token.
8.  The Auraskill System displays the initial screen, showing the authenticated User's name and email, and all menus accessible to them based on their roles/permissions.

---

## Alternative Flows

*   **AF1: Invalid Credentials (Step 4):**
    *   4a. The User enters invalid credentials.
    *   4b. Keycloak displays an error message (e.g., "Invalid username or password").
    *   4c. The User can re-attempt login (return to Step 4) or cancel.
*   **AF2: User Cancels Authentication (Step 4):**
    *   4a. The User chooses to cancel the authentication process on the Keycloak screen.
    *   4b. Keycloak redirects the User back to the Auraskill application, possibly with an error or unauthenticated status.
    *   4c. The Auraskill System displays the unauthenticated initial screen.

---

## Exception Flows

*   **EF1: Session Expired/Invalid Token (Step 7):**
    *   7a. The Auraskill System fails to validate the Access Token (e.g., expired, tampered).
    *   7b. The Auraskill System redirects the User back to the Keycloak authentication screen (return to Step 3).

---

## Non-Functional Requirements (Optional, if specific to this UC)

*   **Security:** Authentication must be secure, protecting user credentials and session data.
*   **Performance:** The authentication process should be fast and responsive.
*   **Usability:** The authentication flow should be intuitive for the user.