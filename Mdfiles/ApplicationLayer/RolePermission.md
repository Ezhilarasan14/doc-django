# Application Layer

## Role and Permission

<p>
In Django, roles and permissions are used to manage access control and define what actions users are allowed to perform within a web application. Django provides a built-in authentication and authorization system that includes roles and permissions.

For digid we customized based on the application requirements:

tables used:
    1. role_action_access, 
    2. role_crncy_dtls, 
    3. role_dtls, 
    4. role_permission_dtls, 
    5. role_prod_access, 
    6. role_workflow_access


</p>

### Roles:

<p>Django does not explicitly define roles like "admin" or "manager," but rather uses the concept of groups to organize users. You can create groups and assign permissions to those groups, effectively using groups as roles. For example, you might have groups like "Admins," "Managers," and "Regular Users."

Here's how you can create groups in Django
<p>

```
from django.contrib.auth.models import Group

# Create a group
admin_group = Group.objects.create(name='Admins')

# Assign a user to a group
user.groups.add(admin_group)
```

### Permissions :

<p>
Permissions define what actions a user is allowed to perform. Django provides a set of built-in permissions such as add, change, and delete for each model. You can also define custom permissions specific to your application.

Built-in Permissions:

add: Allows adding new instances of the model.
change: Allows changing existing instances of the model.
delete: Allows deleting instances of the model.
view: Allows viewing instances of the model.

</p>

```
from django.contrib.auth.models import Permission

# Get a permission (e.g., change permission for a model)
change_permission = Permission.objects.get(codename='change_modelname')

# Assign a permission to a user or group
user.user_permissions.add(change_permission)
```