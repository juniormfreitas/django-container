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
