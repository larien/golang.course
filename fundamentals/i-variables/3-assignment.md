# Assignment

Alterar o valor de uma variável após declará-la.

```go
package main

func main(){
    var speed int // 0

    speed = 100 // 100

    speed = speed - 25 // 75

    // ...
}
```

O Go é uma linguagem fortemente tipada. Logo, você não pode designar um valor de tipo diferente ao tipo de variável que vai receber esse valor.

```go
package main

func main(){
    var speed int

    speed = "100" // erro!

    // o exemplo a seguir funciona em Javascript
    var running bool
    running = 1 // erro!
    // mas não em Go!

    var force float64
    speed = force // erro!
    // ambos são numéricos, mas são diferentes

    force = 1 // isso funciona porque o Go converte tipos numéricos automaticamente para inteiro ou ponto flutuante

    // ...
}
```

## Multiple assignments

É possível designar valores diferentes para variáveis diferentes de uma só vez.

```go
package main
import ("fmt"; "time")

func main(){
    var(
        speed int
        now time.Time
    )
    speed, now = 100, time.Now()
    // ...
}
```

É possível fazer isso com diversas variáveis, mas é bom não ter mais do que três para manter a legibilidade.

## Swapping

Também é possível trocar valores de variáveis com esse formato.

```go
package main
import "fmt"

func main(){
    var(
        speed = 100
        prevSpeed = 50
    )
    speed, prevSpeed = prevSpeed, speed
    // ...
}
```

Esses valores são trocados entre si. `speed` recebe o valor de `prevSpeed` e vice-versa.

## Discarding

É possível descartar os valores retornados de funções se você não quiser. Isso é feito com o underscore \_.

```go
_, file := path.Split("path/file.md")
```

