# Integration Layer

## Email Template

<p>
1. Create an Email Template:

First, create an HTML file for your email template. You can store your email templates in the templates directory of your Django app. For example, create a file like email_template.html.
</p>


```
<!DOCTYPE html>
<html>
<body>
    <p>Hello {{ recipient_name }},</p>
    <p>This is the content of your email.</p>
</body>
</html>
</code>
```

<p>
2. Load and Render the Template in Your Django View:

In your Django view, load and render the email template using the render_to_string function.

</p>

```
from django.template.loader import render_to_string

def send_email(request):
    recipient_name = "John Doe"
    email_content = render_to_string('your_app/email_template.html', {'recipient_name': recipient_name})
```