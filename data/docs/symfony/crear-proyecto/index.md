# Crear proyecto

Instalar Symfony CLI

```javascript
curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | sudo -E bash
$ sudo apt install symfony-cli
```

Crear un proyecto con Symfony CLI

```none
symfony new --webapp <nombre proyecto>
```


Levantar web en desarrollo

```none
symfony serve
```

Lo normal es que se levante en el puerto 8000
