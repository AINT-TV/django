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

## Create a Template

Inside the `templates` folder (located at `./project/templates/`), we create an HTML file named `index.html` like this:

```
<!DOCTYPE html>
<html>
<head>
    <title>Home</title>
</head>
<body>
    Hello World!
</body>
</html>
```

## Associate the Template with a View

Now that our template is created, we should define how/when it should be used. To do this, we need a "view". As we previously saw, the views associated with our `myapp` app are defined inside the `views.py` file located at `./project/myapp/views.py`. We can see that the `render` function is imported inside this file. This function combines a given template with a given context dictionary and returns an HttpResponse object with that rendered text. However, in this simple example, we do not have a "context dictionary". We can define our view like this:

```
def hello(request):
    return render(request, 'index.html')
```

Note that Django knows where to look for `index.html` since we have introduced its path to it (by editing the `settings.py` file). 

## Define a URL Pattern

The last step is to edit the `urls.py` file as we did before. This file is located at `./project/project/urls.py`. We only need to add the following line to it:

```
path('', hello)
```

From now on, whenever we look for `127.0.0.1:9000`, we will see the contents of our `index.html` rendered as a `HttpResponse`.
