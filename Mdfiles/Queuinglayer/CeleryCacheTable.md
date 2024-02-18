#Queuing Layer

##Cache Table in Django

<p>
Django provides a high-level caching framework. You can use the cache framework to store and retrieve data efficiently. Here's a basic example:

</p>

```
settings.py

CACHES = {
    'default': {
        'BACKEND': 'django.core.cache.backends.db.DatabaseCache',
        'LOCATION': 'DJANGO_CELERY_PENDING_LIST',
    }
}
```
<p>
You can choose different cache backends based on your needs.
</p>