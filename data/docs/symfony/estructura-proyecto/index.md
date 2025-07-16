# Estructura de un proyecto

Un proyecto Symfony se compone de los siguientes directorios:


**public/**  

Aquí se encontrara todos los archivos públicos de la webs. Puede ser las hojas de estilo, imagenes, archivos subidos por los usuarios…  

**src/**  

Aquí se encuentra toda la lógica de la aplicación. Controladores, consulta a base de datos… Por defecto se crean tres carpetas:  
- Controller/  
- Controladores  
- Entity/  
- Entidades (Las tablas de la base de datos)  
- Repository/ (Consultas a la base de datos)  

**templates/**

Aquí se ubicarían las plantillas de la aplicación. Todos los archivos twig que corresponden a la vista de la web.


**assets/**

Esta carpeta es utilizada por webpack encore, una tecnología usada por Symfony 6 que permite gestionar las dependencias de los assets de la aplicación.


**bin/**

Contiene un archivo `console` el cual nos permite ejecutar comandos de Symfony. Se puede consultar la lista de comandos disponibles ingresando en la terminal:

```none
php bin/console
```


**var/**

En este directorio podemos encontrar dos carpetas más:cache/    → Donde se almacena la cache de la aplicaciónlog/         → Donde podemos encontrar un archivo `dev.log` que contiene los logs de la aplicación


**vendor/**

Carpeta que contiene todas las dependencias de la aplicación generada a partir de los archivos `composer.json` y `composer.lock`


**.env**

Archivo de parametrización que contiene datos sensibles como por ejemplo pueden ser las claves de la BD
