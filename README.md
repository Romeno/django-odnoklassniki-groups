Django Odnoklassniki Groups
===========================

[![PyPI version](https://badge.fury.io/py/django-odnoklassniki-groups.png)](http://badge.fury.io/py/django-odnoklassniki-groups) [![Build Status](https://travis-ci.org/ramusus/django-odnoklassniki-groups.png?branch=master)](https://travis-ci.org/ramusus/django-odnoklassniki-groups) [![Coverage Status](https://coveralls.io/repos/ramusus/django-odnoklassniki-groups/badge.png?branch=master)](https://coveralls.io/r/ramusus/django-odnoklassniki-groups)

Приложение позволяет взаимодействовать с группами соц. сети Одноклассники, их статистикой и пользователями групп через OK API используя стандартные модели Django

Установка
---------

    pip install django-odnoklassniki-groups

В `settings.py` необходимо добавить:

    INSTALLED_APPS = (
        ...
        'oauth_tokens',
        'taggit',
        'odnoklassniki_api',
        'odnoklassniki_groups',
    )

    # oauth-tokens settings
    OAUTH_TOKENS_HISTORY = True                                             # to keep in DB expired access tokens
    OAUTH_TOKENS_ODNOKLASSNIKI_CLIENT_ID = 12345678                         # application id
    OAUTH_TOKENS_ODNOKLASSNIKI_CLIENT_PUBLIC = ''                           # application public key
    OAUTH_TOKENS_ODNOKLASSNIKI_CLIENT_SECRET = ''                           # application secret key
    OAUTH_TOKENS_ODNOKLASSNIKI_SCOPE = ['']                                 # application scopes
    OAUTH_TOKENS_ODNOKLASSNIKI_USERNAME = ''                                # user login
    OAUTH_TOKENS_ODNOKLASSNIKI_PASSWORD = ''                                # user password

Покрытие методов API
--------------------

* [group.getInfo](http://apiok.ru/wiki/display/api/group.getInfo) – получение информации о группах;
* [group.getInfo](http://apiok.ru/wiki/display/api/group.getMembers) – получение списка пользователей группы;

Примеры использования
---------------------

### Получение группы

    >>> from odnoklassniki_groups.models import Group
    >>> Group.remote.fetch(ids=[47241470410797])
    [<Group: Кока-Кола>]