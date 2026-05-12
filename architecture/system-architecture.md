# AuraSkill System Architecture Guide 🏛️

This document outlines the high-level architecture, data flow, and infrastructure design of the **AuraSkill** ecosystem managed by the **Apexlone Organization**.

---

## 1. High-Level Overview
AuraSkill is a decoupled multi-service ecosystem designed for scalability and secure identity management. It utilizes a **GitOps** approach for infrastructure management and a **Self-Hosted CI/CD** pipeline.



### Core Components:
*   **Aura-Front (Next.js):** The user interface, handling Server-Side Rendering (SSR) and client-side interactions.
*   **Aura-API (Spring Boot):** The core business logic layer and RESTful service provider.
*   **Keycloak (IAM):** Centralized Identity and Access Management using OIDC (OpenID Connect).
*   **Persistence Layer:** Isolated PostgreSQL instances for both the application and identity provider.

---

## 2. Infrastructure Design (WSL2 + Docker)
The environment is orchestrated using native **Docker Engine** on **WSL2 (Ubuntu)**, bypassing Docker Desktop for better performance and native Linux compatibility.

### Service Stack:
| Service | Technology | Port | Purpose |
| :--- | :--- | :--- | :--- |
| **Frontend** | Next.js | 3000 | User Interface |
| **Backend** | Spring Boot | 8081 | Business Logic / API |
| **Auth** | Keycloak | 8080 | Identity & Access |
| **App DB** | PostgreSQL 16 | 5432 | Application Data |
| **KC DB** | PostgreSQL 16 | 5433 | Keycloak Metadata |



---

## 3. CI/CD & Deployment Flow
We use **GitHub Actions** coupled with a **Self-Hosted Runner** residing within the WSL2 environment. This allows for direct deployment to the local hardware while maintaining the security and automation of GitHub.

### The Pipeline Logic:
1.  **Code Push:** Developer pushes to `hml` or `main` branches.
2.  **Orchestration:** GitHub Actions triggers the job on the `apexlone-srv` runner.
3.  **Deployment:** The runner executes `docker compose up -d --build`, ensuring the latest image is built and deployed.
4.  **Monitoring:** Portainer manages the container lifecycle and provides visual health checks.

---

## 4. Authentication Flow (OIDC)
AuraSkill implements a secure authentication flow using **NextAuth.js** and **Keycloak**.

1.  **Challenge:** User attempts to access a protected route in `aura-front`.
2.  **Redirect:** User is redirected to the Keycloak Login Page.
3.  **Token Exchange:** Upon successful login, Keycloak issues a JWT (ID Token, Access Token).
4.  **Session:** `aura-front` persists the session; the Access Token is forwarded to `aura-api` in the `Authorization: Bearer` header for authorized requests.



---

## 5. Persistence and Data Isolation
To ensure data integrity, each service has its own dedicated database schema/instance:
*   **`auraskill-db-app`**: Stores users' skills, profiles, and application-specific metrics.
*   **`auraskill-db-keycloak`**: Stores realms, clients, and credential hashes.

**Data Mapping:** Persistence is guaranteed via Docker Volumes mapped to the WSL2 file system at `./data/`, preventing data loss during container restarts or updates.

---

## 6. Developer Guidelines
*   **Environment Sync:** Always ensure your `.env` files are synchronized across `dev` and `hml` environments.
*   **Type Safety:** When modifying Auth flows, update the `next-auth.d.ts` file in the frontend to reflect new token claims.
*   **Architecture Evolution:** Any change in the networking or service ports must be updated in this document first (Architecture-First approach).

---
**Maintained by Apexlone Organization**  
*Last Updated: 2026*