# ****Структура и настройки Django проекта****

Организация кода в проекте является фундаментальным аспектом разработки программного обеспечения, включая веб-приложения на фреймворке Django. Независимо от размера проекта, хорошо структурированный и организованный код играет важную роль в обеспечении его эффективности, поддерживаемости и масштабируемости.

Организация кода в проекте помогает разработчикам:

- Легче понимать и анализировать код, даже если другой разработчик работает над проектом.
- Обеспечить повторное использование кода и компонентов, что ускоряет разработку.
- Эффективно масштабировать проект при необходимости добавления новых функциональных возможностей.

В данном уроке мы подробно рассмотрим, как организовать код в Django проекте и создать веб-приложение внутри него. Эти знания станут основой для дальнейшей разработки веб-приложений с использованием Django и помогут вам стать более компетентным и организованным разработчиком.

```
current_dir/  <- текущая директория
    __init__.py
    asgi.py
    manage.py
    myproject/
        __init__.py
        settings.py
        urls.py
        wsgi.py

```

## Структура созданного проекта и описание важных файлов и папок

После создания проекта, вам стоит более подробно ознакомиться с его структурой и некоторыми важными файлами:

- `manage.py`: Управляющий скрипт, который позволяет вам взаимодействовать с проектом. С его помощью вы можете запускать локальный сервер, создавать приложения, мигрировать базу данных и многое другое.
- `myproject/settings.py`: Файл настроек проекта, в котором определяются параметры, такие как база данных, статические файлы, маршруты и другие настройки вашего проекта. Этот файл играет важную роль в конфигурации Django-приложения.
- `myproject/urls.py`: Файл маршрутизации, который определяет, какие URL-адреса должны быть связаны с какими представлениями (views) в вашем приложении. Этот файл определяет, какие страницы будут доступны по каким URL.
- `__init__.py`: Этот пустой файл указывает Python, что каталог `myproject` следует рассматривать как модуль Python. Это позволяет вам импортировать объекты и настройки из этого каталога.
- `asgi.py` и `wsgi.py`: Эти файлы используются для поддержки различных серверных протоколов (ASGI и WSGI) при развертывании Django-приложения на веб-серверах.

Понимание структуры созданного проекта и роли каждого файла и каталога является важным шагом для начала разработки на Django.

## Файл настроек `settings.py`

### Роль файла настроек в проекте

Файл `settings.py` является одним из самых важных компонентов Django проекта. Он содержит настройки и конфигурации, которые определяют поведение и характеристики проекта. Роль этого файла сравнима с "управляющим мозгом" проекта, так как он влияет на практически все его аспекты.

Основные задачи файла настроек `settings.py` включают в себя:

1. **Определение базовых параметров проекта:** В этом файле задаются основные параметры, такие как название проекта, уровень отладки, разрешенные хосты и другие.
2. **Подключение и настройка приложений:** Здесь указываются приложения, которые включены в проект, и их настройки. Это позволяет добавлять и настраивать функциональность проекта.
3. **Конфигурация базы данных:** Если в проекте используется база данных, то в `settings.py` указываются параметры подключения к ней, такие как тип базы данных, имя, пользователь и пароль.
4. **Настройки безопасности:** Файл настроек также определяет параметры безопасности, такие как секретный ключ, список разрешенных хостов и другие.
5. **Настройки медиафайлов и статики:** Django позволяет управлять статическими файлами (например, CSS и JavaScript). В `settings.py` можно указать местоположение этих файлов и настроить их обработку.
6. **Другие параметры и настройки:** Файл настроек может содержать множество других параметров, влияющих на работу проекта, таких как язык приложения, часовой пояс, настройки электронной почты и многое другое.

### Основные параметры и настройки, которые можно задать в `settings.py`

В `settings.py` можно настроить множество параметров, но некоторые из наиболее важных включают:

- `DEBUG`: Уровень отладки. Этот параметр определяет, включен ли режим отладки (`True`) или отключен (`False`). В режиме отладки при возникновении ошибок на страницах отображаются подробные сообщения об ошибках, что полезно при разработке, но не рекомендуется для промышленного окружения.
- `INSTALLED_APPS`: Список установленных приложений. Здесь указываются приложения, которые активированы в проекте.
- `DATABASES`: Настройки подключения к базе данных, включая тип базы данных, имя, пользователя и пароль.
- `SECRET_KEY`: Секретный ключ проекта, используемый для шифрования данных и обеспечения безопасности.
- `ALLOWED_HOSTS`: Список хостов, с которых разрешен доступ к проекту.
- `STATIC_URL`: Настройки для работы со статическими файлами (CSS, JavaScript и др.).
- `LANGUAGE_CODE`: Это параметр настройки в Django, который определяет язык, используемый для локализации веб-приложения.

Это лишь небольшой обзор роли и основных параметров файла настроек `settings.py` в Django проекте. Понимание и умение настраивать этот файл являются важными навыками для разработчика Django и позволяют создавать мощные и гибкие веб-приложения.

## Файл маршрутизации `urls.py`

### Задачи и функции файла `urls.py`

Файл `urls.py` является ключевым компонентом Django проекта, отвечающим за определение маршрутов (URL-адресов) и связывание их с соответствующими представлениями (views). Он выполняет несколько важных задач:

