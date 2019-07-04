# Feet to Meters

É possível formatar um ponto flutuante sem a necessidade de usar o número de casas na formatação:

```go
func main(){
    numero := 10.5350000000
    // ao invés de
    fmt.Printf("O número é %.3f\n", numero)

    // utilizar
    fmt.Printf("O número é %g\n", numero)
}
```

O `%g` automaticamente formata o ponto flutuante.

