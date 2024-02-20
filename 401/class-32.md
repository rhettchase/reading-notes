# Class 32 Reading Notes: Permissions & Postgresql

sources: links below, chatGPT

- [DRF Permissions](https://www.django-rest-framework.org/api-guide/permissions/)
- [Review SQL Prework](https://codefellows.github.io/common_curriculum/prework/SQL)
- [Classy Django REST](http://www.cdrf.co/)
- [DRF Generic Views](https://www.django-rest-framework.org/api-guide/generic-views/)

## Reading Questions

## What are the key components and purpose of Django Rest Framework (DRF) permissions, and how do they help in securing an API?

Django Rest Framework (DRF) permissions play a crucial role in securing APIs by determining whether a request should be granted or denied access. These permissions work together with authentication and throttling to ensure that only authorized users can access or modify resources. Here's an overview of the key components, purpose, and how they help in securing an API:

### Key Components of DRF Permissions

1. **Permission Classes:** Permissions in DRF are defined as a list of permission classes. These classes encapsulate the logic to decide whether a request should be allowed or denied. DRF includes several built-in permission classes like `IsAuthenticated`, `IsAdminUser`, `IsAuthenticatedOrReadOnly`, and others that can be used to quickly apply common access control patterns.

2. **View-Level Permissions:** These permissions are checked before running the main body of the view. They typically use the authentication information from `request.user` and `request.auth` to determine if the request should be permitted.

3. **Object-Level Permissions:** Object-level permissions allow for fine-grained control over access to specific objects (e.g., a database model instance). These permissions are checked when accessing individual items, usually via the `.get_object()` method in class-based views or explicitly in custom views.

4. **Custom Permissions:** DRF allows the creation of custom permission classes. By subclassing `BasePermission` and overriding the `.has_permission()` and/or `.has_object_permission()` methods, developers can implement their own access control logic.

### Purpose of DRF Permissions

The primary purpose of DRF permissions is to ensure that only authorized users can access or modify API resources. This is achieved by:

- **Protecting Views:** By determining who can access different parts of the API, permissions protect views from unauthorized access.
- **Fine-grained Access Control:** Through object-level permissions, DRF enables fine-grained access control, allowing or denying access to specific objects based on the requestor's privileges.
- **Customizable Security Policies:** Custom permission classes enable developers to define complex security policies that match the specific requirements of their application.

### How DRF Permissions Secure an API

1. **Authentication and Authorization:** Permissions work closely with authentication by using information about the authenticated user (and their token/session) to make authorization decisions.
2. **Prevent Unauthorized Access:** By checking permissions at the very start of the view, DRF prevents any part of the view from running if the request does not have the required permissions, thereby preventing unauthorized access.
3. **Granular Access Control:** By allowing both view-level and object-level permissions, DRF enables both coarse-grained and fine-grained access control. This ensures that users can only access or modify resources that they are explicitly allowed to.
4. **Clear Response Codes:** When permission checks fail, DRF returns clear HTTP response codes (403 Forbidden or 401 Unauthorized) along with appropriate headers, informing clients about the nature of the access denial.
5. **Security Best Practices:** By encouraging the use of permission classes and providing a framework for defining custom permissions, DRF promotes the adoption of security best practices in API development.
## In SQL, what is the purpose of the SELECT statement, and how would you use it to retrieve all columns from a table called ‘employees’?

The `SELECT` statement in SQL is used to query or retrieve data from one or more tables in a database. It allows you to specify exactly which data you want to fetch, which can include a wide range of selection criteria, from retrieving all columns and rows from a single table to selecting specific columns based on complex conditions across multiple tables.

### Purpose of the SELECT Statement

- **Retrieve Data:** The primary purpose of the `SELECT` statement is to retrieve data stored in the database tables.
- **Specify Columns:** It allows you to specify the columns you want to retrieve. You can select all columns or specify individual column names.
- **Filter Rows:** With the `WHERE` clause, you can filter rows based on specific conditions, allowing you to retrieve only those rows that match your criteria.
- **Aggregate Data:** It can be used with aggregate functions (like `COUNT`, `SUM`, `AVG`, etc.) to perform calculations on numeric data.
- **Join Tables:** The `SELECT` statement can combine data from two or more tables using JOIN operations based on related columns between those tables.
- **Order and Group Results:** It allows for sorting (`ORDER BY`) and grouping (`GROUP BY`) of the returned data, enabling more organized and meaningful presentations of the results.
- **Limit Results:** You can limit the number of rows returned for large datasets using `LIMIT` or pagination clauses (specific syntax can vary by SQL dialect).

### Retrieving All Columns from a Table

To retrieve all columns from a table called `employees`, you would use the `SELECT` statement followed by an asterisk (`*`) as a shorthand to indicate that you want all columns. The basic syntax is as follows:

```sql
SELECT * FROM employees;
```

Here, `SELECT *` tells the database that you want to select all columns, and `FROM employees` specifies that you want this data from the table named `employees`. When executed, this statement will return every column and every row from the `employees` table, making it a straightforward way to query the entire contents of a table.

This command is particularly useful for quick data inspection or when you need all the information the table provides without needing to filter or specify certain columns. However, for larger tables or in production environments, it's generally recommended to specify only the columns you need to minimize data transfer and improve query performance.
    
## Explain the role of DRF Generic Views and provide examples of their usage in building a RESTful API?

Django Rest Framework (DRF) Generic Views are a powerful feature that simplifies the development of RESTful APIs by abstracting common patterns into reusable classes. These views handle many of the repetitive tasks involved in creating API endpoints, such as parsing request data, serializing responses, and performing CRUD (Create, Read, Update, Delete) operations on a database model. By leveraging generic views, developers can build robust APIs with less code, improving development speed and maintainability.

### Role of DRF Generic Views

1. **DRY (Don't Repeat Yourself) Principle:** Generic views encourage code reuse, significantly reducing the amount of code needed to create standard API endpoints for basic CRUD operations.

2. **Consistency:** They provide a consistent approach to handling HTTP requests, which helps in maintaining a clean and understandable codebase.

3. **Built-in Functionality:** Generic views come with built-in functionality for query handling, pagination, and serialization, making it easier to implement common API features.

4. **Customization:** While generic views cover many use cases out of the box, they can also be extended and customized to suit specific needs, offering flexibility.

5. **Integration with Serializers:** Generic views are designed to work seamlessly with DRF serializers, automating the conversion between complex data types and Python primitives for JSON/XML rendering.

### Examples of DRF Generic Views Usage

#### ListAPIView and RetrieveAPIView

These views are used for read-only endpoints to represent a collection of model instances and to retrieve a single model instance, respectively.

```python
from django.contrib.auth.models import User
from rest_framework.generics import ListAPIView, RetrieveAPIView
from .serializers import UserSerializer

class UserListView(ListAPIView):
    queryset = User.objects.all()
    serializer_class = UserSerializer

class UserDetailView(RetrieveAPIView):
    queryset = User.objects.all()
    serializer_class = UserSerializer
```

#### CreateAPIView and UpdateAPIView

These views handle the creation and update of model instances.

```python
from rest_framework.generics import CreateAPIView, UpdateAPIView

class UserCreateView(CreateAPIView):
    queryset = User.objects.all()
    serializer_class = UserSerializer

class UserUpdateView(UpdateAPIView):
    queryset = User.objects.all()
    serializer_class = UserSerializer
```

#### DestroyAPIView

This view handles the deletion of a model instance.

```python
from rest_framework.generics import DestroyAPIView

class UserDeleteView(DestroyAPIView):
    queryset = User.objects.all()
    serializer_class = UserSerializer
```

#### GenericAPIView with Mixins

For more customized behavior, `GenericAPIView` can be combined with mixins to provide specific functionalities like listing and creating resources.

```python
from rest_framework import mixins
from rest_framework.generics import GenericAPIView

class UserListCreateView(mixins.ListModelMixin, mixins.CreateModelMixin, GenericAPIView):
    queryset = User.objects.all()
    serializer_class = UserSerializer

    def get(self, request, *args, **kwargs):
        return self.list(request, *args, **kwargs)

    def post(self, request, *args, **kwargs):
        return self.create(request, *args, **kwargs)
```