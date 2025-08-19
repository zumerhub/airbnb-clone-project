# About the Project
The Airbnb Clone Project is a comprehensive, real-world application designed to simulate the development of a robust booking platform like Airbnb. It involves a deep dive into full-stack development, focusing on backend systems, database design, API development, and application security. 

# Learning Objective
This project is tailored to enhance your expertise in modern software development practices. 

Master collaborative team workflows using GitHub.
Deepen backend architecture and database design principles.
Implement advanced security measures for API development.
Gain proficiency in designing and managing CI/CD pipelines for efficient deployment.
Strengthen ability to document and plan complex software projects effectively.
Develop an understanding of integrating technologies like Django, MySQL, and GraphQL in a unified ecosystem.

# Team Roles

### Backend Developer
  Responsible for implementing API endpoints, database schemas, and business logic.

### Database Administrator
  Manages database design, indexing, and optimizations.

### Business analyst (BA)
  - Understands customer’s business processes.
  - Translates customer business needs into requirements.
  
  Business analyst roles includes:
    A business analyst dives deep into a customer’s workflows and analyzes stakeholder feedback to help a client formulate what their wants look like and align a customer’s vision with what a development team is producing. They translate an    abstract product idea into a set of tangible requirements.

### Product owner (PO)
  - Holds responsibility for a product vision and evolution.
  - Makes sure the final product meets customer requirements.

  PO is holding more responsibility for a product’s success than any other development team member, a product owner is a decision-maker. Balancing both business needs and market trends, they define a business strategy, shape up the product vision, make sure it satisfies customer needs, and manage a product backlog. 

  
### Project manager (PM)
  - Makes sure a product or its part is delivered on time and within budget.
  - Manages and motivates the software development team.

  Project manager is responsible for distributing tasks across team members, planning work activities, and updating project status.

In Agile projects where the focus is on self-management, transparency, and shared ownership, a PM sets up the vision of a product, maintains transparency, fosters communication, searches for improvements in the development process, and makes sure a team delivers more value with each iteration.
 


### UI/UX designer
  - Transforms a product vision into user-friendly designs.
  - Creates user journeys for the best user experience and highest conversion rates.

There are two aspects to the product design process—user interface (UI) and user experience (UX) design.

A UI designer devises intuitive, easy-to-use, and eye-pleasing interfaces for a product, while the UX part stands for thinking out an entire journey of a user’s interaction with a product. A UX designer is thus involved in such activities as user research, persona development, information architecture design, wireframing, prototyping, and more.


### Software architect
  - Designs a high-level software architecture.
  - Selects appropriate tools and platforms to implement the product vision.
  - Sets up code quality standards and performs code reviews.

An architect is an expert-level software engineer who makes executive software design decisions on behalf of an app development team. 

A software architect decides which services and databases should communicate together, how integrations should work, and how to ensure that the product is secure and stable.


### Software developer
  - Engineers and stabilizes the product.
  - Solves any technical problems emerging during the development lifecycle.

A software developer does the actual job and codes an application. And just like an app features a front end and a back end, there are front-end and back-end developers.

### Quality assurance (QA) engineer
  - Makes sure an application performs according to requirements.
  - Spots functional and non-functional defects.

  The job of a quality assurance engineer is to verify whether an application meets the requirements—both functional and non-functional. Functional requirements define what an application should do, while non-functional requirements specify how it should do that. To verify both, QA specialists run various checks, followed by analyzing the test results and reporting on the application quality.


### Test automation engineer
  - Designs a test automation ecosystem.
  - Writes and maintains test scripts for automated testing.

  A test automation engineer is there to help you test faster and better. To enable that, they develop test automation scripts—small programs that provide reliable and continuous feedback on application quality without any human involvement.


### DevOps engineer
  - Facilitates cooperation between development and operations teams.
  - Builds continuous integration and continuous delivery (CI/CD) pipelines for faster delivery.

  DevOps engineers serve as a link between the two teams, unifying and automating the software delivery process and helping strike a balance between introducing changes quickly and keeping an application stable. Working together with software developers, system administrators, and operational staff, DevOps engineers oversee and facilitate code releases on a CI/CD basis.

# Technology Stack

  ## Django

    Django a web framework used for building RESTful APIs.
  
  ## PostgreSQL
  
    PostgreSQL a powerful relational database used for data storage.

  
  ## GraphQL
    
    GraphQL offers a flexible and efficient query mechanism for interacting with the backend.


# Database Design


The database is designed to capture the essential relationships between users, properties, bookings, reviews, and payments.  

### Key Entities and Fields 

1. **Users**
   - `id` (Primary Key)
   - `name`
   - `email` (unique)
   - `password_hash`
   - `role` (guest, host, admin)

   **Relationships:**  
   - A user can list multiple properties.  
   - A user can make multiple bookings.  
   - A user can leave multiple reviews.  

---

2. **Properties**

    - `id` (Primary Key)
    - `user`_id (Foreign Key -> Users)
    - `title`
    - `description`
    - `location`
    - `price_per_night`
  
   **Relationship:**
   - A property belongs to one host (user).
   - A property can have many bookings.
   - A property can have many reviews.

---


3. **Bookings**

    - `id` (Primary Key)
    - `property_id` (Foreign Key -> Properties)
    - `user_id` (Foregin Key -> Users)
    - `start_date`
    - `end_date`
    - `status` (pending, confirmed, canclled)

   **Relationships:**
    - A booking belong to one property.
    - A booking belong to one user/guest.
    - a booking is linked to one payment.
      
---

4. **Payments**

    - `id` (Primary Key)
    - `booking_id` (Foreign Key -> Bookings)
    - `amount`
    - `payment_method` (card, paystack, Paypal, etc.)
    - `status` (successful, failed, pending, refunded)

  **Relationships:**
  - A payment belong to one booking.

---

5. **Reviews**

    - `id` (Primary Key)
    - `property_id` (Foreign Key -> Properties)
    - `user_id` (Foreign Key -> Users)
    - `rating` (1-5)
    - `comment`
  
   **Relationships:*
   - A review belong to one property.
   - A review is created by one user.
  
---

### Entity Relationships Summary
- A **User** can be both a guest and a host.
- A **User (host)** can create multiple **Properties**.
- A **User (guest)** can make multiple **Bookings**.
- A **Property** can have many **Bookings** and **Reviews**.
- A **Booking** is tied to one **Property**, one **User**, and one **Paymeny**,
- A **Review** is tied to one **Property** and one **User**.

---

## Feature Breakdown

User Authentication
Endpoints: /users/, /users/{user_id}/
Features: Register new users, authenticate, and manage user profiles.

Property Management
Endpoints: /properties/, /properties/{property_id}/
Features: Create, update, retrieve, and delete property listings.
4. Booking System
Endpoints: /bookings/, /bookings/{booking_id}/
Features: Make, update, and manage bookings, including check-in and check-out details.
5. Payment Processing
Endpoints: /payments/
Features: Handle payment transactions related to bookings.
6. Review System
Endpoints: /reviews/, /reviews/{review_id}/
Features: Post and manage reviews for properties
