# Class-13 Reading Notes: CRUD (pt 2)

## CRUD Basics

source: [CRUD Basics](https://medium.com/geekculture/crud-operations-explained-2a44096e9c88), chatGPT

1. **Which HTTP method would you use to update a record through an API?**
   The HTTP method used to update a record through an API is typically the `PUT` method. In the context provided, the article mentions using `PUT` to reschedule a playdate for Togo. The `PUT` method is commonly used for updating an existing resource on the server.
2. **Which REST methods require an ID parameter?**
   In RESTful APIs, the `PUT`, `GET`, and `DELETE` methods often require an ID parameter to specify the resource being manipulated. In the context provided, the article mentions the following:

   - `PUT` request for updating a playdate with a specified ID: `/appointments/:id`
   - `GET` request for viewing appointments: `/appointments`
   - `DELETE` request for canceling an appointment with a specified ID: `/appointments/:id`

   The use of the `:id` parameter in the routes indicates that an ID is necessary to identify the specific resource (e.g., playdate appointment) associated with the operation.

3. **What is CRUD?**
   CRUD is an acronym that stands for **Create, Read, Update, and Delete**. These four operations represent the fundamental actions that can be performed on data in a persistent storage system, such as a database. In the context of web development and APIs, CRUD is often aligned with the HTTP methods as follows:

   - **Create**: Corresponds to the HTTP `POST` method, used for adding new data.
   - **Read**: Corresponds to the HTTP `GET` method, used for retrieving data without making changes.
   - **Update**: Corresponds to the HTTP `PUT` or `PATCH` methods, used for modifying existing data.
   - **Delete**: Corresponds to the HTTP `DELETE` method, used for removing data.

## REST vs. CRUD

[Speed Coding: Building a CRUD API](https://www.youtube.com/watch?v=EzNcBhSv1Wo) (_Watch a Twitch streamer code an Express API in 20 minutes!_)

1. **What’s the relationship between REST and CRUD?**
   **REST (Representational State Transfer)** is an architectural style for designing networked applications. It defines a set of constraints and principles for building scalable and maintainable web services. **CRUD (Create, Read, Update, Delete)**, on the other hand, represents the four basic operations that can be performed on data in a persistent storage system.

   The relationship between REST and CRUD lies in the fact that RESTful APIs often align the four CRUD operations with the standard HTTP methods:

   - **Create**: Typically mapped to the HTTP `POST` method.
   - **Read**: Mapped to the HTTP `GET` method.
   - **Update**: Mapped to the HTTP `PUT` or `PATCH` methods.
   - **Delete**: Mapped to the HTTP `DELETE` method.

   RESTful APIs use these HTTP methods to perform CRUD operations on resources identified by URIs (Uniform Resource Identifiers). The principles of REST guide the design of APIs to be stateless, scalable, and easily understandable.

2. **If you had to describe the process of creating a RESTful API in 5 steps, what would they be?**
   Creating a RESTful API involves several steps, and here are five key steps in the process:

   **Step 1: Define Resources and Endpoints**

   - Identify the resources your API will expose (e.g., users, products).
   - Define the URIs (Uniform Resource Identifiers) that will represent these resources (e.g., `/users`, `/products`).

   **Step 2: Choose HTTP Methods**

   - Assign appropriate HTTP methods to CRUD operations for each resource.
   - For example, use `GET` for retrieving data, `POST` for creating new resources, `PUT` or `PATCH` for updating existing resources, and `DELETE` for removing resources.

   **Step 3: Design Data Formats**

   - Choose data formats for communication (e.g., JSON or XML).
   - Define the structure of request and response payloads.

   **Step 4: Implement CRUD Operations**

   - Implement the logic for CRUD operations based on the chosen HTTP methods.
   - Ensure that the operations adhere to the principles of idempotence and safety.

   **Step 5: Implement Authentication and Authorization**

   - Implement mechanisms for authenticating users and authorizing their access to resources.
   - Use authentication tokens, API keys, or other secure methods.
