# SODA Backend (Personal Fork Documentation)

> **Note:** This README documents my personal contributions to the SODA backend module.  
> It is based on my fork of the original repository and is intended **solely for showcasing my work** for MS CS applications.  
> This is not an official documentation of the original project.

---

## Project Context

This repository contains the **backend server** for the SODA social platform, developed using Django.  
The backend provides RESTful API endpoints for user authentication, profile management, posts, and social interactions.  

The project was a collaborative effort, and I was fully responsible for the **user module**, covering both design and implementation.

---

## Backend Overview

- **Framework:** Django  
- **Database Management:** Django ORM  
- **API Format:** JSON over HTTP  
- **Authentication:** JWT-based token authentication for frontend session management  
- **Deployment:** Hosted alongside the frontend on a Raspberry Pi for live classroom demonstration  

The backend handles all data persistence and business logic, while the frontend interacts via RESTful APIs.  

---

## My Contributions: User Module

I was solely responsible for the **complete user authentication and profile management backend**, including two main modules: **userctrl** and **UserProfile**. My contributions cover the full lifecycle of the user module, from database modeling to API design and implementation.

- **Authentication & Registration (`userctrl`)**
  - Validates credentials received from frontend (SHA-256 hashed)
  - Registers new users and ensures username uniqueness
  - Issues **JWT tokens** for lightweight session management, stored by the frontend
  - Updates `last_login` timestamps and handles error scenarios gracefully

- **Profile Management (`UserProfile`)**
  - Retrieves and updates user profiles, including first name, last name, email, and introduction
  - Supports following/unfollowing users, and tracks relationships in the database
  - Provides endpoints to list followers and followings
  - Ensures data integrity and returns structured JSON responses with proper HTTP status codes

- **Database Models**
  - Managed using Django ORM: `User`, `Follow`, `UserTag`, `PostTag`, `Like`, etc.
  - Maintains referential integrity and uniqueness (`unique_together`)
  - Enables modular and extensible support for social features

- **Error Handling & Validation**
  - Comprehensive handling of input validation, missing parameters, and database integrity
  - Returns user-friendly messages for frontend consumption

---

## Technology Highlights

- **JWT tokens**: issued on login, stored by the frontend for lightweight session management  
- **RESTful API design**: supports frontend–backend separation  
- **Modular architecture**: `userctrl` and `UserProfile` designed independently for extensibility  
- **Django ORM**: ensures data consistency, relationship constraints, and referential integrity  
- **Lightweight session**: frontend manages login state via JWT without complex session tables  

---

## Deployment & Demonstration

- Backend and frontend were deployed on a **self-hosted Raspberry Pi**  
- Demonstrated in a final course presentation with multiple users performing:
  - Registration and login  
  - Profile management  
  - Posting and searching content  
  - Private messaging  
  - Following/unfollowing users  
- Validated the robustness and usability of the implemented user module

---

## Future Improvements

- Replace the current lightweight authentication flow with a **secure, server-managed session or cookie-based mechanism**, including proper session lifecycle management and CSRF protection  
- Introduce a **state management strategy** for backend data caching or session handling if user scale increases  
- Formalize API contracts and schema validation for long-term maintainability  
- Enhance error handling and observability for better monitoring in production  
- Conduct comprehensive unit and integration testing to ensure reliability and regression safety  
- Expand user profile functionality with more advanced personalization features, such as dynamic tags, privacy settings, and recommendation preferences
