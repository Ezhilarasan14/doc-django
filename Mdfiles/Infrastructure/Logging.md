#Infrastructure Layer

##Logging

<p>
Logging is an essential aspect of software development as it helps in monitoring and debugging applications. In Django, you can configure logging to record information about your application's behavior.

Here are the steps to set up logging in a Django project:

Digid Customized logger functions: 
1. Application level logger - MLBANK
2. Query level logger - QUERY
3. Integration level logger - INTEG
3. Queue level logger - AI

</p>

###1. Configure Logging Settings:


```
import os

# ...

LOGGING = {
    'version': 1,
    'disable_existing_loggers': False,
    'formatters': {
        'standard': {
            'format' : "[%(asctime)s] %(levelname)s [%(name)s:%(filename)s:%(lineno)s:%(funcName)s] %(message)s",
            'datefmt' : "%d/%b/%Y %H:%M:%S"
        },
    },
    'handlers': {
        'MLBANK': {
            'handlers': ['console', 'logfile'],
            'level': 'DEBUG',
            'propagate': False
        },
		'INTEG': {
            'handlers': ['console', 'logfile'], #['dynamic_debug'],
            'level': 'DEBUG',
            'propagate': False
        },
        'QUERY': {
            'handlers': ['query_prints'],
            'level': 'INFO',
            'propagate': False
        },
    },
    'loggers': {
        'django': {
            'handlers': ['file'],
            'level': 'DEBUG',
            'propagate': True,
        },
    },
}

```

###2. Use Logging in Your Code
<p>
You can use the logging module in your Django code to add log messages. For example:

</p>

```
import logging

logger = logging.getLogger('MLBANK')
qlogger = logging.getLogger('QUERY')
ilogger = logging.getLogger('INTEG')


# Example app log messages
logger.debug('This is a debug message')
logger.info('This is an info message')
logger.warning('This is a warning message')
logger.error('This is an error message')
logger.critical('This is a critical message')

# Example query log messages
qlogger.debug('This is a debug message')
qlogger.info('This is an info message')


# Example query log messages
ilogger.debug('This is a debug message')
ilogger.info('This is an info message')
```