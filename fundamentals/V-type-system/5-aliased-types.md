# Aliased Types

Tipos alias são tipos já existentes com nomes diferentes. Por exemplo, `byte` e `uint8`. Podemos representar como:

```golang
type byte = uint8
```

`rune` e `int32` também são aliases um do outro:

```golang
type rune = int32
```

Isso melhora a legibilidade.

## Exemplo

```golang

package main

func main(){
    var (
        byteValue byte
        uintValue uint8
        intVal int
    )

    uint8Val = byteVal // isso pode ser feito por serem aliases, não por terem apenas a mesma base

    var (
        runeValue rune
        int32Value int32
    )

    runeVal = int32Val
}
```
