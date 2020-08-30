# django-container

## A Docker Container ready to run a Django application

Run the build based on the Dockerfile

```
docker build .
```

Then run the build on the docker-compose

```
docker-compose build
```

### Create Django Project - in the docker container

```
docker-compose run app sh -c "django-admin.py startproject app ."
```

### Create an core app

```
docker-compose run app sh -c "python manage.py startapp core"
```

### Settings

In the `app/app/settings.py` add `core` or the name of the app that you created into INSTALLED_APPS

```python
Example:
...
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'core',
]
```

### Database

In the `app/app/settings.py` you must declare the environment variables already created by the Docker into DATABASES in order to set up your PostgreSql database.

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'HOST': os.environ.get('DB_HOST'),
        'NAME': os.environ.get('DB_NAME'),
        'USER': os.environ.get('DB_USER'),
        'PASSWORD': os.environ.get('DB_PASS'),
    }
}
```

### Run Python unit tests

```
docker-compose run app sh -c "python manage.py test"
```

### Run a Django App in the browser

To start a Django container in the browser `localhost:8000`.

```
docker-compose up
```

or if you want run the process in background

```
docker-compose up -d
```

### Create a super user

In order do access the admin side on `localhost:8000/admin/` for the first time you must create a super user.

```
docker-compose run app sh -c "python manage.py createsuperuser"
```

### Troubleshooting

Your code editor might not see the Django Rest Framework files. To fix that you need to install Django Rest Framework locally running the following command:

```
python3 -m pip install djangorestframework
```
