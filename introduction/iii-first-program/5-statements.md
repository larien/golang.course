# Statements

Dizem ao Go para executar alguma coisa e podem mudar o fluxo de execução do código. Logo, controlam o fluxo de execução.

Uma declaração é executada por vez \(a não ser que utilize ponto-e-vírgula\).

No exemplo a seguir, quase todos são declarações, menos a expressão `Olá!`.

```go
package main
import "fmt"

func main(){
    fmt.Println("Olá!")
}
```

## Execution flow

```go
package main # 1
import "fmt" # 2

func main(){ # 3
    if 5 > 1 { # 4
        fmt.Pritln("maior") # 5
    } else {
        fmt.Pritln("menor")
    }
    # 6
}
```

Utilizar duas declarações na mesma linha também é possível:

```go
package main
import "fmt"

func main(){
    fmt.Println("Olá!"); fmt.Println("Tudo bem?")
}
```

Mas ainda existem duas declarações aqui.

