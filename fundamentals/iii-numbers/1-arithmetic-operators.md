# Arithmetic operators

## Concept

`8 * 2`

| nome | operador | expressão | resultado |
| :--- | :--- | :--- | :--- |
| negação | - | -\(-2\) | 2 |
| produto | \* | 8 \* -4.0 | -32.0 |
| quociente | / | -4 / 2 | -2 |
| resto | % | 5 % 2 | 1 |
| soma | + | 1 + 2.5 | 3.5 |
| diferença | - | 2 - 3 | -1 |

O resto só funciona com inteiros.

## Code

```go
func main() {
    var (
        minhaIdade = 30
        suaIdade = 45
        media float64
    )
    media = minhaIdade + suaIdade // erro!
}
```

`minhaIdade` e `suaIdade` são literais de inteiro. Seu resultado também é um literal de inteiro, que não pode ser atribuído a um `float64`. Aí ocorre uma incompatibilidade de tipos. Isso pode ser corrigido da seguinte forma:

```go
func main() {
    var (
        minhaIdade = 30
        suaIdade = 45
        media float64
    )
    media = float64(minhaIdade + suaIdade) / 2
}
```

## Float inaccuracy

O valor em ponto flutuante que utilizamos pode ter valores relevantes em inúmeras casas decimais. Como raramente precisamos de várias casas decimais, esses valores são arredondados e esses valores são perdidos.

```go
func main() {
    ratio := 1.0 / 10
    fmt.Printf("%.60f", ratio)
    // printa 0.100000000000000005551115123125782702118158340454101562500000
}
```

No caso acima, esse primeiro 5 pode ser relevante.

Operações entre `int` e `float64` geram um `float64`.

```go
func main() {
    fmt.Println("soma: ", 3+2) // soma: int
    fmt.Println("soma: ", 2+3.5) // soma: float64
    fmt.Println("dif: ", 3-1) // diferença: int
    fmt.Println("dif: ", 3-0.5) // diferença: float64
    fmt.Println("prod: ", 4*5) // produto: int
    fmt.Println("prod: ", 5*2.5) // produto: float64
    fmt.Println("quoc: ", 8/2) // quociente: int
    fmt.Println("quoc: ", 8/1.5) // quociente: float64

    fmt.Println("resto: ", 10%3) // resto: apenas inteiros
    // 10 dividido por 3 dá 3 e >sobra< 1
    fmt.Println("resto: ", 10.0%3) // erro!
}
```

## Operator Precedence

A precedência de operação determina a ordem em que os cálculos são feitos. No geral, as expressões são calculadas da esquerda para a direita, a não ser que um operador à direita tenhha maior precedência que o da esquerda.

| nome | expressão | igual a | resultado | motivo |
| :--- | :--- | :--- | :--- | :--- |
| multiplicação | 2 + 2 \* 4 / 2 | 2 + \(\(2 \* 4\) / 2\) | 10 | \* tem maior procedência que + |

É possível agrupar uma expressão dentro de parênteses. Os parênteses têm maior precedência que a \* ou /, então são efetuados anes.

Precedência: \(\), ^, / \*, + -

