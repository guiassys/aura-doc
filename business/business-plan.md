# Business Requirements Document: Auraskill

---

**Version:** 1.0

**Status:** In Definition

**Project:** Aura Suite (AI Professional Identity Engine)

---

## 1. Product Overview

**Auraskill** is a professional identity processing engine designed to convert historical trajectories and technical competencies into high-impact career assets. The system centralizes professional data, treating the resume as a modular, dynamic, and strategic asset, allowing users to manage multiple "aspects" of their career in a single repository.

---

## 2. Personas and Access Profiles

To support the business model (SaaS) and data governance, the system will operate with the following profiles:

### 2.1. Standard User (Free)

- **Focus:** Professionals seeking organization and visibility.
- **Access:** Management of professional profile and use of basic resume templates.

### 2.2. Prime User (Premium)

- **Focus:** Specialists and seniors seeking competitive differentiation.
- **Access:** Advanced features, executive templates, keyword analysis, and unlimited storage of resume versions.

### 2.3. Administrator

- **Focus:** Platform management.
- **Access:** Monitoring metrics, user support, and global permission management.

---

## 3. Functional Requirements (What the system must deliver)

### 3.1. Professional Inventory Management

The system must allow detailed registration and maintenance of:

- **Biographical Data:** Contact information, bio, and social links.
- **Experience Trajectory:** History of companies, positions, and description of achievements.
- **Competency Matrix:** List of technical and behavioral skills with level indication.
- **Complementary Assets:** Highlighted projects, certifications, awards, and academic achievements.

### 3.2. Composition and Generation Engine (Curriculum Engine)

- **Item Selection:** The user must be able to select which specific experiences or skills to include in a particular export.
- **Presentation Models:** Application of different layouts (templates) over the selected data.
- **Smart Export:** Generation of optimized files for recruitment systems (ATS-friendly).

### 3.3. Plan and Permission Management

- **Feature Differentiation:** Blocking and releasing functionalities based on user profile (Standard vs. Prime).
- **Subscription Management:** Interface for the user to manage their Prime membership status.

---

## 4. Business Rules (Operational Logic)

- **BR01 – Unique Identity:** Each authenticated user has a single master professional profile.
- **BR02 – Export Modularity:** Generating a document does not require including all registered data. The user has autonomy to filter what is relevant for each job opening.
- **BR03 – Chronological Consistency:** The system must not allow experience end dates prior to the start date. Experiences without an end date are treated as "Current".
- **BR04 – Premium Feature Disclosure:** Free users should see Premium feature menus as an incentive for upgrade (Upsell), but access must be restricted.
- **BR05 – Data Persistence:** When downgrading from Prime to Standard, user-saved data should not be deleted; only access to advanced templates and functions will be limited.

---

## 5. Quality and Security Requirements

- **Privacy:** Professional data is the exclusive property of the user and cannot be shared without authorization.
- **Availability:** Profile access for quick edits must be available on mobile and desktop devices.
- **Scalability:** The system must maintain document generation performance even with an increasing user base.