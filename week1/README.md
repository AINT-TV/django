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

To create an app called `myapp`, change the current directory to `./project/` (where the `manage.py` exists), and run `python manage.py startapp myapp`.
