To setup a Django project in Docker, `cd` into the project directory and complete the following steps.

# Dockerfile

Create a file called `Dockerfile` and paste the following inside:
```
FROM python:3
ENV PYTHONUNBUFFERED 1

RUN mkdir /code
WORKDIR /code

COPY requirements.txt /code/
RUN pip install -r requirements.txt

COPY . /code/
```

# Requirements

Create a file called `requirements.txt` and paste the following inside:
```
Django>=2.0,<3.0
psycopg2>=2.7,<3.0
```

# Docker Compose

Create a file called `docker-compose.yml` and paste the following inside:
```
version: '3'

services:
  db:
    container_name: django_db
    image: postgres
  
  web:
    container_name: django_web
    build: .
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/code
    ports:
      - "8000:8000"
    depends_on:
      - db
```

# Django Project

From within your project directory, you need to start your first Django project.
```
$ sudo docker-compose run web django-admin startproject <app_name> .
```

# Database Connection

To access the Postgres database volume, update the `DATABASES` parameter in our `settings.py`
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',
        'USER': 'postgres',
        'HOST': 'db',
        'PORT': 5432,
    }
}
```

# gitignore

Create your `.gitignore` file and add any files you do not wish to track.


# Start Django
```
$ docker-compose up
```


### Quickly create files

```
touch Dockerfile
touch requirements.txt
touch docker-compose.yml
touch .gitignore
```
