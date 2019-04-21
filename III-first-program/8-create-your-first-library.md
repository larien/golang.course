# Create your first library

```go
package library // printer/printer.go

func hello(){
    fmt.Println("não exportado")
}
```

```go
package main // printer/cmd/main.go

func main(){
    printer.hello() // erro!
}
```

Para poder ser executado:

```go
package library // printer/printer.go

func hello(){
    fmt.Println("não exportado")
}

// Hello é uma função exportada e mostra "exportado" na tela.
func Hello(){
    fmt.Println("exportado")
}
```

```go
package main // printer/cmd/main.go

import "github.com/usuario/printer"

func main(){
    printer.Hello() // printa: exportado
}
```

Importamos dessa forma porque o Go procura os pacotes importados em `$GOPATH/src/` automaticamente.

Se compilarmos essa biblioteca com o comando `go build`, o Go vai gerar um arquivo compilado `library.a` dentro do pacote `pkg` do projeto.
Ele faz isso para compilar os projetos mais rapidamente.

## Exporting

Exportar permite que um pacote disponibilize suas funcionalidades para outros pacotes.

Não existe `public` ou `private` dentro do Go: para tornar uma função, variável ou constante pública, basta iniciar seu nome com letra maiúscula.

Declarações com letra maiúscula e minúscula são dois objetos diferentes.
