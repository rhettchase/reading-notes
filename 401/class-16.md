# Class 16 Readings Notes: Serverless Functions

sources: links below, chatGPT

- [What is Serverless Computing?](https://www.ibm.com/cloud/learn/serverless)
- [venv - Creation of Virtual Environments](https://docs.python.org/3/library/venv.html)
- [Vercel - Get Started](https://vercel.com/docs/get-started)
- [http.server](https://pymotw.com/3/http.server/index.html)
- [Requests](https://requests.readthedocs.io/en/latest/)
- [Python & APIs](https://realpython.com/python-api/)
- [What is Serverless?](https://www.youtube.com/watch?v=vxJobGtqKVM) (video)
- [Serverless Functions](https://vercel.com/docs/concepts/functions/serverless-functions)
- [Effective Python Environment](https://realpython.com/effective-python-environment/)

## What are the key characteristics of serverless computing, and how does it differ from traditional server-based architectures?

Serverless computing has several key characteristics that distinguish it from traditional server-based architectures:

1. **Abstracted Infrastructure**: In serverless computing, developers are not responsible for managing or provisioning servers. This task is entirely handled by the cloud service provider. The underlying infrastructure is 'invisible' to developers, allowing them to focus solely on writing and deploying code.

2. **Auto-Scaling**: Serverless architectures automatically scale resources up or down depending on demand. This includes scaling to zero when the service is not in use, which is not typically feasible in traditional architectures.

3. **Billing Model**: With serverless, billing is based on actual usage, meaning you only pay for the compute time and resources used when the code is executing. This contrasts with traditional models where you may pay for idle resources.

4. **Fast Provisioning and Deployment**: Serverless platforms allow for rapid deployment of applications. Provisioning of resources is measured in milliseconds, significantly faster than traditional models.

5. **Maintenance and Administration**: In serverless environments, the cloud provider manages maintenance tasks such as OS updates, security, and capacity planning. This reduces the administrative burden on developers compared to traditional architectures where such tasks are significant.

6. **Statelessness**: Serverless architectures are inherently stateless, with each function execution being independent. Persistent state is usually handled by external services. This differs from server-based models where applications can maintain state over time.

7. **High Availability and Disaster Recovery**: These are typically inherent in serverless platforms without additional cost or effort. Traditional architectures require explicit planning and additional resources for HA and DR.

8. **Resource Utilization**: Serverless offers high efficiency as there's no idle capacity; resources are used only when the code executes. Traditional server-based models usually have some degree of idle capacity.

9. **Diverse Runtime Environment**: Serverless computing supports multiple languages and frameworks, providing a polyglot environment that accommodates various development preferences.

10. **Simplified DevOps**: The serverless model simplifies many aspects of the software deployment lifecycle, reducing the time and effort required for integration, testing, and deployment.

**Differences from Traditional Server-Based Architectures**:

- **Infrastructure Management**: In traditional architectures, developers or IT teams manage servers, including provisioning, scaling, and maintenance. Serverless abstracts this away entirely.
  
- **Scalability**: Traditional architectures often require manual scaling and do not scale to zero, whereas serverless architectures do this automatically and instantaneously.

- **Cost Model**: Traditional server-based models often involve paying for provisioned resources regardless of usage, while serverless models charge based on actual usage.

- **Operational Overhead**: Serverless reduces the operational burden significantly compared to traditional models which require ongoing server maintenance and administration.

- **Development Focus**: Serverless allows developers to concentrate more on writing code and business logic, without worrying about the underlying infrastructure.

## How can one get started with Vercel, and what are the main steps involved in deploying a serverless function using Vercel?

- **Sign Up and Set Up**:
    - Create an account on the [Vercel website](https://vercel.com/).
    - Install Vercel Command Line Interface (CLI) using npm: `npm i -g vercel`.
    - Log in to Vercel via CLI: `vercel login`.
- **Prepare Your Project**:
    - Create or use an existing project. For serverless functions, place your code in the `/api` directory.
    - (Optional) Configure deployment settings in `vercel.json`.
- **Develop Serverless Function**:
    - Write your serverless function code, e.g., a Node.js function in `/api/hello.js`.
    - Test locally using `vercel dev`.
- **Deploy**:
    - Run `vercel` in the project's root directory to deploy.
    - Link your project to a Vercel project when prompted.
    - After deployment, a URL is provided to view your function.
    
##  What are APIs, and how can they be utilized in Python applications to access and manipulate data from external sources?

- **Definition of APIs**:
  - APIs (Application Programming Interfaces) are sets of protocols, routines, and tools for building software applications.
  - They define the methods and data formats that applications can use to communicate with each other, especially over a network.

- **Utilization in Python Applications**:
  - **Data Access**: APIs enable Python applications to interact with external services or resources, such as databases, web services, or other software products.
  - **Sending Requests**: Python can use libraries like `requests` to send HTTP requests to API endpoints, allowing it to retrieve or send data.
  - **Data Manipulation**: Once data is received from an API, Python can manipulate it using its powerful data processing capabilities, such as with libraries like `pandas` for data analysis.
  - **Integration with Services**: APIs allow Python applications to integrate with third-party services and platforms, like social media, cloud services, or payment gateways.
  - **Automation**: Automate tasks by programmatically interacting with APIs, for instance, auto-generating reports, triggering emails, or updating records in a CRM system.
  - **Data Formats**: Python can handle various data formats provided by APIs, such as JSON, XML, or CSV, and 

## What is the Requests library in Python, and how can it be used to interact with APIs by sending HTTP requests? Can you provide an example of a basic GET request using the Requests library?

The `requests` library in Python is a popular and user-friendly HTTP library used for sending all types of HTTP requests. It simplifies the process of working with APIs by managing the complexities of making HTTP requests and handling responses. Here's an overview of its functionality and an example of a basic GET request:

### What is the Requests Library?

- **Purpose**: It's used to send HTTP requests in Python. It's known for its simplicity and ease of use.
- **HTTP Methods**: Supports all HTTP methods including GET, POST, PUT, DELETE, HEAD, etc.
- **Handling Responses**: Easily handles response data, including text, JSON, and binary data.
- **Parameters and Authentication**: Supports URL parameters, headers, and various forms of authentication.
- **Session Objects**: Can use sessions to persist certain parameters across requests.

### Using Requests to Interact with APIs:

- **Send Requests**: Send requests to API endpoints to perform actions (retrieve data, submit data, etc.).
- **Parse Responses**: Process and parse the data returned from the API, often in JSON format.
- **Error Handling**: Check for errors in responses and handle them accordingly.
- **Authentication**: Include authentication tokens or credentials when necessary.

### Example: Basic GET Request

Here's a basic example of using the Requests library to perform a GET request:

```python
import requests

# The URL of the API endpoint
url = "http://api.example.com/data"

# Sending a GET request to the URL
response = requests.get(url)

# Checking if the request was successful
if response.status_code == 200:
    # Parsing the response data (assuming JSON)
    data = response.json()
    print("Data retrieved:", data)
else:
    print("Failed to retrieve data. Status code:", response.status_code)
```

In this example:
- We import the `requests` module.
- Define a URL for the API endpoint.
- Use `requests.get()` to send a GET request to that URL.
- Check the response's status code to ensure the request was successful.
- If successful, we parse the JSON response and print it out. If not, we handle the failure.

This simple pattern can be extended and customized for different types of requests and APIs, including adding headers, query parameters, or handling more complex data structures.