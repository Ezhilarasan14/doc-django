# Application Layer

## Time zone

<p>
In Django, the timezone module is part of the django.utils package and provides utilities for working with time zones. It uses the pytz library internally to handle time zone conversions. Here's how you can work with time zones in a Django project:

</p>

### 1. Enable Time Zone Support in Settings:
<p>
Ensure that the USE_TZ setting is set to True in your Django project's settings.py file. This enables time zone support in your project.
</p>

```
LANGUAGE_CODE = 'en-us'

TIME_ZONE = 'UTC'

USE_TZ = True
```

### 2. Querying with Time Zones

<p>
When querying the database, ensure that you use timezone.now() and timezone.timedelta for comparisons.
</p>

```
from django.utils import timezone
from myapp.models import MyModel

now = timezone.now()
recent_objects = MyModel.objects.filter(created_at__gte=now - timezone.timedelta(days=7))
```

Custom time zone reference : https://pypi.org/project/pytz/

Django time zone reference : https://docs.djangoproject.com/en/5.0/topics/i18n/timezones/