# Class-11 Reading Notes: CRUD

source: [Status Codes Based On REST Methods](https://www.moesif.com/blog/technical/api-design/Which-HTTP-Status-Code-To-Use-For-Every-CRUD-App/), chatGPT

1. **Status Code Groups:**
    - **100's (1xx):** Informational codes. They indicate that the request was received, continuing process.
    - **200's (2xx):** Success codes. They indicate that the request was successful or received, understood, and accepted.
    - **300's (3xx):** Redirection codes. They indicate that further action needs to be taken to fulfill the request.
    - **400's (4xx):** Client error codes. They indicate that the client seems to have made an error in the request.
    - **500's (5xx):** Server error codes. They indicate that the server failed to fulfill a valid request.
2. **Status Code 202:**
    - **Accepted:** The request has been accepted for processing, but the processing has not been completed. This status is often used for asynchronous processing.
3. **Status Code 308:**
    - **Permanent Redirect:** This status code indicates that the requested resource has been permanently moved to another location, and the client should use the new URL for all future requests.
4. **Code for Update without Data:**
    - **204 No Content:** The server successfully processed the request but does not need to return any content. Useful in scenarios where an update operation is performed, and the client doesn't need new data.
5. **Code for Resource No Longer Exists:**
    - **410 Gone:** The requested resource is no longer available at the server, and no forwarding address is known. It is a permanent condition.
6. **'Forbidden' Status Code:**
    - **403 Forbidden:** The server understood the request, but it refuses to authorize it. This status is similar to 401 (Unauthorized), but indicates that the client must authenticate itself to get permission.

## REST API

[Build A REST API With Node.js, Express, & MongoDB - Quick](https://www.youtube.com/channel/UCFbNIlppjAuEX4znoulh0Cw) - First 20 minutes, chatGPT

1. **Why use .env for MongoDB connection string?**
    
    - Security: Putting sensitive information, such as database connection strings, in a `.env` file allows you to keep this information confidential. The `.env` file is typically not committed to version control, reducing the risk of exposing sensitive data.
    - Configurability: Using environment variables allows you to easily switch between different databases (e.g., development, testing, production) without modifying the code. Each environment can have its own `.env` file with appropriate configurations.
2. **What is middleware?**
    
    - Middleware functions in web development are functions that have access to the request object (`req`), the response object (`res`), and the next middleware function in the application's request-response cycle. Middleware functions can perform tasks such as modifying the request or response, ending the request-response cycle, and calling the next middleware in the stack.
3. **What does `app.use(express.json())` do?**
    
    - In an Express.js application, `app.use(express.json())` is middleware that parses incoming JSON payloads. It adds a middleware function that parses the incoming request body, assuming it is in JSON format, and makes the parsed data available in `req.body` for further processing.
4. **What does `/:id` mean in a route?**
    
    - In a route definition, `/:id` represents a route parameter. It's a placeholder for a dynamic value that will be part of the URL. For example, in the route `/users/:id`, the `:id` portion can be replaced with a specific user ID when making requests to that route, like `/users/123`.
5. **Difference between PUT and PATCH:**
    
    - **PUT:** Typically used to update or create a resource. It requires sending the entire representation of the resource, even if only a small part is being updated. It replaces the existing resource.
    - **PATCH:** Used to apply partial modifications to a resource. It only sends the data that needs to be updated, making it more efficient when updating a small portion of the resource. It does not replace the existing resource but modifies it.
6. **How to make a default value in a schema?**
    
    - In a MongoDB/Mongoose schema, you can set default values for fields using the `default` property. For example:
    
```js
const userSchema = new Schema({
  name: { type: String, default: 'John Doe' },
  age: { type: Number, default: 25 },
});

```

1. **What does a `500` error status code mean?**
    
    - A `500` status code is a server error response. It indicates that an unexpected condition occurred on the server, and the server is unable to fulfill the request. This is a generic error message, and the actual cause of the error should be investigated.
2. **Difference between a status `200` and a status `201`:**
    
    - **`200 OK`:** It indicates that the request was successful. This status is typically returned for successful GET requests or successful operations that don't result in a new resource being created.
    - **`201 Created`:** It indicates that the request has been fulfilled, resulting in the creation of a new resource. It is often used in response to successful POST requests where a new resource is created as a result of the request. The URI of the newly created resource is usually included in the response.