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
