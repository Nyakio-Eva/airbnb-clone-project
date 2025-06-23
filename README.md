# air-bnb-clone-project
## Team Roles
#### 1. Backend Developer
- Role: Builds and maintains the server-side logic, APIs, and business logic that powers the application.
- Responsibilities:
    * Design and build RESTful APIs for listings, bookings, users, and payments.
    * Implement authentication (e.g., signup/login).
    * Handle business logic like booking availability, price calculations, and validation.
    * Ensure performance, scalability, and security of the backend.
    * Write unit and integration tests for backend components.

#### 2. Database Administrator (DBA)
- Role: Designs, manages, and maintains the database that stores all application data.
- Responsibilities:
* Design database schema (e.g., for users, properties, bookings, reviews).
* Optimize database performance and indexing.
* Set up backups and data recovery strategies.
* Ensure data integrity and enforce constraints.
* Support developers with efficient queries.
        
#### 3. DevOps Engineer
- Role: Sets up the infrastructure and CI/CD pipeline to deploy and maintain the app.
- Responsibilities:
 * Configure hosting (e.g., AWS, Heroku, or Docker containers).  
 * Automate deployment and testing pipelines.
 * Monitor application uptime, logs, and metrics.
 * Manage environments (development, staging, production).
 * Ensure app security, scalability, and smooth deployment.
#### 4. Quality Assurance (QA) / Tester
- Role: Ensures the app works as intended and catches bugs before users do.
- Responsibilities:
  * Create test cases and test plans for core features (like booking and signup). 
  * Perform manual and automated testing. 
  * Validate bug fixes and regression tests.
  * Report and track bugs.
  * Ensure the product meets acceptance criteria
##### 5. Project Manager / Scrum Master
  - Role: Keeps the project organized, on track, and ensures team collaboration.
  - Responsibilities:
    * Define milestones, timelines, and deliverables.
    * Run standups and retrospectives.
    * Assign tasks and track progress using tools like Trello or Jira.
    * Communicate with stakeholders and manage documentation.
    * Remove blockers for the dev team.
## Technology
- Django: A high-level Python web framework used for building a RESTful API.
- Django REST Framework: Provides tools for creating and managing RESTful APIs.
- PostgreSQL: A powerful relational database used for data storage.
- GraphQL: Allows for flexible and efficient querying of data.
- Celery: For handling asynchronous tasks such as sending notifications or processing payments.
- Redis: Used for caching and session management.
- Docker: Containerization tool for consistent development and deployment environments.
- CI/CD Pipelines: Automated pipelines for testing and deploying code changes.
  
## Database Design
#### 1. Users
- A user can have many properties (the host)
- A user can have many bookings (the guest)
- A user can make many payments
- A user can write many reviews on different properties
- A user can both book and host 
#### 2. Properties
- A property can have many bookings
- A property can have many reviews
#### 3. Payments
- one payment belongs to one booking
#### 4. Bookings
- one booking belongs to one user
- One booking is for one property
  
#### 5. Reviews
- A user can write one review per property
- A property can have many reviews

 ## Feature Breakdown
 #### 1. API Documentation
 - Ensures  that the backend APIs are well-documented using the OpenAPI standard, making them easy to understand, use, and test.With both Django REST framework and GraohQL, the system offers flexibility for standard CRUD operations and GrapHQL for optimized, custom data queries.
#### 2. User Management
- Allows users to register, login and manage their profiles via endpoints like /users/ and /users/{user_id}. It provides a secure foundation for tracking user-specific actions like bookings, payments and reviews, while enabling role-based access e.g guest vs host
#### 3. Property management
- Through endpoints like /properties/, users (typically hosts) can create, edit, view, or delete property listings. This is the core feature that populates the app’s marketplace, allowing users to browse available places to stay and enabling hosts to manage their offerings.
#### 4. Booking System
- The booking system allows guests to book, update, or cancel reservations through endpoints like /bookings/. It handles check-in/check-out dates, availability validation, and links to both user and property data—forming the transactional heart of the application.
#### 5. Payment processing
- This feature manages the payment workflow, ensuring that guests can securely pay for bookings through the /payments/ endpoint. It handles transactions, links them to specific bookings, and may support future extensions like refunds or payment history.
#### 6. Review System
- Guests can leave ratings and written reviews for properties they've stayed in using endpoints like /reviews/. This feature builds trust and transparency, helping future users make informed decisions and giving hosts valuable feedback.
#### 7. Database Optimization
- To ensure smooth performance at scale, this feature introduces indexing for faster queries and caching mechanisms to minimize repetitive database access. These optimizations contribute significantly to speed, scalability, and user experience, especially under high traffic.

## API Security 
#### 1. Authentication
- Verifies the identity of users before granting access, via JWT tokens or session-based logins.
- This ensures that only the registered users can access sensitive actions like boking a property, viewing their profile, or making payments.
#### 2. Authorization
- Controls what an authenticated user is allowed to do. e.g a guest can't edit another user's booking.
- It prevents privelege escalation and data leaks.
#### 3. Rate limiting
- Limits the number of requests a user or bot can make to the API within a certain timeframe.
- It protects against denial of service (DoS) attacks and brute-force login attempts.
#### 4. Data Validation
- Ensures that user input is properly checked and cleaned before being processed or stored in the database.
- It prevents SQL injection, Cross-site scripting(xss) and other input-based attacks.
#### 5. HTTPS and Secure Communication
- Uses SSL/TLS encryption to protect all data transmitted between clients and the server.
- prevents man-in-the-middle attacks, keeping user credentials, payment info, and personal data safe from interception.
#### 6. Secure Payment Handling
- Uses a trusted third-party payment processor e.g paypal, Stripe, Mpesa rather than handling card details directly.
- It protects both the platform and it's users from credit card fraud and regulatory risks
#### 7. Password Hashing
- Stores user passwords as hashed, not plain text using algorithms like bcrypt or Argon2
- Even if the database is compromised, hashed passwords are hard to reverse.
#### 8. CORS
- Controls which frontend dormains can acces backend resources
- Prevents malicious websites from making unauthorized requests to tje backend on behalf of a logged in user(CSRF-like behavior)
#### 9. Logging and monitoring
  - Tracks critical actions and security events such as failed logins, data access attaempts and paymen failures.
  - Helps in detecting suspicious activity early and aids in incdent response if a breach occurs.
#### 10. Role-Based Access Control
- Assigns specific permissions based on user roles e.g guest, host, admin
- Helps enforce boundaries and restricts access to sensitive admin features or user data.
  
