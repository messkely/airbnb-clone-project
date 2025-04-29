# Airbnb Clone Project

## Overview
The Airbnb Clone Project is a full-stack application designed to simulate a robust booking platform similar to Airbnb.  
Learners will build and deploy a scalable web service with a focus on backend architecture, database design, API security, and CI/CD best practices.  
**Tech stack**: Django, MySQL, GraphQL, Docker, GitHub Actions.

---

## Team Roles

| Role                     | Responsibilities                                                                                  |
| ------------------------ | ------------------------------------------------------------------------------------------------- |
| **Project Manager**      | • Defines scope and milestones<br>• Coordinates team workflow and sprints<br>• Ensures timely delivery |
| **Backend Developer**    | • Designs and implements Django REST/GraphQL APIs<br>• Integrates business logic and services     |
| **Database Administrator** | • Designs relational schema in MySQL<br>• Manages migrations, indexing, and performance tuning      |
| **DevOps Engineer**      | • Configures Docker environments<br>• Builds and maintains CI/CD pipelines (GitHub Actions)<br>• Monitors deployments |
| **Frontend Developer**   | • (If applicable) Implements user interfaces and integrates with backend APIs                     |
| **Security Engineer**    | • Defines authentication/authorization strategy<br>• Implements rate limiting and encryption      |
| **QA Engineer**          | • Writes and executes test plans<br>• Automates end-to-end and API tests<br>• Reports bugs        |

---

## Technology Stack

- **Django**  
  A high-level Python web framework used for building RESTful and GraphQL APIs.
- **MySQL**  
  Relational database management system for storing users, properties, bookings, reviews, and payments.
- **GraphQL**  
  Query language enabling clients to request exactly the data they need, reducing over- and under-fetching.
- **Docker**  
  Containerization platform to standardize development and production environments.
- **GitHub Actions**  
  CI/CD service to automate testing, building, and deployment workflows.
- **Markdown**  
  For documentation and planning (this README itself).

---

## Database Design

### Entities & Key Fields

- **User**  
  - `id` (PK), `username`, `email`, `password_hash`, `date_joined`  
- **Property**  
  - `id` (PK), `owner_id` (FK→User), `title`, `description`, `location`, `price_per_night`  
- **Booking**  
  - `id` (PK), `user_id` (FK→User), `property_id` (FK→Property), `start_date`, `end_date`, `status`  
- **Review**  
  - `id` (PK), `author_id` (FK→User), `property_id` (FK→Property), `rating`, `comment`, `created_at`  
- **Payment**  
  - `id` (PK), `booking_id` (FK→Booking), `amount`, `payment_method`, `status`, `processed_at`  

### Relationships

- One **User** can own many **Properties**.  
- One **Property** can have many **Bookings**.  
- One **User** can make many **Bookings**.  
- One **Property** can have many **Reviews** from different **Users**.  
- One **Booking** has one **Payment**.

---

## Feature Breakdown

1. **User Management**  
   Sign up, log in/out, profile settings, and password reset.  
2. **Property Listings**  
   Create, read, update, and delete property listings with photo uploads.  
3. **Search & Filters**  
   Search by location, date availability, price range, and amenities.  
4. **Booking System**  
   Select dates, request bookings, and view booking history.  
5. **Reviews & Ratings**  
   Leave reviews for stays; aggregate ratings per property.  
6. **Payments**  
   Secure checkout with support for multiple payment methods.  
7. **Admin Dashboard**  
   Manage users, properties, bookings, and site metrics (optional).

---

## API Security

- **Authentication**  
  Implement token-based authentication (JWT or OAuth2) to verify user identity.
- **Authorization**  
  Role-based access control to restrict endpoints (e.g., only owners can modify their properties).
- **Rate Limiting**  
  Throttle requests per IP or user to prevent abuse and DoS attacks.
- **Input Validation & Sanitization**  
  Validate all incoming data to prevent SQL injection and XSS.
- **Encryption**  
  Enforce HTTPS/TLS for data in transit; hash and salt passwords at rest.
- **Audit Logging**  
  Record critical actions (login, bookings, payments) for monitoring and forensics.

---

## CI/CD Pipeline

Continuous Integration and Continuous Deployment (CI/CD) automate testing, building, and deployment to reduce manual errors and speed up releases.

- **GitHub Actions**  
  - Run unit and integration tests on every PR.  
  - Build Docker images and push to registry.  
  - Deploy to staging/production on merge to main.  
- **Docker**  
  - Containerize the Django app, database, and any auxiliary services.  
- **Environments**  
  - Use separate staging and production environments with IaC (e.g., Terraform, Docker Compose).

---

## Manual Review

Please review this README for completeness, accuracy, and consistency with your project plan before moving on to actual implementation.  
