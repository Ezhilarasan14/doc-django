# Security Layer


## CSRF

Django provides built-in middleware to protect against CSRF (Cross-Site Request Forgery) attacks and includes several measures to mitigate XSS (Cross-Site Scripting) vulnerabilities.

### CSRF Protection:

Middleware:

Django includes middleware called django.middleware.csrf.CsrfViewMiddleware to protect against CSRF attacks.

To enable CSRF protection, ensure the following middleware is included in your MIDDLEWARE setting:

```
# settings.py
MIDDLEWARE = [
    # ...
    'django.middleware.csrf.CsrfViewMiddleware',
    # ...
]
```

This middleware provides protection by including a hidden CSRF token in forms and checking this token on form submissions.



## XSS

Django includes several features and practices to mitigate XSS vulnerabilities:

Django Forms:

When rendering form inputs in templates, Django forms automatically escape form data to prevent XSS vulnerabilities.

# XSS Protection:

Middleware:

Django's django.middleware.security.SecurityMiddleware includes various security features, including setting the X-Content-Type-Options header to "nosniff" to prevent browsers from interpreting files as a different MIME type, and the X-XSS-Protection header to enable the browser's XSS protection filter.

Ensure the following middleware is included in your MIDDLEWARE setting:

```
# settings.py
MIDDLEWARE = [
    # ...
    'django.middleware.security.SecurityMiddleware',
    # ...
]
```

By following these practices and utilizing the built-in security features, Django helps developers create web applications with a strong defense against CSRF attacks and XSS vulnerabilities. Always stay updated with the latest security practices and consider additional security measures based on the specific requirements of your project.



# CSRF/ XSS using django's default middleware

```
MIDDLEWARE = [
'django.middleware.security.SecurityMiddleware',
'django.middleware.csrf.CsrfViewMiddleware',
'django.middleware.clickjacking.XFrameOptionsMiddleware',
]
```
