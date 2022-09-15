# Templates

A template is a text file used to generate another text file (e.g., an HTML, XML, or CSV file). If follows a special language called the "Django Template Language" (DTL). 

Previously, our `hello` view just returned a simple string. However, if it was a real website, we would need to use an HTML page as our response. To do that, we would need a "template"!

Remember that our project was structured like this:

```
./project/
├─ db.sqlite3
├─ project
│   ├── __init__.py
│   ├── __pycache__
│   ├── asgi.py
│   ├── settings.py   (this is where we introduce our templates directory)
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
│   ├── views.py
```

## Create and Introduce the Templates Directory

We need a folder to store our "templates". So, we create a new folder called `templates` which will be located at `./project/templates/`. 

The only problem is that the Django project does not recognize this folder. To solve this, we should change `settings.py` file located at `./project/project/settings.py`. Inside this file, there is a `TEMPLATES` variable, which looks like this at first:

```
TEMPLATES = [
    {
        "BACKEND": "django.template.backends.django.DjangoTemplates",
        "DIRS": [], # we should change this line
        "APP_DIRS": True,
        "OPTIONS": {
            "context_processors": [
                "django.template.context_processors.debug",
                "django.template.context_processors.request",
                "django.contrib.auth.context_processors.auth",
                "django.contrib.messages.context_processors.messages",
            ],
        },
    },
]
```

We need to change the value associated with the `DIRS` key, and add our "templates" path to its list. So, `"DIRS": []` will be changed to `"DIRS": ['templates']`

Inside this folder, we create an HTML file named `index.html`. Now,  
