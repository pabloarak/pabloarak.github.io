---
title: 'Go: Arrays, Slices, Maps y Clases'
description: 'Arrays, Slices, Maps y Clases'
pubDate: '2024-07-04T11:12:34.123Z'
heroImage: 'https://i.imgur.com/OHpo6oP.png'
categories: ['Go']
tags: ['Go', 'Golang']
authors: ['pabloarak']
---

# Arrays

Los arrays son inmutables y se declaran de la siguiente forma:

```go
var array [4]int
```

El array por defecto es rellenado con 0. Y podemos editar sus valores de la siguiente forma:

```go
array[0] = 1
array[1] = 2
```

2 funciones muy importantes en Go para el manejor de arrays son:

```go
len(array) // Devuelve la cantidad de elementos que hay en un array.
cap(array) // Devuelve la capacidad maxima de elementos que puede guardar un array.
```

# Slices

Los slices son mutables y similares a los array, pero no se les indica la cantidad de valores que van a tener:

```go
slice := []int{0,1,2,3,4,5,6}
```

Algunos ejemplos para interactuar con un slice son:

```go
slice[0]
slice[:3] // Se accede a los elementos hasta el indice 3.
slice[2:4] // Se accede a los elementos entre el 2do y 4to (el 2do elemento no se incluye).
slice[4:] // Se accede a los elementos del 4to en adelante.
```

Una de las formas de editar un slice es usando el método append:

```go
slice = append(slice, 7) // Agrega el elemento 7.
```

Con append también podemos agregar otra lista:

```go
newSlice := []int{8,9,10}
slice = append(slice, newSlice...) // Con los "..." en lugar de agregar una nueva lista, agrega los elementos de esa lista de forma independiente.
```

Ademas, usando "range" podemos recorrer un slice:

```go
func main() {
	salice := []string{"hello","how","are","you"}

	for i, value := range slice { // Si no deseamos el indice, lo podemos reemplazar por _
		fmt.Println(i,value) // Si solo quieres saber el indice, solo colocamos el indice "i"
	} 
	
}
```

# Maps

En Go existe la estructura de datos "llave-valor" y se llaman maps. Para crear un map en Go se utiliza make:

```go
m := make(map[string]int)
```

Y podemos editar sus valores de la siguiente forma:

```go
m["key1"] = "value1"
m["key2"] = "value2"
```

En el caso de los maps, no hay separacion por coma, si no un espacio.

Usando "range" podemos recorrer la lista del map y obtener las llaves y valores respectivos:

```go
for i, v := range m {
	fmt.Println(i, v)
}
```

Al imprimir los valores, podras notar que se muestran de forma aleatoria. Si deseas un orden, se recomienda el uso de slices.

Si necesitamos un valor especifico, lo podemos obtener de la siguiente forma:

```go
value := m["key1"]
```

Si ingresamos una llave que no esta en el map se imprimira un valor por defecto. Si el valor que le agregamos en la definicion es un "int", se imprimira un 0. Para saber si un valor existe en el map, usamos la palabra "ok":

```go
value, ok := m["notExistValue"]
```

Si existe, "ok" devolvera "true". Y si no, devolvera "false".

Los maps son una estructura de datos muy conveniente cuando tienes 2 listas que se relacionan entre si. Son mas eficientes que los arrays y los slices, debido a que de forma nativa implementan concurrencia para poder interactuar entre las operaciones que se utilizarán.

# Clases

En Go no existe una forma de crear clases como en otros lenguajes de programación. En su lugar se utilizan los "structs". Por ejemplo si necesitamos una clase "car", la podemos crear de la siguiente forma: 

type es el keyword para decir tipo de dato, y struct indica al runtime que es un struct (coleccion de campos)

```go
type car struct {
	// attributes
	brand string
	year int
}

func main() {
	// Instance creation
	myCar := car{brand: "Ford", year: 2020}

	// Another way
	var otherCar car
	otherCar.brand = "Ferrari"
}
```

Si no se especifica un valor en un atributo, se le asigna un valor por defecto (por ejemplo: en caso de un "int" se le asigna un 0).

En otros lenguajes existen keywords especiales para indicar si una variable, funcion, aspecto o tipo de dato, tiene acceso publico o privado al resto de un paquete. En Go, esto no se maneja con keywords, si no mas bien con la primera letra del nombre. Si es mayuzcula, es pública. Si es minuscula, es privada. Creemos un paquete para ejemplificar lo descrito:

```sh
touch mypackage.go
```

En la primera linea de la clase indicamos el nombre del paquete:

```go
package mypackage

type car struct {
	brand string
	year int
}
```

Por el simple hecho de que estan en minusculas, no podemos acceder a la clase ni a sus atributos. Son privados. Para hacerlos publicos, debemos colocar la primera letra en mayuzcula:

```go
package mypackage
// CarPublic descripcion (buena practica)
type CarPublic struct {
	Brand string
	Year int
}
```

Cuando exportamos un paquete publico, Go nos obliga a agregarle un comentario al comienzo de la creación del struct (como buena práctica). Luego para utilizar los paquetes en otro archivo, lo podemos hacer de la siguiente forma:

```go
import {pk "golang experience project/src/mypackage"}

func main() {
	var myCar pk.CarPublic
	myCar.Brand = "Ferrari"
}
```

Tambien podemos crear funciones de acceso publico o privado

```go
func PrintMessage() {
	fmt.Println("Hola")
}
```

# Referencias.

[Curso Go](https://platzi.com/cursos/programacion-golang/)
