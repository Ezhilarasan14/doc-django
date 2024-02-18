#Queuing Layer

##Celery Settings and Rabbitmq

<p>
Configure Django to Use Celery

Update your Django settings to include Celery settings. In your settings.py file, add or modify the following:
</p>

```
settings.py

RABBIT_URL = conf('RABBIT_URL')

# Celery Configuration Options
CELERY_TIMEZONE = "Asia/Kolkata"
CELERY_TASK_TRACK_STARTED = True
CELERY_TASK_TIME_LIMIT = 3600
# CELERY_BROKER_URL = os.environ.get('BROKER_URL', )
CELERY_BROKER_URL = os.environ.get("CELERY_BROKER", RABBIT_URL)
CELERY_RESULT_BACKEND = os.environ.get("CELERY_BROKER", RABBIT_URL)

CELERY_TASK_SOFT_TIME_LIMIT = 3200
CELERY_RESULT_BACKEND = 'django-db'
CELERY_CACHE_BACKEND = 'django-cache'
CELERY_ACCEPT_CONTENT = ['application/json']
CELERY_TASK_SERIALIZER = 'json'
CELERY_RESULT_SERIALIZER = 'json'
CELERYD_MAX_TASKS_PER_CHILD=1
CELERY_RESULT_EXTENDED = True
CELERY_ACKS_LATE = True
```

<p>
Make sure to replace the CELERY_BROKER_URL and CELERY_RESULT_BACKEND with your desired message broker (like Redis, RabbitMQ).
</p>