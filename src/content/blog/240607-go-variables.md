---
title: 'Go: variables, constantes y tipos de datos'
description: 'Variables, constantes y tipos de datos en Go'
pubDate: '2024-06-07T23:21:34.123Z'
heroImage: 'https://i.imgur.com/cCVc0US.png'
categories: ['Go']
tags: ['Go','Golang']
authors: ['pabloarak']
---
# Variables.

Una variable es un valor que puede variar en el tiempo. En Go hay 3 formas de definir variables:

```go
name := value
```

Los : indican que es variable no ha sido declarada anteriormente. Esto creara la variable y le asignara el valor dado. Esto quiere decir que se declara y se le asigna un valor sin decirle el tipo de dato.

```go
var name type = value
```

Le decimos el tipo de dato y le asignamos el valor.

```go
var name type
```

Las variables sin valor asignado tendran un "zero values" por defecto. Dependiendo del tipo, Go puede asignar los siguientes valores:

```go
var a int     // 0
var b float64 // 0
var c string  // ""
var d bool    // false
```

Go se da cuenta cuando estas declarando variables y no las usas. Si ejecutas el programa te va a lanzar un error. Te va a decir cual es el error y en que linea está. Esto lo hace para cuidar el almacenaje en memoria.

# Constantes.

Una constante es un valor que nunca va a cambiar en el tiempo. Para declarar una constante se hace de la siguiente manera:

```go
const name type = value
```

Otra forma de declaración sin tipo de dato seria así:

```go
const name = value
```

# Tipos de datos.

El uso de tipos de datos en Go nos permite mejorar la performance de nuestro programa. En Go tenemos los siguientes tipos:

##### Enteros:

* byte (uint de 8 bits)
* rune (int de 32 bits)

* int (32 o 64 bits dependiendo del sistema operativo)
* int8 (8 bits de -128 a 127)
* int16 (16 bits de -2^15 a 2^15-1)
* int32 (32 bits de -2^31 a 2^31-1)
* int64 (64 bits de -2^63 a 2^63-1)

* uint (32 o 64 bits dependiendo del sistema operativo)
* uint8 (8 bits 0 a 127)
* uint16 (16 bits 0 a 2^15-1)
* uint32 (32 bits 0 a 2^31-1)
* uint64 (64 bits 0 a 2^63-1)

La "u" antes del "int" hace referencia a "Unsigned", es decir, sin signo o sin valor negativos. Este tipo se utiliza cuando sabemos que tendremos un valor positivo. Esto nos ayuda así nos ayuda a optimizar memoria.

##### Decimales:

* float32 (32 bits de 1.18e^-38  a +/- -3.4e^38)
* float64 (64 bits de 2.23e^-308  a +/- -1.8e^308)

##### Textos y booleanos: 

* string ("")
* bool (true o false)

##### Números complejos:

* complex64 (real e imaginario float32)
* complex128 (real e imaginario float64)

# Referencias.

[Curso Go](https://platzi.com/cursos/programacion-golang/)