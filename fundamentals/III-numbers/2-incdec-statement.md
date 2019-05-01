# IncDec Statement

Incrementa ou decrementa valores numéricos em um.

batata++ batata--

```go
func main(){
    var n int

    n = n + 1

    // mesma coisa que
    n += 1

    // mesma coisa que
    n++ // declaração incdec

    5 + n-- // erro! n-- é uma expressão, não um valor

    n-- // também é possível
}
```

Não é possível executar uma operação com as declarações incdec porque dificulta a legibilidade do código. Por isso, os criadores da linguagem decidiram tornar uma declaração, não uma expressão calculável.

## Assignment operations

```go
func main(){
    var area float64

    area = area - 10
    area = area + 10
    area = area * 10
    area = area / 2

    // podem ser simplificados para

    area -= 10
    area += 10
    area *= 10
    area /= 10
}
```
