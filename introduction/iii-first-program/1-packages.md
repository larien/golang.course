# Packages

Todos os arquivos do pacote devem estar no mesmo diretório

```text
$GOPATH/src/github.com/nome-de-usuario/nome-do-projeto/nome-do-pacote
```

Todos os arquivos devem pertencer ao mesmo pacote

```text
package main
package x
package y
```

## Package clause

```text
package main
```

Você pode utilizar uma cláusula de pacote em um arquivo para avisar ao Go a qual pacote aquele arquivo pertence. Ela precisa estar na primeira linha do arquivo e deve ter apenas uma.

No caso do main, podemos fazer algo do tipo:

```go
package main

import "fmt"

func main(){
    fmt.Println("Hello!")
}
```

Podemos ver que esse arquivo está presente no pacote `main` e é executável, por ter a função `main()`. É por ali que seu sistema irá começar a ser executado com `go run` ou `go build`.

## Scope

Cada pacote Go tem seu próprio `escopo`. Por exemplo, funções privadas declaradas no pacote são apenas visíveis naquele pacote e estão no mesmo diretório.

## Running multiple files

É possível executar das seguintes formas:

```go
go run *.go
```

```go
go run main.go arquivo1.go arquivo2.go
```

