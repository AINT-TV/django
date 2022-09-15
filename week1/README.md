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

To define a `hello` view associated with `myapp`, we should edit the `views.py` file located at `./project/myapp/views.py`. We write the following lines inside this file:

```
from django.http import HttpResponse

def hello(request):
    return HttpResponse('hello world!')
```

As you see, our `hello` view recieves a `request`, and returns a `HttpResponse` (as it was supposed to). Now, we should specify when this view should be called, in other words, when it should be used!

To do this, we have to define a "URL Pattern" associated with it. This can be done by editing the `urls.py` file located at `./project/project/urls.py`. We should add the following lines to this file:

```
from myapp.views import hello

urlpatterns = [
    path("",hello)
]
```

This means that whenever the user sends its request by looking for the `127.0.0.1:9000` url, the `hello` app should be called to prepare a response. If we change the above piece of code and write `path("greet",hello)` instead, it means that the `hello` view should be called if the user looks for `127.0.0.1:9000/greet`.

