# django-cheatsheet
Django Cheatsheet

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
