---
title: 'Go: Ciclos, Condicionales y Keywords'
description: 'Ciclos, Condicionales y Keywords'
pubDate: '2024-06-19T11:12:34.123Z'
heroImage: 'https://i.imgur.com/ZtD8zaR.png'
categories: ['Go']
tags: ['Go', 'Golang']
authors: ['pabloarak']
---

# Ciclos.

Un ciclo es una tarea que se repite en base a una condición establecida. En los lenguajes de programación existen distintas formas de hacer ciclos. En el caso de Go solo hay 1 ciclo iterativo, el "for":

```go
func main() {
  // For condicional
  for i:= 0; i < 10; i++ {
    fmt.Println(i)
  }
}
```

## For While

Ciclo repetitivo hasta que una condicion se cumpla:

```go
func main() {
  // For while
  counter := 0
  for counter < 10 {
    fmt.Println(counter)
    counter++
  }
}
```

## For Forever

Este ciclo seguira iterando infinitamente o hasta que lo detengamos con un proceso u acción:

```go
func main() {
  // For forever
  counterForever := 0
  for {
    fmt.Println(counterForever)
    counterForever++
  }
}
```

## For Range

Ciclo for basado en un rango previamente definido:

```go
func main() {
  // For range
  numbers := [6]int{0, 1, 2, 3, 4, 5}
  for i, j := range numbers {
		fmt.Printf(i, j)
	}
}
```

## For Functions

Ciclo for basado en funciones:

```go
func main() {
  // For function
  for i := previousFor(); condition(i); i = postFor(i) {
		fmt.Printf(i)
		if i == 7 {
			break
		}
	}
}
```

## For goto TAG

Ciclo for basado en "goto" y tagging:

```go
func main() {
  CICLO:
    for i < 10 {
      if i == 6 {
        i = i + 3
        goto CICLO2
      }
      i++
    }
  CICLO2:
    if i == 9 {
      i = i + 3
      goto CICLO
    }
}
```

# Condicionales

## If

Dada una condicion predeterminada, se ejecuta un ciclo determinado o al reves (si no se cumple la condición). En Go los condicionales se trabajan de la siguiente manera:

```go
import (
	"fmt"
)

func main() {
  value1 := 1
  value2 := 2

  if value1 == 1 {
    fmt.Println("Es 1")
  } else {
    fmt.Println("No es 1")
  }

  if value1 == 1 && value2 == 2 {
    fmt.Println("Es verdad")
  }

  if value1 == 1 || value2 == 2 {
    fmt.Println("Es verdad")
  }
}
```

Un uso común del "if" es para el manejo de errores. Por ejemplo: para convertir un numero que viene en texto a un numero entero. El paquete que se utiliza para hacer esto es el "strconv":

```go
import (
	"fmt"
	"log"
	"strconv"
)

func main() {
  value, err := strconv.Atoi("53")
  if err != nil {
    log.Fatal(err)
  }
  fmt.Println("Value:", value)
}
```

El "value" va a guarda el resultado de la conversión. Si existe un error, "err" va a ser distinto de "nil". Por ejemplo: si le agregamos un texto al método "Atoi", va a lanzar error.

## Switch

Cuando se ejecutan multiples condicionales "if" uno tras otro, se vuelve redundante, dificil de leer y dificulta la mantencion de codigo. Para mejorar esto, en Go se utiliza "switch" para anidar multiples condiciones. Veamos un ejemplo para cuando un numero es par o impar:

```go
import (
	"fmt"
)

func main() {
  switch modulo := 5 % 2; modulo {
    case 0:
      fmt.Println("es par")
    default:
      fmt.Println("es impar")
  }
}
```

Switch tambien se puede usar sin ninguna condicion en el caso de que vayas a iterar sobre una misma variable (solo si conoces los valores que va a tener):

```go
import (
	"fmt"
)

func main() {
  value := 200
  switch {
    case value > 100:
      fmt.Println("Es mayor a 100")
    case value < 0:
      fmt.Println("Es menor a 0")
    default:
      fmt.Println("No condición")
  }
}
```

# Keywords

3 keywords más importantes en Go son: defer, continue y break.

## Defer

Esta keyword jecuta la ultima funcion antes de que todo muera:

```go
import (
	"fmt"
)

func main() {
  defer fmt.Println("Hola")
  fmt.Println("Mundo")
}
```

Un caso de uso puede ser cuando abres una conexion a una base de datos, y utilizas el "defer" para cerrarla al final de la ejecución del código respectivo. El mismo caso puede aplicar para un archivo. Ambos casos son una buena practica para cerrar la conexion o el archivo y no consumir recursos innecesariamente.

Es posible utilizar mas de una sentencia "defer" en una función, pero la buena practica es que uses solo 1.

## Continue

"continue" se utiliza cuando se cumple cierta condicion y deseas que el ciclo continue con la siguiente iteración. Por ejemplo: ocurre 1 error, se registra o se guarda y luego se continua con la siguiente iteración del ciclo.

```go
import (
	"fmt"
)

func main() {
  for i := 0; i < 10; i++ {
    fmt.Println(i)

    if i == 2 {
      fmt.Println("es 2")
      continue
    }
  }
}
```

## Break

Finalmente "break" se usa para cuando se cumple una condicion determinada y no quieres que el ciclo continue:

```go
import (
	"fmt"
)

func main() {
  for i := 0; i < 10; i++ {
    fmt.Println(i)

    if i == 8 {
      fmt.Println("break")
      break
    }
  }
}
```

# Referencias.

[Curso Go](https://platzi.com/cursos/programacion-golang/)
