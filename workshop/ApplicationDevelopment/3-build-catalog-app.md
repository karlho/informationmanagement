# [Catalog](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django)
[MVC]: https://mdn.mozillademos.org/files/13931/basic-django.png "MVC"
[MVC Flow](https://mdn.mozillademos.org/files/13931/basic-django.png)
1. Create an catalog app
    * Create app ``` python manage.py startapp catalog ```
    * visit ```http://127.0.0.1:8000/catalog```
    * catalog/views.py
    ```python
    
   from django.http import HttpResponse
   from django.template import loader
   from .models import Department
   from django.shortcuts import render
    from django.http import HttpResponse
    def index(request):
        return HttpResponse("Hello, world. You're at the catalog index.")
    def dept(request):
        departments = Department.objects.all()
       template = loader.get_template('catalog/dept.html')
       context = {
            'department_list': departments,
        }
       return HttpResponse(template.render(context, request))   
    ```
    * catalog/templates/catalog/dept.html
    ```html
    {% load static %}
    
    <link rel="stylesheet" type="text/css" href="{% static 'catalog/style.css' %}">
    
    {% if department_list %}
        <table ="1">
    <tr><th>Department</th><th>Building</th></tr>
        {% for dept in department_list %}
            <tr>
                <td>{{ dept.dept_name }}</td>
                <td>{{ dept.building }}</td>
            </tr>
        {% endfor %}
        </table>
    {% else %}
        <p>No Departments are available.</p>
    {% endif %}
   
    ```


    * catalog/urls.py
    ```python
   from django.urls import path
   from . import views
   urlpatterns = [
        path('', views.index, name='index'),
   ]
    ```
   * in the main routing file mysite/urls.py
   ```python
    from django.contrib import admin
    from django.urls import include, path

    urlpatterns = [
        path('catalog/', include('catalog.urls')),
        path('admin/', admin.site.urls),
    ]
    ```
   * In terminal press Ctrl-C to stop webserver, restart it with ``` python manage.py runserver```
2. List Departments
    * catalog/urls.py
    ```python
    from django.urls import path
    from . import views

    urlpatterns = [
        path('', views.index, name='index'),
        path('dept', views.dept, name='dept'),
    ]
    ```
    * catalog/models.py
    ```python
    from django.db import models

    class Department(models.Model):
        dept_name = models.CharField(primary_key=True, max_length=20)
        building = models.CharField(max_length=15, blank=True, null=True)
        budget = models.DecimalField(max_digits=12, decimal_places=2, blank=True, null=True)

        class Meta:
            managed = False
            db_table = 'department'
    ```
    * mysite/settings.py
    ```python
    INSTALLED_APPS = [
        'catalog.apps.CatalogConfig',
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
    ]
   ```
    * catalog/admin.py
    ```python
       from django.contrib import admin
       from .models import Department

       admin.site.register(Department)
   ```
    * visit ```http://localhost:8000/catalog/dept```



| MacOS         | Windows   | 
|:-------------:|:-------------:| 
| python3       |python |
| pip3       |pip |
| mv            | move |
| nano            | notepad |
