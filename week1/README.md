# Apps and Views

An app in django is a part of the whole project. For instance, when designing a website, you can make an app for the `users`, `views statistics`, `posts`, etc. 

Views are functions or classes that receive a web request and return a web response (e.g., `HttpResponse`).

# Code Tutorial

Note: We assume that the whole project is located at `./project`, and structured as follows:

```
./project/
├─ db.sqlite3
├─ project
│   ├── __init__.py
│   ├── __pycache__
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
├─ manage.py
```

## Creating and Installing an App

To create an app called `myapp`, change the current directory to `./project/` (where the `manage.py` exists), and run `python manage.py startapp myapp`.
To make the Django project recognize this app (a.k.a "Install" it), edit the `settings.py` file located at `./project/project/settings.py`.

There is a variable called `INSTALLED_APPS` defined in this piece of code. This variable is a list. To install the newly created app, add the name of your app to the end of this list. It will become something like this:

```
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
    "myapp"
]
```

Note that after creating an app, a new folder named after the newly created app will be created at `./project/myapp/`, and the structure of the project will become like this:

```
./project/
├─ db.sqlite3
├─ project
│   ├── __init__.py
│   ├── __pycache__
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
├─ manage.py
├─ myapp
│   ├── __pycache__
│   ├── migrations
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── tests.py
│   ├── views.py    (here we can define views associated with this app)
```

## Defining a View


