# Comments

Utilizado para gerar documentação e/ou explicação sobre seu código. Não são executados pelo compilador.

Existem dois tipos de comentários:

```go
// comentário de linha única

/* comentário
em
bloco
*/
```

## Package documentation

```go
// Package name faz alguma coisa muito legal.
```

## Function documentation

```go
// ola faz alguma coisa muito legal.
func ola(){
    fmt.Println("Olá!")
}
```

## GoDoc

Cria documentação automaticamente. É utilizado executando o comando `go doc`. O comando `go doc -src fmt Println` vai gerar a documentação do código fonte da função `Println` dentro do pacote `fmt`, presente na biblioteca padrão da linguagem.

Também é utilizado para gerar a documentação oficial encontrada em `golang.org/doc`.

