# Class-08 Reading Notes: APIs

source: [API Design Best Practices](https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design), chatGPT

1. **What does REST stand for?**

- REST stands for Representational State Transfer.

1. **REST APIs are designed around a ____?**
    
    - REST APIs are designed around a stateless client-server architecture.
    
1. **What is an identifier of a resource? Give an example.**
    
    - An identifier of a resource in REST is typically a URI (Uniform Resource Identifier). For example, the URI "[https://api.example.com/users/123](https://api.example.com/users/123)" identifies the resource of the user with the ID 123.
    
1. **What are the most common HTTP verbs?**
    
    - The most common HTTP verbs used in REST are:
        - GET: Retrieve a resource.
        - POST: Create a new resource.
        - PUT: Update an existing resource.
        - DELETE: Delete a resource.
        
1. **What should the URIs be based on?**
    
    - URIs (Uniform Resource Identifiers) should be based on nouns, representing resources. They should identify the resource the API is working with.
    
1. **Give an example of a good URI.**
    
    - A good URI is descriptive and represents the resource it points to. For example:
        - Good URI: "[https://api.example.com/products/electronics](https://api.example.com/products/electronics)"
        
1. **What does it mean to have a ‘chatty’ web API? Is this a good or a bad thing?**
    
    - A 'chatty' web API refers to an API that requires a large number of requests to perform a single operation, leading to increased network traffic and potential performance issues. It is generally considered a bad thing as it can impact efficiency.
    
1. **What status code does a successful `GET` request return?**
    - A successful `GET` request returns a status code of 200 OK.
    
1. **What status code does an unsuccessful `GET` request return?**
    
    - An unsuccessful `GET` request can return various status codes, but common ones include 404 Not Found for a resource that doesn't exist and 403 Forbidden for unauthorized access.
    
1. **What status code does a successful `POST` request return?**
    
    - A successful `POST` request returns a status code of 201 Created or 200 OK.
    
1. **What status code does a successful `DELETE` request return?**
    
    - A successful `DELETE` request returns a status code of 204 No Content.