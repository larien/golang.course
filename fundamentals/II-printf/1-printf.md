# Printf

Printa a saída de forma formatada.

```go
func main(){
    var brand string

    fmt.Printf("%q\n", brand) // printa: ""
}
```

```go
func main(){
    var brand = Google

    fmt.Printf("%q\n", brand) // printa: "Google"
}
```

```go
func main(){
    var brand = Google

    fmt.Printf("%s\n", brand) // printa: Google
}
```

`"%q\n"` - texto de formatação: determina "o quê" e "como" o texto será printado
`%q` - verbo
`\n` - sequência de escape
`brand` - valor substituto: substitui o(s) verbo(s) dentro do texto de formatação

## Println vs Printf

```go
// total: 2350 success: 543 / 433

fmt.Println("total:", ops, "success:", ok, "/", fail)

fmt.Printf("total: %d success: %d / %d\n", ops, ok, fail)
```
