1. Prerequisites
    * PostgresSQL
    * pgAdmin
    * Python, pip
  
2. install [Django](https://docs.djangoproject.com/en/3.0/intro/install/)
    * environment ``` pip -V``
    * (optional) if you're using virtualenv ```source ~/.virtualenvs/django/bin/activate;cd ~/PycharmProjects/EPPS6354```
    * ```python -m pip install Django```
    * ```python -c 'import django; print(django.get_version())'```
    * ```python -m django --version```
3. Initiate a project [Tutorial](https://docs.djangoproject.com/en/3.0/intro/tutorial01/)
    * Initiate project structure``` django-admin startproject mysite ```
    * Change project name ``` mv mysite epps6354  ```
    * ``` cd epps6354 ```
    * Run Webserver ``` python manage.py runserver ```
    * In your favorite browser, go to ``` http://127.0.0.1:8000/ ``` 
    * admin ``` http://127.0.0.1:8000/admin ```
4. Connect to Database
    * Install python-postgres database engine/connector ``` pip install psycopg2 ```
    * If using docker ``` pip install psycopg2-binary ```
    * File mysite/settings, find "DATABASES" dictionary, change it to
```python      
    DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',
        'USER': 'postgres',
        'PASSWORD': 'mysecretpassword',
        'HOST': 'localhost',
        'PORT': '5432',
        }
    } 
```
    * Restart Webserver "python manage.py runserver ```
    
5. ORM ( Object-Relational Mapping )
    * Create and apply SQL to database ```python manage.py migrate ```
    * Create super user ```python manage.py createsuperuser```
    * Inspect Models, visit ``` http://127.0.0.1:8000/admin ``` 
    * Create ORM code ``` python manage.py inspectdb  > models.py```

 