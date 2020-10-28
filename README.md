# Django-jenkins-docker

## About
CI/CD pipeline using Docker, Jenkins and Django

Currently only [Using-jenkins-without-nginx](https://github.com/Vedant-Mhatre/Django-jenkins-docker-CI-CD-pipeline/tree/main/Using-jenkins-without-nginx) method is working.

Might not pursue other methods due to their disadvantages and many errors.

This pipeline clones my [django-ecommerce](https://github.com/Vedant-Mhatre/django-ecommerce) github repository which contains a sample django project configured with [django-jenkins](https://pypi.org/project/django-jenkins/)

Setup:

1. Clone repository using HTTPS and **cd** into the project
```
git clone https://github.com/Vedant-Mhatre/Django-jenkins-docker.git
```
```
cd Using-jenkins-without-nginx
```

2. Run using docker-compose
```
docker-compose up
```

* Jenkins will show initial password in the terminal, copy that

* Jenkins will be available at [localhost:8080](http://localhost:8080/)

3. Visit Jenkins page and login using the above password and select install using suggested plugins options.

4. Create a user using any credentails and login

5. Install [Cobertura](https://plugins.jenkins.io/cobertura/)  plugin for showing the code coverage and [Violations](https://plugins.jenkins.io/violations/) for parsing pylint reports

6. Go to Create New and Create free style project according to this [blog](https://medium.com/aubergine-solutions/django-jenkins-integration-for-django-project-3fe3251cd6f4) and in execute shell build step use this script:
```
virtualenv -p python3 ecommerce
source ecommerce/bin/activate
pip install -r requirements.txt
python manage.py makemigrations
python manage.py migrate
python manage.py jenkins
```
And then setup the after build steps using the above guide