1. **Маршрутизация запросов:** Файл `urls.py` определяет, какие URL-адреса должны быть обработаны какими представлениями. Это позволяет Django знать, какие действия выполнять при получении запросов от пользователей.
2. **Читаемость и структурирование:** Хорошо организованный файл `urls.py` делает код более читаемым и понятным. Разделение маршрутов на отдельные пути позволяет быстро найти нужное представление в проекте.

### Примеры определения URL-адресов и связанных с ними представлений (views)

Для определения маршрутов и связанных с ними представлений в файле `urls.py` используется синтаксис, который позволяет создавать удобные и информативные маршруты. Вот например содержимое файла `myproject/urls.py`:

```python
from django.contrib import admin
from django.urls import path

urlpatterns = [
    # Маршрут для административного интерфейса Django.
    # При посещении URL "admin/", Django перенаправляет запрос
    # на административный интерфейс.
    path("admin/", admin.site.urls),
]

```

В данном коде, который был сгенерирован автоматически, видим определение единственного маршрута (`path`) в списке `urlpatterns` в файле `urls.py`. Этот маршрут связан с административным интерфейсом Django и позволяет администраторам управлять данными и настройками приложения.

Административная панель Django - это встроенный инструмент, предоставляемый Django, который позволяет администраторам и разработчикам управлять данными и моделями вашего веб-приложения через веб-интерфейс. Она предоставляет удобный способ создания, изменения и удаления данных в базе данных с использованием веб-интерфейса.

- `path("admin/", admin.site.urls)` определяет маршрут, который начинается с URL-префикса "admin/". Когда пользователь посещает этот URL (например, "[http://127.0.0.1:8000/admin/](http://example.com/admin/)"), Django перенаправляет запрос на административный интерфейс.
- `admin.site.urls` указывает Django использовать стандартные URL-адреса для административного интерфейса.

Этот код демонстрирует, как можно определить маршруты в файле `urls.py` и связать их с соответствующими представлениями. В данном случае, маршрут "admin/" используется для доступа к административному интерфейсу Django. 

Такие определения URL-адресов позволяют Django понимать, какие представления вызывать при запросах пользователей и как их идентифицировать. Файл `urls.py` становится центром управления маршрутами в проекте.

## Управляющий скрипт `manage.py`

В каждом Django проекте присутствует файл с именем `manage.py`, который играет ключевую роль в управлении проектом и выполнении различных задач. Давайте разберем, что представляет собой этот скрипт и какие основные команды доступны для работы с проектом.

### Что представляет собой `manage.py`

`manage.py` является командным скриптом, который позволяет вам выполнять различные операции и управлять Django проектом без необходимости написания длинных команд в консоли. Он предоставляет доступ к множеству полезных команд, которые помогают в разработке, тестировании и управлении приложением.

### Основные команды для работы с проектом

Ниже приведены некоторые из основных команд, которые вы можете выполнять с помощью `manage.py`:

- **`runserver`**: Запускает локальный сервер разработки, который используется для тестирования вашего приложения во время разработки. Вы можете указать порт и IP-адрес, если это необходимо.
    
    **Запуск сервера с IP 0.0.0.0 и портом 8001**:
    
    ```bash
    python manage.py runserver 0.0.0.0:8001
    
    ```
    
    Эта команда запустит локальный сервер на всех доступных интерфейсах (0.0.0.0) и порту 8001. Теперь ваше приложение будет доступно по IP-адресу вашей машины и указанному порту.
    
    Обратите внимание, что для выполнения этих команд вы должны находиться в директории проекта, где находится файл `manage.py`.
    
- **`migrate`**: Применяет миграции и обновляет структуру базы данных в соответствии с текущими миграциями.
    
    **Применение миграций**:
    
    ```bash
    python manage.py migrate
    
    ```
    
    Эта команда выполнит все ожидающие миграции и обновит структуру базы данных в соответствии с текущими миграциями. 
    
    > "You have 18 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions. Run 'python [manage.py](http://manage.py/) migrate' to apply them."
    > 
    
    Это информация, появляющаяся при запуске сервера, о наличии 18 неприменённых миграций в вашей базе данных. Сообщение указывает на необходимость выполнения команды `python manage.py migrate`, чтобы применить эти миграции. 
    
- **`createsuperuser`**: Создает администратора (суперпользователя) Django, который имеет доступ к панели администрирования вашего приложения.
    
    **Создание суперпользователя**:
    
    ```bash
    python manage.py createsuperuser
    
    ```
    
    При выполнении этой команды вам будет предложено ввести имя пользователя, адрес электронной почты и пароль для нового суперпользователя Django, который будет иметь доступ к административной панели вашего приложения.
    

Это лишь небольшой набор доступных команд. `manage.py` предоставляет множество других команд и опций, которые могут быть полезными в разных ситуациях. Этот скрипт является мощным инструментом для управления Django проектом и упрощает рутинные задачи разработки.

> C полным перечнем команд доступных для `manage.py` вы сможете ознакомиться в [официальной документации](https://docs.djangoproject.com/en/4.2/ref/django-admin/).
