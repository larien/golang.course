# Project: Greeter

```go
var Args []string
```

Quanto você executa um programa em Go, o Go coloca os argumentos da linha de comando dentro dessa variável automaticamente.

É possível acessar os argumentos da seguinte forma:

```bash
go run main hi yo
```

```go
Args[0] = .../exe/main // caminho do programa
Args[1] = "hi"
Args[2] = "yo"
```

## Greeter 1

```go
package main

import (
    "fmt"
    "os"
)

func main(){
    fmt.Printf("%+v\n", os.Args)

    fmt.Println("Caminho: ", os.Args[0])
    fmt.Println("Primeiro argumento: ", os.Args[1])
    fmt.Println("Segundo argumento: ", os.Args[2])
    fmt.Println("Terceiro argumento: ", os.Args[3])

    fmt.Println("Numero de argumentos: ", len(os.Args))
}
```

### Running

```bash
go build -o greeter // cria: ./greeter
./greeter hi hello hey

Caminho: ./greeter
Primeiro argumento: hi
Segundo argumento: hello
Terceiro argumento: hey
Numero de argumentos: 4
```

## Greeter 2

```go
package main

import (
    "fmt"
    "os"
)

func main(){
    name := os.Args[1]
    fmt.Println("Olá, grande", name, "!")

    name, age := "Gandalf", 2019
    fmt.Println("Meu nome é", name)
    fmt.Println("Minha idade é", name)
    fmt.Println("BTW, you shall NOT pass!")
}
```

### Running

```bash
go build -o greeter // cria: ./greeter
./greeter jack

Olá, grande jack!
Meu nome é Gandalf
Minha idade é 2019
BTW, you shall NOT pass!
```

