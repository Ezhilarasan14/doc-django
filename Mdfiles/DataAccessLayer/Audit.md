# Data Access Layer

## Audit


Audit table that logs information about external IP addresses making requests, including details such as request URL, request method, response, response code, and related API, you can follow these steps. Since the details you want to log are related to incoming requests, you'll need to capture this information at the application level rather than the database level

## Step 1: Create an Audit Table in the Database

You may have already created a table for auditing in the database, capturing information like timestamp, external IP, etc.


```
# models.py
from django.db import models

class AuditLog(models.Model):
    external_ip = models.GenericIPAddressField()
    external_url = models.URLField()
    method = models.CharField(max_length=10)
    path = models.CharField(max_length=255)
    user_agent = models.TextField()
    timestamp = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return f"{self.method} {self.path} from {self.external_ip} accessing {self.external_url}"
```



## Step 2: Implement Request Logging in Your Application

In your application code (assuming you're using Python and Django), you can implement request logging middleware or decorators to capture the desired information.


```

# middlewares.py

from django.utils.deprecation import MiddlewareMixin
from .models import AuditLog

class AuditLogMiddleware(MiddlewareMixin):
    def process_request(self, request):
        # Log the request information to your database
        external_ip = request.META.get('REMOTE_ADDR')
        external_url = request.build_absolute_uri()
        AuditLog.objects.create(
            external_ip=external_ip,
            external_url=external_url,
            method=request.method,
            path=request.path,
            user_agent=request.META.get('HTTP_USER_AGENT'),
            # Add more fields as needed
        )
```

## Step 3: Update Settings

Add the updated middleware to the MIDDLEWARE setting in your settings.py file:

```
# settings.py
MIDDLEWARE = [
    # other middleware...
    'your_app.middlewares.AuditLogMiddleware',
]
```
