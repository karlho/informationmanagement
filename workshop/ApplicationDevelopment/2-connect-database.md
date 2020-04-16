1. Confirm Web Server is running
    * ``` cd epps6354 ```
    * Run Webserver ``` python manage.py runserver ```
    * In your favorite browser, go to ``` http://127.0.0.1:8000/ ``` 
    * admin ``` http://127.0.0.1:8000/admin ```
    
2. Connect to Database
    * Install python-postgres database engine/connector ``` pip install psycopg2 ```
      | MacOS         | Windows   | 
      |:-------------:|:-------------:| 
      | nano mysite/settings.py       |notepad mysite\settings.py |
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
    * Be sure to change to your PostgreSQL password
    * Restart Web Server "python manage.py runserver ```
    
3. ORM ( Object-Relational Mapping )
    * Create and apply SQL to database ```python manage.py migrate ```
    * Create super user ```python manage.py createsuperuser```
    * Inspect Models, visit ``` http://127.0.0.1:8000/admin ``` 

| MacOS         | Windows   | 
|:-------------:|:-------------:| 
| python3       |python |
| pip3       |pip |
| mv            | move |
| nano            | notepad |
 
