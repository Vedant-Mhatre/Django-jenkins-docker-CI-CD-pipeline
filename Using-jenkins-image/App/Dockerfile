FROM python:3.8.5-alpine as baseimage

RUN apk add --no-cache mariadb-connector-c-dev

RUN apk update && \
    apk add python3 python3-dev mariadb-dev build-base && \
    pip3 install mysqlclient && \
    apk del python3-dev mariadb-dev build-base


WORKDIR /app

RUN python -m pip install --upgrade pip

ENV PYTHONUNBUFFERED=1

RUN pip install Django==3.1.2 django-mysql==3.8.1 

RUN pip install django-jenkins

# RUN python manage.py runserver 0.0.0.0:8000