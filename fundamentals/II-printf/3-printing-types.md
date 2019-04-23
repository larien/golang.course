# Printing types

Você pode utilizar o `printf` para printar os tipos de valores (variáveis, constantes etc.)

```go
package main
import "fmt"

func main(){
    var speed int
    var heat float64
    var off bool
    var brand string

    fmt.Printf("%T\n", speed) // printa: int
    fmt.Printf("%T\n", heat) // printa: float64
    fmt.Printf("%T\n", off) // printa: bool
    fmt.Printf("%T\n", brand) // printa: string
}
```

Para printar qualquer valor, utilize o formatador `%v`:

```go
package main
import "fmt"

func main(){
    var planet = "venus"

    fmt.Printf("Planet: %v\n", planet) // printa: venus
}
```

## Argument index

É possível acessar os argumentos já utilizados no mesmo texto com a indexação de argumentos.

```go
// ...
fmt.Printf("%v está a %v kms de distância. Cara! %[2]v kms! %[1]v OMG!\n", planet, distance)
```

`%[2]` pega o segundo argumento (`distance`), enquanto que `%[1]v` pega o primeiro (`planet`).

```go
// printa: venus está a 261000000 kms de distância. Cara! 261000000 kms! venus OMG!
```

## Types

```go
package main
import "fmt"

func main(){
    var (
        planet = "venus"
        distance = 261
        orbital = 224.701
        hasLife = false
    )

    fmt.Printf("%s\n", planet)
    fmt.Printf("%d\n", distance)
    fmt.Printf("%f\n", orbital) // printa: 224.701000
    fmt.Printf("%.3f\n", orbital) // printa: 224.701
    fmt.Printf("%t\n", hasLife)
}
```

O Go compara o valor a ser formatado com seu verbo correspondente. Se um verbo for usado para o tipo incorreto, o Go vai avisar.

## Printing precision

```go
package main
import "fmt"

func main(){
    orbital := 224.701

    fmt.Printf("%f dias\n", orbital) // printa: 224.701000 dias
    fmt.Printf("%.0f dias\n", orbital) // printa: 224 dias
    fmt.Printf("%.1f dias\n", orbital) // printa: 224.7 dias
    fmt.Printf("%.2f dias\n", orbital) // printa: 224.70 dias
    fmt.Printf("%.3f dias\n", orbital) // printa: 224.701 dias
    fmt.Printf("%.4f dias\n", orbital) // printa: 224.7010 dias
    fmt.Printf("%.5f dias\n", orbital) // printa: 224.70100 dias
    fmt.Printf("%.6f dias\n", orbital) // printa: 224.701000 dias
}
```
