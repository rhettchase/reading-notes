# Class 29 Reading Notes: Django Custom User

sources: links below, chatGPT

- [Django Custum User Model](https://learndjango.com/tutorials/django-custom-user-model)
- [DjangoX](https://github.com/wsvincent/djangox)
- [Creating a Custom User Model](https://www.youtube.com/watch?v=eCeRC7E8Z7Y&t=59s) (video)
- [Abstract User, User Profile and Signals in Django](https://www.youtube.com/watch?v=EudKs1HPUfE) (video)
- [Substituting a custom User model](https://docs.djangoproject.com/en/3.0/topics/auth/customizing/#auth-custom-user)

## What are the key benefits of using a Django Custom User Model, and how does it differ from the default Django User Model?

### Benefits

- **Customization and Flexibility**: Enables defining custom fields and authentication mechanisms, like using email as the primary identifier instead of a username, tailored to your application's specific needs.
- **Future-Proofing**: Makes adapting to future requirements easier without significant refactoring, recommended for all new projects to avoid potential challenges later.
- **Enhanced Security**: Allows for the implementation of additional security measures, such as complex password policies or two-factor authentication, tailored to the application's needs.
- **Seamless Integration**: Facilitates easier integration with third-party services by accommodating relevant data more efficiently in the user model structure.
- **Simplified Migrations and Upgrades**: Avoids complex migrations and database restructuring when changing user-related functionalities, ensuring smoother future modifications.

### Differences from the Default Django User Model

- **Fields and Behaviors**: The default Django User Model comes with a predefined set of fields (username, first name, last name, email, password) and behaviors (methods for setting password, checking permissions, etc.). A custom user model allows you to define your own fields and methods, giving you control over what information is stored and how it is handled.
- **Authentication Identifier**: The default model uses the username as the unique identifier for authentication purposes. When you create a custom user model, you can choose a different field, such as an email address, as the unique identifier.
- **Migrations and Upgrades**: Changing from the default user model to a custom one in an existing project can be complex and requires careful database migrations. Starting with a custom user model from the beginning of the project eliminates this issue and makes future modifications smoother.
- **Administration Interface**: The Django admin interface will reflect the fields and behaviors of your custom model, which may differ significantly from the default setup. This means you can tailor the admin interface to the needs of your team, improving efficiency and usability.
    
## Explain the process of creating and implementing a Custom User Model in Django, including the necessary changes to settings.py and the required model fields

Creating and implementing a Custom User Model in Django involves several steps, from defining the model itself to adjusting your project's settings to acknowledge this custom model. Below is a detailed guide through the process:

### Step 1: Define the Custom User Model

First, you need to create a custom user model by extending `AbstractBaseUser` and, optionally, `PermissionsMixin` if you need Django's built-in permissions framework. This is done in your app's `models.py` file.

```python
from django.contrib.auth.models import AbstractBaseUser, BaseUserManager, PermissionsMixin
from django.db import models

class MyUserManager(BaseUserManager):
    def create_user(self, email, password=None, **extra_fields):
        if not email:
            raise ValueError('The Email field must be set')
        email = self.normalize_email(email)
        user = self.model(email=email, **extra_fields)
        user.set_password(password)
        user.save(using=self._db)
        return user

    def create_superuser(self, email, password=None, **extra_fields):
        extra_fields.setdefault('is_staff', True)
        extra_fields.setdefault('is_superuser', True)

        return self.create_user(email, password, **extra_fields)

class MyUser(AbstractBaseUser, PermissionsMixin):
    email = models.EmailField(unique=True)
    is_active = models.BooleanField(default=True)
    is_staff = models.BooleanField(default=False)
    is_admin = models.BooleanField(default=False)

    objects = MyUserManager()

    USERNAME_FIELD = 'email' # how user logins
    REQUIRED_FIELDS = []

    def __str__(self):
        return self.email

	def has_perm(self, perm, obj=None):
		return self.is_admin
```

In this example, `MyUser` is the custom user model with `email` as the primary unique identifier. `MyUserManager` is a custom manager that includes helper methods to create users and superusers.

### Step 2: Update settings.py

After defining your custom user model, you must inform Django to use it as the default user model. This is done by adding or updating the `AUTH_USER_MODEL` setting in your project's `settings.py` file.

```python
AUTH_USER_MODEL = 'your_app_name.MyUser'
```

Replace `'your_app_name'` with the name of the app where you defined your custom user model.

### Step 3: Migrations

Once the custom user model is defined and `settings.py` is updated, you need to create and apply migrations to reflect these changes in your database.

```
python manage.py makemigrations your_app_name
python manage.py migrate
```

### Step 4: Use the Custom User Model

With the custom user model set up, you can now use it throughout your Django project. For instance, when creating user-related forms, you should use `get_user_model()` instead of directly referring to the `User` model.

```python
from django.contrib.auth import get_user_model

User = get_user_model()
```

### Step 5: Admin Integration

If you want to use the Django admin to manage users, you'll need to define a custom `UserAdmin` class for your custom user model. This involves extending `admin.ModelAdmin` or Django's default `UserAdmin` class and registering it along with your custom user model.

```python
from django.contrib import admin
from django.contrib.auth.admin import UserAdmin as BaseUserAdmin
from .models import MyUser

class UserAdmin(BaseUserAdmin):
    # Define admin model here

admin.site.register(MyUser, UserAdmin)
```

### Required Model Fields

At minimum, your custom user model should define the following:

- A unique identifier field (`email` in the example).
- `is_active` field to indicate whether the user's account is active.
- `is_staff` field to indicate whether the user can access the Django admin (if you're using Django's admin).
- A manager that extends `BaseUserManager`, implementing `create_user` and `create_superuser` methods.

Implementing a custom user model in Django is a powerful way to tailor authentication and user management to your project's needs, ensuring flexibility and scalability as your application grows.
    
## What is DjangoX and how does it complement or extend the functionality of Django? Provide an example use case for incorporating DjangoX in a project

DjangoX is an open-source Django project template or boilerplate that aims to extend the basic Django framework by providing a more comprehensive starting point for new projects. It's not an extension of Django's core functionalities per se but rather a pre-configured setup that includes additional tools, libraries, and configurations that are commonly used in Django projects. This setup helps developers kickstart their projects more efficiently, reducing the time spent on initial configuration.

### How DjangoX Complements or Extends Django

DjangoX complements Django by including:

- **Pre-configured User Model**: It often comes with a custom user model set up out of the box, following best practices and saving you from the hassle of implementing one from scratch.
- **Authentication Flow**: Includes pre-built user authentication flows, such as signup, login, logout, and password change/reset functionalities.
- **Third-party Libraries**: Bundled with useful Django extensions and third-party libraries for common functionalities, such as environment variable management, better user authentication, and more sophisticated settings configurations.
- **Docker Support**: Ready-to-use Docker configurations for containerized development and deployment.
- **Pre-built Templates**: Comes with basic templates for common pages (like home, about, user authentication pages) styled with CSS frameworks like Bootstrap for a head start on the frontend.
- **Development Tools**: Configured with tools for code formatting, linting, and other best practices to maintain code quality from the start.

### Example Use Case

Suppose you're tasked with building a new web application that requires user authentication, a blog module, and API endpoints for mobile apps. Starting from scratch with Django would require setting up a custom user model, configuring the authentication flow, creating the blog models, views, and templates, and then integrating Django Rest Framework for the APIs.

With DjangoX, you can significantly accelerate this process. Here's how:

- **User Authentication**: DjangoX comes with a pre-configured user model and authentication flows, including social media logins if needed, allowing you to focus on the unique aspects of your project right away.
- **Blog Module**: You can quickly scaffold the blog models, views, and templates based on the project's structure and styling conventions provided by DjangoX, ensuring consistency.
- **APIs**: Leverage the included Django Rest Framework setup to create API endpoints for your blog module, benefiting from the pre-configured settings and authentication mechanisms.
