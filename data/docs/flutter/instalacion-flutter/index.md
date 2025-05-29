# Instalación de Flutter

Guía de instalación oficial para los diferentes sistemas operativos:  
https://dart.dev/get-dart


## Índice

1. [Instalación en macOS](#id1)
1. [Instalación en Windows](#id2)


<div id='id1' />

## Instalación en macOS

Para realizar la instalación del SDK de Dart antes debemos instalar **Homebrew**

``` bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Comprobamos que se reconozca el programa en el terminal

``` bash
brew
```

En caso de que no sse reconzca debemos agregar la siguiente ruta al PATH del sistema operativo.

``` bash
echo "export PATH=/opt/homebrew/bin:$PATH" >> ~/.zprofile
```

Una vez ya reiniciemos el terminal el comando `brew` será reconocido.

A continuación, ejeuctamos los dos siguientes comandos.

``` bash
brew tap dart-lang/dart
```

``` bash
brew install dart
```

Teoricamente en este punto ya tendriamos instalado el SDK. Podemos verificarlo del siguiente modo tras haber reiniciado el terminal.

```
dart --version
```


<div id='id2' />

## Instalación en Windows

La manera que se explicara a continuación es una alternativa a la oficial sobre como se instala el SDK.

En primer lugar, debemos descargar el SDK correspondiente a nuestra arquitectura en el siguiente enlace:  
https://dart.dev/get-dart/archive

Una vez lo tengamos, al descomprimirlo nos encontraremos con una carpeta llamada `dart-sdk`. Dicha carpeta tendremos que moverla a la dirección `C:/tools`

De este sitio nos tendremos que quedar con la siguiente dirección clave:  
`C:/tools/dart-sdk/bin`

A continuación, debemos editar las variables de entorno del sistema `Editar variables de entorno del sistema > Variables del sistema > Path > Editar...` En este menú tendremos que añadir la dirección que vimos anteriormente.

De este modo, el SDK de Dart ya debería estar instalado en el sistema. Podemos confirmar que esto es así dirigiendonos a un PowerShell e ingresando el siguiente comando:

```
dart --version
```
