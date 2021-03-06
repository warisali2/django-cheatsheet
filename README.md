# django-cheatsheet
Django Cheatsheet

## Table Of Contents
* [Check Django Version](#check-django-version)
* [Create Django Project](#create-django-project)
* [Run Development Server](#run-development-server)
* [Create an App](#create-an-app)
* [Projects vs Apps](#projects-vs-apps)
* [Sample View](#sample-view)
* [Map View to URL](#map-view-to-url)
* [Point Root URLConf at App's URL module](#point-root-urlconf-at-apps-url-module)

## Check Django Version
```bash
python -m django --version
```

## Create Django Project
**Note:** Don't use - in project name
```bash
django-admin startproject your_project_name
```
It creates following directory structure
```
└── your_project_name
    ├── manage.py
    └── your_project_name
        ├── __init__.py
        ├── settings.py
        ├── urls.py
        └── wsgi.py
```
These files are:
* **Outer your_project_name** Root director of your project. Just a container.
* **manage.py** Django utility to interact with project.
* **Inner your_project_name** Actual django app.
* **settings.py** Settings for this django project.
* **urls.py** URLs declarations for this django project.
* **wsgi.py** Entry point for WSGI (Web Server Gateway Interface) compatible servers to serve your project.

## Run Development Server
```bash
python manage.py runserver [ip-address:port]
```
If no address is given, it will run server on http://localhost:8000/.

## Create an App
```bash
python manage.py startapp your_app_name
```
It creates following directory structure
```
├── your_app_name
    ├── admin.py
    ├── apps.py
    ├── __init__.py
    ├── migrations
    │   └── __init__.py
    ├── models.py
    ├── tests.py
    └── views.py
```
**Note:** Apps can live anywhere on your *python path*.

## Projects vs Apps
An app is a Web application that does something – e.g., a Weblog system, a database of public records or a simple poll app. A project is a collection of configuration and apps for a particular website. A project can contain multiple apps. An app can be in multiple projects.

## Sample View
Here is simplest possible view in django
```python
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello django!!")
```

## Map View to URL
Create a ***urls.py*** file in your app's directory and add following lines
```python
from django.urls import path

from . import views

urlpatterns = [
    path('url_to_view', 'your_view', name='name_for_your_url')
]
```
*name* attribute is used to refer your view from somewhere else in your code. Even if you change the actual url, name will still refer to same view. For example

**In Code**
```python
password_url = reverse('name_for_your_url')
```

**In template**
```html
<p>Please go <a href="{% url 'name_for_url' %}">here</a></p>
```

## Point Root URLConf at App's URL module
Add following lines in your ***project/urls.py***
```python
from django.urls import include

urlpatterns = [
    path('sub_url_for_your_app', include('your_app.urls'))
]
```
*include()* allows referencing other URLConfs
