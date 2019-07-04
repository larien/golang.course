# Expressions

Computa um ou diversos valores.

Deve ser utilizada dentro ou junto de uma declaração.

O exemplo abaixo não funciona:

```go
package main
import "fmt"

func main(){
    "Olá!"
}
```

Porque `"Olá!"` é uma expressão e não pode ser utilizada sozinha sem uma declaração.

Algumas declarações \(`func`\) também podem agir como expressões.

```go
package main
import (
    "fmt"
    "runtime"
)

func main(){
    fmt.Println("Olá!") // "Olá" é a expressão
    fmt.Pritln(runtime.NumpCPU())
}
```

No exemplo acima, há uma função dentro de outra função. `NumCPU` é uma expressão que retorna um valor e `Println` é uma declaração que printa esse valor. Logo, tudo o que retorna um valor pode ser utilizado como expressão.

O Go adiciona ponto-e-vírgula automaticamente entre cada declaração.

## Operators

É possível combinar expressões dentro de uma declaração com operadores:

```go
package main
import (
    "fmt"
    "runtime"
)

func main() {
    fmt.Println(runtime.NumCPU() + 10)
}
```

