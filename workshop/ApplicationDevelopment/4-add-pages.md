1. Prerequisites
    * Server is running ``` http://127.0.0.1:8000/ ``` 
    * Connected to database ``` http://127.0.0.1:8000/admin ```
    * Demo app is running ``` http://localhost:8000/catalog/dept ```
    * install library ```pip install requests pandas plotly```
    * create directories 
    ``` 
   catalog/static/catalog
   catalog/templates/catalog
    ```
    * In terminal press Ctrl-C to stop webserver, restart it with ``` python manage.py runserver```
    
        
2. Add another page with static image
    * catalog/urls.py
    ```python
   from django.urls import path
   from . import views
   urlpatterns = [
       path('', views.index, name='index'),
       path('static_image', views.static_image, name='static_image'),
   ]
    ```
    * catalog/views.py
    ```python
   ...
    def static_image(request):
        template = loader.get_template('catalog/static_image.html')
        context = {}
        return HttpResponse(template.render(context, request))
    ... 
    ```
   * catalog/template/catalog/static_image.html
   ```python
   {% load static %}
   <link rel="stylesheet" type="text/css" href="{% static 'catalog/style.css' %}">
   <img src="{% static "catalog/sars-cov-19.jpg" %}" alt="sars-cov-19">
   ```

    * visit ```http://localhost:8000/catalog/static_image```

3. Add another page with Covid-19 charts
    * catalog/urls.py
    ```python
    from django.urls import path
    from . import views
    
    urlpatterns = [
        path('', views.index, name='index'),
        path('dept', views.dept, name='dept'),
        path('static_image', views.static_image, name='static_image'),
        path('covid19', views.covid19, name='covid19'),
    ```
    * catalog/views.py
    ```python
   ...
    def covid19(request):
        template = loader.get_template('catalog/covid19.html')
        graph = None
    
        # chart
        import plotly.express as px
        api_url = 'http://corona-api.com/countries/us?include=timeline'
        api_response = requests.get(api_url)
        api_response_json = json.loads(api_response.text)
        df = pandas.read_json(json.dumps(api_response_json['data']['timeline']))
    
        fig = px.line(df, x="date", y="confirmed", title='Covid-19 Confirmed Case in the US')
        graph = fig.to_html(full_html=False, default_height=500, default_width=700)
        # end of chart
        
        context = {
            'graph': graph
        }
        return HttpResponse(template.render(context, request))
    ... 
    ```
   * catalog/template/catalog/covid19.html
   ```python
    {% if graph %}
    {{graph|safe}}
    {% else %}
        <p>No Graph</p>
    {% endif %}
   ```

    * visit ```http://localhost:8000/catalog/covid19```

| MacOS         | Windows   | 
|:-------------:|:-------------:| 
| python3       |python |
| pip3       |pip |
| mv            | move |
