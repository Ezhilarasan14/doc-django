# Infrastructure

## Common Functionality

Python, there are several functions and patterns that are commonly reused across different projects. Here are some commonly used functions and patterns:

Generate OTP:


```
import random

def generate_otp(length=6):
    """Generate a random OTP."""
    return ''.join(random.choice('0123456789') for _ in range(length))

# Example usage:
otp = generate_otp()
print(f"Generated OTP: {otp}")


```

Validate Date Format Based on Platform:


```
import datetime

def validate_date_format(date_string, platform='unix'):
    """Validate date format based on the platform ('unix' or 'windows')."""
    try:
        if platform == 'unix':
            datetime.datetime.strptime(date_string, '%Y-%m-%d')
        elif platform == 'windows':
            datetime.datetime.strptime(date_string, '%m/%d/%Y')
        else:
            raise ValueError("Invalid platform specified.")
        return True
    except ValueError:
        return False

# Example usage:
date_unix = '2022-02-18'
date_windows = '02/18/2022'

print(validate_date_format(date_unix, platform='unix'))      # True
print(validate_date_format(date_windows, platform='windows'))  # True
print(validate_date_format('2022/02/18', platform='unix'))    # False

```


Convert Lengthy Decimal Value to 8 Decimal Places:


```
def convert_to_8_decimal(value):
    """Convert a lengthy decimal value to an 8-decimal value."""
    try:
        return round(float(value), 8)
    except ValueError:
        return None

# Example usage:
lengthy_decimal = "12345.6789012345678901234567890123456789"
converted_value = convert_to_8_decimal(lengthy_decimal)
print(f"Converted Value: {converted_value}")


```


Validate Not Future Date:


```
def validate_not_future_date(date_string, format='%Y-%m-%d'):
    """Validate that a date is not a future date."""
    try:
        input_date = datetime.datetime.strptime(date_string, format)
        today = datetime.datetime.now().replace(hour=0, minute=0, second=0, microsecond=0)
        return input_date <= today
    except ValueError:
        return False

# Example usage:
date_future = '2022-02-20'
date_past = '2022-02-18'

print(validate_not_future_date(date_future))  # False
print(validate_not_future_date(date_past))    # True
print(validate_not_future_date('invalid_date'))  # False

```