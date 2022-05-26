# log-telegram
Python logger handler that sends logs to telegram chats

Based on [python-telegram-logger](https://github.com/parikls/python-telegram-logger)

Example of logging to the console and to a telegram chat:

```python
import logging
from logging import config

LOGGING = {
    "version": 1,
    "disable_existing_loggers": False,
    "handlers": {
        "console": {"class": "logging.StreamHandler", "formatter": "verbose"},
        'telegram': {
            'class': 'log_telegram.Handler',
            'token': 'XXXXXXXXXX:FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF',
            'chat_ids': [000000000],
            'fmt': '[%(levelname)s] %(name)s - %(asctime)s:\n\n%(message)s'
        }
    },
    "root": {
        "handlers": ["console", "telegram"],
        "level": "WARNING",
    },
    "formatters": {
        "verbose": {
            "format": "[{levelname}] {name} - {asctime}:{message}",
            "style": "{",
        },
    },
}

logging.config.dictConfig(LOGGING)

logger = logging.getLogger(__name__)
```