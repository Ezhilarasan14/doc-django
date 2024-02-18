# Data Access Layer

## Data Validation

<p>
Pydantic is a data validation and settings management library in Python. It is used for data validation and parsing by defining data models using Python type annotations. Pydantic is often used in web applications, APIs, and other projects where data validation and serialization/deserialization are important.

Here's a basic overview of using Pydantic:

</p>

```

from pydantic import BaseModel

class User(BaseModel):
    username: str
    email: str
    age: int



user_data = {
    "username": "john_doe",
    "email": "john@example.com",
    "age": 25,
}

user = User(**user_data)
Pydantic will validate the data against the defined model.

```


### Incorrect data

```

invalid_user_data = {
    "username": "john_doe",
    "email": "john@example.com",
    "age": "twenty-five",  # Should be an int, not a str
}

# This will raise a validation error
invalid_user = User(**invalid_user_data)

```
Pydantic will raise a validation error.
