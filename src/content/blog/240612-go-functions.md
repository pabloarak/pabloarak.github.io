---
title: 'Go: Funciones'
description: 'Funciones en Go'
pubDate: '2024-06-12T12:50:34.123Z'
heroImage: 'https://i.imgur.com/UazuP3U.png'
categories: ['Go']
tags: ['Go','Golang']
authors: ['pabloarak']
---
# Funciones.

Las funciones son una buena práctica en programación que te ayudan a transformar tu código repetitivo en una función que puedes usar en cualquier punto de tu código. Tu código se hace mas corto y facil de leer para otras personas. Por ejemplo tenemos la siguiente función:

```go
func main() {
  result1 := 1 + 1
  fmt.println("Result 1 = ", result1)
  result2 := 2 + 2
  fmt.println("Result 2 = ", result2)
  result3 := 3 + 3
  fmt.println("Result 3 = ", result3)
}
```

Como pueden ver estamos repitiendo el mismo comando, cuando lo único que cambia es el parametro. Es aquí donde podemos utilizar una función que reciba dos parametros de tipo int:

```go
func sum(a, b int) {
  sumResult := a + b
  fmt.Printf("Result = ", sumResult)
}
```

```go
func main() { 
  sum(1,1)
  sum(2,2)
  sum(3,3)
}
```

Por otro lado, si necesitamos que la función nos retorne un valor, escribimos su tipo despues de los parametros:

```go
func multiply(a int) int { 
  return a * 2;
}

func main() {
  value := multiply(2)
  fmt.Println("Value: ", value)
}
```

También podemos retornar 2 o más valores, agregandolos entre parentesis despues de los parametros:

```go
func doubleReturn(a int) (c, d int) {
  return a, a*2
}

func main() {
  value1, value2 := doubleReturn(2)
  fmt.Println("value1 y value2", value1,value2)
}
```

Supongamos que en una funcion necesitas un valor pero no el otro. En Go puedes usar el simbolo piso "_" para ignorar el segundo valor:

```go
value1, _ := doubleReturn(2)
```

Con el uso de funciones cada operación puede estar encapsulada en una función separada, mejorando la estructuración del código. Esto también permite mayor legibilidad por que delegamos ciertas tareas a funciones especificas. Finalmente podemos reutilizar las funciones en cualquier parte del programa, lo cual nos permite a la vez facilitar su edición y mejora.

# Referencias.

[Curso Go](https://platzi.com/cursos/programacion-golang/)