1. Prerequisites
    * PostgresSQL
    * pgAdmin
    * python 3, pip
    * PyCharm
2. install [Django](https://docs.djangoproject.com/en/3.0/intro/install/)
    * environment ``` pip -V``

 | MacOS         | Windows   | 
      |:-------------:|:-------------:| 
      | python -m pip install Django     |py -m venv epps6354 |
      |                                  |py -m pip install Django |
    * (optional) if you're using virtualenv ```source ~/.virtualenvs/django/bin/activate;cd ~/PycharmProjects/EPPS6354```
    * ```python -m pip install Django```
    * ```pip install psycopg2-binary ```
    * ```python -c "import django; print(django.get_version())"```
    * ```python -m django --version```
3. Initiate a project [Tutorial](https://docs.djangoproject.com/en/3.0/intro/tutorial01/)
    * Initiate project structure``` django-admin startproject mysite ```
    * Change project name ``` mv mysite epps6354  ``` (Windows move mysite epps6354)
    * ``` cd epps6354 ```
    * Run Webserver ``` python manage.py runserver ```
    * In your favorite browser, go to ``` http://127.0.0.1:8000/ ``` 
    * admin ``` http://127.0.0.1:8000/admin ```

