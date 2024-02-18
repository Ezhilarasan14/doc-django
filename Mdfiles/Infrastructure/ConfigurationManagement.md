#Infrastructure Layer

##Configuration management


<p>

To manage configuration settings in a Django project using a .ini file and the python-decouple library, follow these steps:

</p>

<b>
Install python-decouple:
</b>

```
pip install python-decouple
```

<b>
Create a .ini file:
</b>
<p>
Create a .ini file (e.g., config.ini) to store your configuration settings. For example:
<\p>

```
[DATABASE]
NAME=mydatabase
USER=mydatabaseuser
PASSWORD=mypassword
HOST=localhost
PORT=5432

[SECRET_KEY]
KEY=mysecretkey            
```
<b>
Use python-decouple in Django settings
</b>
<p>
Update your Django settings (settings.py) to use python-decouple to read values from the .ini file:
</p>

```
from decouple import config

database_name = config('DATABASE_NAME', default='')
secret_key = config('SECRET_KEY', default='')

# Database settings
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': config('DATABASE_NAME', default=''),
        'USER': config('DATABASE_USER', default=''),
        'PASSWORD': config('DATABASE_PASSWORD', default=''),
        'HOST': config('DATABASE_HOST', default=''),
        'PORT': config('DATABASE_PORT', default=''),
    }
}

# Secret key
SECRET_KEY = config('SECRET_KEY', default='')
```

<p>
Secure the .ini file:

Ensure that your .ini file is not exposed to the public or unauthorized users. Keep it secure, and do not include sensitive information in version control systems.

By following these steps, you can manage your Django project's configuration settings in a separate .ini file using the python-decouple library. This helps keep sensitive information separate from your code and makes it easier to manage different configurations for development, testing, and production environments.
</p>