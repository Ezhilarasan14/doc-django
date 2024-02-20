# Security Layer

## Passworld Encryption

Django, the default password hashing algorithm is pbkdf2_sha256. When you create a user or change a password, Django automatically uses this algorithm to hash the password securely. You don't need to specify the algorithm explicitly as it is the default

Algorithm :  pbkdf2_sha256


to get the hash algorithm type

```
from django.contrib.auth.hashers import make_password, check_password, identify_hasher


hashed_password = "pbkdf2_sha256$100000$kyOHnnbwxxkV$uK9PhD0rsU1vB+O1rkgZVnhTdIOen3jeY4mSplS0cJg="
hasher = identify_hasher(hashed_password)
print(hasher.algorithm) # output  : pbkdf2_sha256

```

In the one-liner for creating a new password:

```
python3 manage.py shell --command "from django.contrib.auth.hashers import make_password, check_password; print(make_password('Welcome1@', hasher='pbkdf2_sha256'))"
```

This will output the hashed password using the pbkdf2_sha256 algorithm. Remember that you should store this hashed password in your database for user authentication. When checking a password during login, you can use the check_password function:

```
# Example of checking a password during login
stored_password_hash = "pbkdf2_sha256$100000$kyOHnnbwxxkV$uK9PhD0rsU1vB+O1rkgZVnhTdIOen3jeY4mSplS0cJg="
entered_password = 'Welcome1@'

if check_password(entered_password, stored_password_hash):
    print("Password is correct!")
else:
    print("Password is incorrect.")
```