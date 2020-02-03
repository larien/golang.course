# Underlying types

Todo tipo em Go tem um tipo fundamental e não há hierarquia de tipos na linguagem.

`type Duration int64` e `type MyDuration Duration` têm o mesmo tipo fundamental, que é `int64`.

## Exemplo

```golang
// main.go
package main

func main(){
    type (
        Gram int
        Kilogram Gram
        Ton Kilogram
    )

    var (
        salt Gram = 100
        apples Kilogram = 5
        truck Ton = 10
    )

    fmt.Printf("salt: %d, apples: %d, truck: %d\n", salt, apples, truck)

    salt = Gram(apples)
    apples = Kilogram(truck)
    truck = Ton(Gram(int(apples)))

    salt = weights.Gram(100) // não funciona, porque o tipo Gram do pacote weights é diferente desse

    fmt.Printf("Type of weights.Gram: %T\n", weights.Gram(1)) // weights.Gram
    fmt.Printf("Type of main.Gram: %T\n", Gram(1)) // main.Gram

    type myGram weights.Gram // tipo novo, pertence à main, é apenas um alias
}

// weights.go
package weights

type (
        Gram int
        Kilogram Gram
        Ton Kilogram
    )
```
