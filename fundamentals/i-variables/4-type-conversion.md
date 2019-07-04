# Type conversion

A conversão de tipos permite que o tipo de um valor seja alterado para outro tipo.

É utilizado da seguinte forma:

```go
type(value)
```

`type` é o nome do tipo. O valor é convertido para esse tipo.

`value` é o valor a ser convertido.

## Why is this necessary

Não é possível usar valores de tipos diferentes juntos.

```go
func main(){
    speed := 100 // int
    force := 2.5 // float64

    speed = speed * force // erro!

    // ...
}
```

É necessário converter os valores explicitamente.

```go
func main(){
    speed := 100 // int
    force := 2.5 // float64

    speed = speed * int(force) // errado!

    // ...
}
```

Quando a conversão é feita de `float64` para `int`, o decimal que houver no ponto flutuante é descartado ou arredondado. Essa é uma operação `destrutiva` e deve-se pensar bastante se isso é realmente necessário.

Isso também não é possível:

```go
func main(){
    speed := 100 // int
    force := 2.5 // float64

    speed = float64(speed) * force // erro!

    // ...
}
```

Porque a operação gera um `float64` e `speed` é um `int`. Logo:

```go
func main(){
    speed := 100 // int
    force := 2.5 // float64

    speed = int(float64(speed) * force)

    // ...
}
```

A ordem das conversões é importante para calcular corretamente. A operação acima também pode ser destrutiva dependendo dos valores definidos.

Tipos similares, como `int` e `int32`, ainda são diferentes e também precisam ser convertidos.

```go
func main(){
    var apple int
    var orange int32

    apple = orange // erro!

    // ...
}
```

Também não é possível converter tipos numéricos para constantes booleanas.

```go
func main(){
    var apple int
    var orange int32

    apple = int(orange)

    isDelicious := bool(orange) // erro!

    // ...
}
```

É possível, no entanto, converter inteiros \(não pontos flutuantes\) para texto.

```go
func main(){
    var orange int32

    orange = 65

    color := string(orange)

    fmt.Println(color) // printa: A

    // ...
}
```

Isso acontece porque uma string é na verdade uma coleção de valores numéricos por trás das cenas. 65 é o valor correspondente da letra A na tabela ASCII e o Go converte o valor de tal forma.

Isso também funciona com um array de bytes:

```go
func main(){
    fmt.Println(string([]byte{104, 105})) // printa: hi
}
```

