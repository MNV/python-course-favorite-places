Любимые места
*************

Сервис для сохранения информации о любимых местах.

Установка
=========

Установите требуемое ПО:

1. Docker для контейнеризации – |link_docker|

.. |link_docker| raw:: html

    <a href="https://www.docker.com" target="_blank">Docker Desktop</a>

2. Для работы с системой контроля версий – |link_git|

.. |link_git| raw:: html

    <a href="https://github.com/git-guides/install-git" target="_blank">Git</a>

3. IDE для работы с исходным кодом – |link_pycharm|

.. |link_pycharm| raw:: html

    <a href="https://www.jetbrains.com/ru-ru/pycharm/download" target="_blank">PyCharm</a>

Клонируйте репозиторий проекта в свою рабочую директорию:

    .. code-block:: console

        git clone https://github.com/MEfah/python-course-favorite-places

Использование
=============

Перед началом использования приложения необходимо его сконфигурировать.

.. note::

    Для конфигурации выполните команды, описанные ниже, находясь в корневой директории проекта (на уровне с директорией `src`).

1. Скопируйте файл настроек `.env.sample`, создав файл `.env`:
    .. code-block:: console

        cp .env.sample .env

    Этот файл содержит преднастроенные переменные окружения, значения которых будут общими для всего приложения.
    Файл примера (`.env.sample`) содержит набор переменных со значениями по умолчанию.
    Созданный файл `.env` можно настроить в зависимости от окружения.

    .. warning::

        Никогда не добавляйте в систему контроля версий заполненный файл `.env` для предотвращения компрометации информации о конфигурации приложения.

2. Соберите Docker-контейнер с помощью Docker Compose:
    .. code-block:: console

        docker compose build

    Данную команду необходимо выполнять повторно в случае обновления зависимостей в файле `requirements.txt`.


3. Для запуска приложения выполните:
    .. code-block:: console

        docker compose up

    Приложение предоставляет возможность работы с API посредством интерфейса Swagger по URL http://localhost:8010/docs

    Swagger спецификацию API можно получить по URL http://localhost:8010/openapi.json

Работа с базой данных
---------------------

Для инициализации миграций выполните следующую команду:

    .. code-block::console
        docker compose exec favorite-places-app alembic init -t async migrations

Чтобы создать миграцию выполните следующую команду:

    .. code-block::console
        docker compose run favorite-places-app alembic revision --autogenerate  -m "your description"
Чтобы применить созданные миграции выполните следующую команду:

    .. code-block::console
        docker compose run favorite-places-app alembic upgrade head

Автоматизация
=============

Проект содержит специальный файл (`Makefile`) для автоматизации выполнения команд:

1. Сборка Docker-контейнера.
2. Генерация документации.
3. Запуск форматирования кода.
4. Запуск статического анализа кода (выявление ошибок типов и форматирования кода).
5. Запуск автоматических тестов.
6. Запуск всех функций поддержки качества кода (форматирование, линтеры, автотесты).

Инструкция по запуску этих команд находится в файле `README.md`.

Документация к исходному коду
*****************************

.. toctree::
    :maxdepth: 2
    :caption: Содержимое:

Clients
=======

Base
----

.. automodule:: clients.base.base
    :members:

Geo
---

.. automodule:: clients.geo
    :members:

Schemas
-------

.. automodule:: clients.shemas
    :members:


Integrations
============

Database
--------

.. automodule:: integrations.db.session
    :members:

Events
------

Producer
^^^^^^^^

.. automodule:: integrations.events.producer
    :members:

Schemas
^^^^^^^

.. automodule:: integrations.events.schemas
    :members:

Models
======

Mixins
------

.. automodule:: models.mixins
    :members:

Places
------

.. automodule:: models.places
    :members:

Repositories
============

Base
----

.. automodule:: repositories.base_repository
    :members:

Places
------

.. automodule:: repositories.places_repository
    :members:

Settings
========

.. automodule:: settings
    :members:

Schemas
=======

Base
----

.. automodule:: schemas.base
    :members:

Places
------

.. automodule:: schemas.places
    :members:

Services
========
.. automodule:: services.places_service
    :members:

Transport
=========
.. automodule:: transport.handlers.places
    :members: