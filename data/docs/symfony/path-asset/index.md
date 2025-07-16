# path y asset

En Symfony disponemos de estas dos funciones

* **path()**

  Permite obtener la ruta completa de una vista a partir de su nombre y con la posibilidad de pasarle parámetros.

```php
<tbody>
{% for post in posts %}
  <tr>
    <td><a href="{{ path('postDetails', {id:post.id}) }}">Ver</a></td>
    <td>{{post.title}}</td>
    <td>{{post.description}}</td>
    <td>{{post.creation_date | date}}</td>
  </tr>     
{% endfor %}
</tbody>
```


* **asset()**

  Permite obtener el contenido de la carpeta /public ahorrándonos tener que poner la ruta completa al directorio del proyecto.

  En el siguiente ejemplo podemos ver como se agrega un css a nivel global del proyecto en la plantilla base de Tiwig.

```php
<!DOCTYPE html>
<html>
    <head>
        ...
        {% block stylesheets %}
            <link rel="stylesheet" href="{{asset('css/bootstrap.min.css')}}">
        {% endblock %}
        ...
    </head>
    ... 
</html>
```

O si por ejemplo quisiéramos mostrar una imagen.

```php
    {% if post.file != null %}
        <img src="{{ asset('uploads/files/' ~ post.file)}}" alt="photo" width="100%">
    {% endif %}
```
