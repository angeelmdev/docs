# Twig

Documentación oficial

[https://twig.symfony.com](https://twig.symfony.com/)


Twig es un motor de plantillas desarrollado para el lenguaje de programación PHP y que nace con el objetivo de facilitar a los desarrolladores de aplicaciones web que utilizan la arquitectura MVC

* Comentarios `{#  #}`

```php
{# Esto es un comentario #}
```


* Variables y funciones `{{  }}`

```php
{# Ver los tipos y el contenido de una variable #}
{{ dump(posts) }}

{# Saber si hay un usuario autenticado #}
{{ is_granted('IS_AUTHENTICATED_REMEMBERED') }}
```


* Operaciones lógicas y declaración de variables `{%  %}`

```php
{% for post in posts %}
  <h1>{{post.title}}</h1>
  <h2>{{post.description}}</h2>
{% endfor %}
```


* Filtros 

  Se aplican agregando tras una variable una barra vertical `|`Por ejemplo, el siguiente código nos permite convertir todos los caracteres de una cadena en mayúsculas.

```php
{{ 'hola mundo' | upper }}
```


* Bloques

  Nos permiten reutilizar código. Para su uso debemos agregar el código en una plantilla base que será heredada. 

```php
<title>{% block title %}Welcome!{% endblock %}</title>
```

     y posteriormente, desde el archivo donde vamos a reutilizar ese código twig

```php
{% extends 'base.html.twig' %}

{% block title %}{{parent()}} - Frikyland{% endblock %}
```


Ejemplo completo  

base.html.twig

```php
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>{% block title %}Welcome!{% endblock %}</title>
        <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 128 128%22><text y=%221.2em%22 font-size=%2296%22>⚫️</text><text y=%221.3em%22 x=%220.2em%22 font-size=%2276%22 fill=%22%23fff%22>sf</text></svg>">
        {% block stylesheets %}
        {% endblock %}

        {% block javascripts %}
            {% block importmap %}{{ importmap('app') }}{% endblock %}
        {% endblock %}
    </head>
    <body>
        {% block body %}{% endblock %}
    </body>
</html>
```

index.html.twig

```php
{% extends 'base.html.twig' %}

{% block title %}{{parent()}} - Frikyland{% endblock %}

{% block body %}
    {{ form(form) }}

    <table>
        <thread>
            <tr>
                <td>id</td>
                <td>titulo</td>
                <td>descripción</td>
                <td>creation date</td>
            </tr>
        </thread>
        <tbody>
        {% for post in posts %}
            <tr>
                <td>{{post.id}}</td>
                <td>{{post.title}}</td>
                <td>{{post.description}}</td>
                <td>{{post.creation_date | date}}</td>
            </tr>  
        {% endfor %}
        </tbody>
    </table>

{% endblock %}
```


