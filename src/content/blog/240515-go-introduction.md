---
title: 'Go: "Hello World"'
description: 'Introducción al lenguaje de programación Golang'
pubDate: '2024-05-15T01:32:34.123Z'
heroImage: 'https://i.imgur.com/GEHuUVf.png'
categories: ['Go']
tags: ['Go','Golang']
authors: ['pabloarak']
---
Hace poco me pidieron desarrollar una nueva funcionalidad en un proyecto desarrollado en Go. Nunca habia desarrollado en este lenguaje. Como apoyo hice "pair programming" con un compañero más experimentado en ello, y en paralelo decidí hacer un curso como complemento y compartir esta experiencia a través de distintas publicaciones. Asi que vamos allá:

Go es un lenguaje de programación compilado y estáticamente tipado. Fue creado y lanzado por Google el 2012. Algunas de sus caracteristicas más importantes son:

* Gran velocidad de compilación a lenguaje máquina.
* Alto rendimiento en tareas pesadas.
* Soporte nativo para concurrencia.
* Obliga a implementar buenas prácticas a través de su propia sintaxis.

Go es utilizado por multiples empresas como: 

* Mercado Libre: para procesar miles de request con tan solo una pequeña porción de RAM.
* Twitch: para manejar a sus usuarios de manera concurrente.
* Twitter: para procesar analítica.
* Uber: para mantener la posición de conductores y pasajeros en tiempo real.
* Docker y Kubernetes: para despliegue de Apps.

# Instalación en Linux.

En el primer proyecto con Go que participé hace poco, tuve que utilizar una versión específica. Es por ello que decidí instalar [goenv](https://github.com/ankitcharolia/goenv), un administrador de versiones de Go que facilita su uso con multiples proyectos. Para instalar goenv debes:

1. Crear la carpeta .go en nuestro home:
```sh
mkdir ~/.go
```
2. Descargar goenv y descomprimirlo la carpeta creada:
```sh
wget -O - https://github.com/ankitcharolia/goenv/releases/latest/download/goenv-linux-amd64.tar.gz | tar -xz -C ~/.go
```
3. Guardar las variables de entorno de Go:
```sh
export PATH=$HOME/.go:$PATH >> ~/.bashrc
```
4. Reiniciar la terminal o actualizar la variables de entorno del sistema:
```sh
source ~/.bashrc
```

Luego para instalar Go debes:

1. Listar las versiones de Go disponibles:
```sh
goenv --list-remote
```
2. Instalar Go:
```sh
goenv --install 1.22.3
```
3. Seleccionar la version de Go a utilizar:
```sh
goenv --use 1.22.3
```
4. Reiniciar la terminal o actualizar la variables de entorno del sistema:
```sh
source ~/.bashrc
```
5. Verifica la versión instalada:
```sh
go version
```
Una vez terminada la instalación, Go estará listo para ser usado.

# Primeras lineas de código.

Vamos a crear nuestro primer programa en Go usando el clásico "Hello World":

1. Creamos la carpeta de nuestro proyecto y luego una subcarpeta llamada "src":
```sh
mkdir starting_with_go
cd starting_with_go
mkdir src
```
2. Creamos el archivo principal:
```sh
touch main.go
```
3. Vamos a nuestro editor de texto favorito. En mi caso utilizo VSCode con la extensión de Golang:
```sh
cd ..
code .
```
![Imgur](https://i.imgur.com/lDDqEdj.png)

El punto central de cualquier programa en Go es el package. Un package es el nombre de la carpeta donde esta guardado el archivo. Para el archivo principal el package va a ser main:
```go
package main
```
Luego declaramos la función principal que va a ejecutar el codigo y le agregamos una impresión de consola usando el paquete "fmt":
```go
package main

func main(){
  fmt.Println("Hello World")
}
```
Cabe destacar que al guardar el archivo, la extensión de Go de VSCode nos agregara la importación del paquete "fmt". Go nos obliga a tener buenas prácticas de código. Si no tuvieramos la extensión, para ordenar y formatear el código se utiliza el comando:
```sh
go fmt -w main.go
```
El código nos quedara así:
```go
package main

import "fmt"

func main(){
  fmt.Println("Hello World")
}
```
Compilamos nuestro código:
```sh
go build src/main.go
```
Esto nos va a crear un archivo llamado "main", el cual podemos ejecutar:
```sh
./main
```
En Go existe otra opción de ejecución que se salta el paso de la compilación. Se utiliza para agilizar el desarrollo. Se usa el siguiente comando:
```sh
go run src/main.go
```
![Imgur](https://i.imgur.com/SJXlBKr.png)

Finalmente hemos logrado desarrollar nuestro primer programa en Go. Felicidades ! :)

# Referencias.

[Curso Go](https://platzi.com/cursos/programacion-golang/)