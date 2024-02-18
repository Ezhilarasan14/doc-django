# Queuing Layer

## Celery

<p>
Celery is a distributed task queue library for Python that is commonly used with Django for handling asynchronous tasks. It allows you to offload time-consuming tasks to be executed in the background, improving the responsiveness of your web application.

Here is a basic guide on how to set up Celery with Django:
</p>

### Install Celery:
<p>
Install Celery using pip:
</p>

```
pip install celery
```

###Create a Celery Configuration File:

<p>
Create a file named celery.py in your Django project directory (next to your settings.py). This file will configure and instantiate Celery for your project.

</p>

```
# celery.py
from __future__ import absolute_import, unicode_literals
import os
from celery import Celery

# set the default Django settings module for the 'celery' program.
os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'your_project.settings')

# create a Celery instance and configure it
app = Celery('your_project')

# Load task modules from all registered Django app configs.
app.config_from_object('django.conf:settings', namespace='CELERY')

# Auto-discover tasks in all installed apps
app.autodiscover_tasks()
```