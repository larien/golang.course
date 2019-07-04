# Importing

Permite que um arquivo utilize funcionalidades de um arquivo de biblioteca.

Funciona como se você tivesse declarado o que está dentro dos arquivos do pacote importado no seu próprio arquivo.

```go
// arquivo.go
import "fmt"
import "errors"
import "time"
```

Todos esses pacotes são compilados junto do arquivo binário executável final.

## File scope

Visível no decorrer do arquivo.

Pacotes importados são visíveis apenas dentro do arquivo em que foram importados.

O seguinte exemplo não funciona:

```go
// arquivo.go
package main

func ola(){
    fmt.Println("Ola!")
}
```

Porque, apesar do arquivo `main.go` poder ter importado o pacote `fmt`, esse arquivo não importou. Logo, ele não sabe o que `Println` faz até que o pacote `fmt` seja importado:

```go
// arquivo.go
package main
import "fmt"

func ola(){
    fmt.Println("Ola!")
}
```

## Renaming imported packages

É possível importar diversos pacotes em um mesmo arquivo, mas todos precisam ter o nome único \(não serem repetidos\). Se houver um pacote de mesmo nome, é possível renomeá-los da seguinte forma:

```go
import "fmt"
import f "fmt"

func main(){
    fmt.Println("Ola!")
    f.Printf("Oi!\n")
}
```

## Redeclare names

O seguinte exemplo é possível:

```go
package awesome

import "fmt"

// declared at the package scope
var enabled bool

func block() {
    // also declared in the block scope
    var enabled bool

    var counter int
    fmt.Println(counter)
}
```

Isso porque ambos estão em escopos diferentes. O segundo `enabled` sobrescreve o primeiro durante o mesmo nível dele. No caso, para a função `block()`, a partir da hora que o `enabled` é declarado, o programa reconhece esse nome como escopo de função até que essa função acabe.

