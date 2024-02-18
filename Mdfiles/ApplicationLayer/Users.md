# Application Layer

## Default User model

<p>
In Django, the User model is part of the built-in authentication system and is used to manage user accounts. It provides fields such as username, password, email, and methods for handling user authentication. The User model is located in the django.contrib.auth.models module.

Here's a basic overview of the Django User model:

</p>

```
python manage.py createsuperuser
```

## Custom User Model

Django also allows you to create a custom user model by extending the AbstractUser class. This gives you the flexibility to add custom fields to the user model.

Here's an example of creating a custom user model:

```
from django.contrib.auth.models import AbstractUser

class CustomUser(AbstractUser):
    # Add custom fields here

# Update the AUTH_USER_MODEL setting in settings.py
AUTH_USER_MODEL = 'your_app.CustomUser'
```