# Scope

Escopo representa visibilidade. Quem pode ver o quê.

## Declarations

Declarações declaram um nome único relacionados a um escopo. O mesmo nome não pode ser declarado novamente dentro do mesmo escopo.

Toda linha de código pode ter o escopo diferente dependendo da posição em um arquivo Go.

```go
package main
import "fmt" // escopo de arquivo - visível apenas nesse arquivo

const ok = true // escopo de pacote - visíveis em todos os arquivos que pertencem a esse pacote

func main(){ // escopo de pacote
    var ola = "Ola!" // escopo de bloco - só é visível a partir de sua declaração
    fmt.Println(hello, ok)// escopo de bloco
}
```

O exemplo a seguir não funciona:

```go
package main
import "fmt"

func nope(){
    const ok = true
    var hello = "Hello!"
    _ = hello
}
func main(){
    fmt.Println(hello, ok)
}
```

Porque a função `main()` não tem visibilidade da constante `ok` nem da variável `hello`, já que ambas estão visíveis apenas dentro do escopo da função `nope` e fora do escopo da função `main()`.

## Package scope

Nomes são visíveis no decorrer de todo o pacote. Eles podem ser utilizados dentro do arquivo que são declarados e por outros arquivos que estejam dentro do mesmo pacote.

