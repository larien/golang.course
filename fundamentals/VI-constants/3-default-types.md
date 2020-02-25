# Default types


O GO converte constantes sem tipo para constantes com tipo quando necessário:

```go
const min int32 = 1

max := 5 + min // tipo: int32
```

O Go também tem valores padrões para cada tipo.

```go
const min = 1

max := 5 + min // tipo: int
```


```go
i := 42 // int
f := 3.14 // float64
b := true // bool
s := "Hello" // string

```

O Go precisa converter o valor float sem tipo (quando não definimos explicitamente um valor para a variável ou constante) para seu tipo padrão.


```go

```