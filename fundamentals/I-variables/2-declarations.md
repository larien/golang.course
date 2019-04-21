# Declarations

É necessário declarar uma variável antes de utilizá-la.

Sintaxe de declaração:

```go
var speed int
```

- var: diminutivo para variável. É utilizado para declarar variáveis.
- speed: nome da variável. Também conhecido como "identificador". Uma variável nomeia um valor.

Um nome deve sempre começar com uma letra ou sublinhado \_. Pode ser uma letra maiúscula ou minúscula. Também pode começar com letras unicode.

| Pode    | Não pode | Regra                  |
| ------- | -------- | ---------------------- |
| speed   | -------- | ter letra minúscula    |
| SpeeD   | -------- | ter letra maiúscula    |
| \_speed | -------- | começar com sublinhado |
| 速度    | -------- | ter caractere unicode  |
| ------- | 3speed   | começar com número     |
| ------- | !speed   | começar com pontuação  |
| ------- | spe!ed   | ter pontuação          |
| ------- | 3speed   | ser palavra-chave      |

Essas regras existem para prevenir ambiguidade e ajudar o compilador do Go a entender o que você quer.

- int: diminutivo para inteiro. Aí fica o tipo estático da variável. No Go, toda variável e valor tem um tipo.

Uma variável é inicializada com seu valor padrão/zerado.

> Existe apenas duas coisas difíceis na Ciência da Computação: invalidação de cache e dar nomes às coisas.

- [Phil Karlton](https://martinfowler.com/bliki/TwoHardThings.html)

## int

Inteiros são mais utilizados para cálculos numéricos.

```go
var nFiles int
var counter int
var nCPU int
```

## float64

Pontos flutuantes também são usados em cálculos nuḿericos, mas mais quando é necessário mais precisão.

```go
var heat float64
var ratio float64
var degree float64
```

## bool

Booleanos são muito utilizados para representar estado de `on/off` ou `válido/inválido`.

```go
var off bool
var valid bool
var closed bool
```

## string

Strings são utilizadas para representar textos.

```go
var msg string
var name string
var text string
```

## Zero values

Uma variável vazia recebe um valor zerado dependendo de seu tipo.

```go
package main
import "fmt"

func main(){
    var speed int
    var heat float64
    var off bool
    var brand string

    fmt.Println(speed) // printa: 0
    fmt.Println(heat) // printa: 0
    fmt.Println(off) // printa: false
    fmt.Printf("%s\n", brand) // printa: ""
}
```

| tipo      | valor |
| --------- | ----- |
| booleanos | false |
| numérico  | 0     |
| strings   | ""    |
| ponteiros | nil   |

## Unused variables

Toda variável a escopo de bloco deve ser usada.

Variáveis não utilizadas geram problemas de manutenção de código.

```go
package main
import "fmt"

func main(){
    var speed int // erro!
}
```

No entanto, se a variável for declarada a escopo de pacote:

```go
package main
import "fmt"

var speed int

func main(){
}
```

O compilador não vai reclamar. Isso acontece porque não está claro para ele em que ponto do sistema essa variável vai ser utilizada.

## Blank identifier

```go
package main
import "fmt"

func main(){
    var speed int

    _ = speed
}
```

Esse underscore \_ "engole" o valor da variável, tipo um buraco negro.

## Multiple declarations

Declarar várias variáveis de uma só vez.

```go
package main

func main(){
    var (
        speed int
        heat float64

        off bool
        brand string
    )
    // ...
}
```

É bom utilizar essa forma para agrupar a declaração de variáveis em apenas um lugar (geralmente no início dad função) ou para simbolizar que aquelas variáveis estão relacionadas entre si.

Também é possível declarar mais de uma vez as variáveis que tiverem o mesmo tipo:

```go
package main

func main(){
    var speed, velocity int
    // ...
}
```

Essa forma também é chamada de declaração paralela e é a mesma coisa que:

```go
package main

func main(){
    var speed int
    var velocity int
    // ...
}
```

## Naming things

Não idiomático = uso não ideal da linguagem

Ter um nome verboso é útil se o escopo de utilização for grande, mas não se o escopo é pequeno, como o de uma função. Nesses casos, uma função assim:

```go
func Read(buffer *Buffer, inBuffer []byte) (size int, err error){
    if buffer.empty(){
        buffer.Reset()
    }

    size = copy(
        inBuffer,
        buffer.buffer[buffer.offset:]
    )

    buffer.offset += size
    return size, nil
}
```

É menos idiomático que:

```go
func Read(b \*Buffer, p []byte) (n int, err error){
    if b.empty(){
        b.Reset()
    }

    n = copy(p, b.buf[b.off:])

    b.off += n

    return n, nil
}
```

É importante levar isso em conta para melhor mantenebilidade e legibilidade do seu código.

Outros exemplos:

```go
var s string // string
var i int // index
var num int // number
var msg string // message
var v string // value
var val string // value
var fv string // flag value
var err error // error value
var args []string // arguments
var seen bool // has seen?
var parsed bool // parsing ok?
var buf []byte // buffer
var off int // offset
var op int // operation
var opRead int // read operation
var l int // length
var n int // number or number of
var m int // another number
var c int // capacity
var c int // character
var a int // array
var r rune // rune
var sep string // separator
var src int // source
var dst int // destination
var b byte // byte
var b []byte // buffer
var buf []byte // buffer
var w io.Writer // writer
var r io.Reader // reader
var pos int // position
```

E a lista continua.

## Naming conventions

- Usar apenas as primeiras letras das palavras.

```go
var fv string // flag value
```

- Usar poucas letras em escopos menores.

```go
var bytesRead int // número de bytes lidos, não usar
var n int // número de bytes lidos, usar
```

- Usar palavras completas em escopos maiores.

```go
package main

var fileClosed bool
```

- Utilizar mixedCaps: se for necessário utilizar mais de uma palavra no nome, inicie as seguintes com maiúsculo e continue em minúsculo. Não utilize underscore \_.

```go
var file_closed bool // NÃO!
var fileClosed bool // Sim!
```

- Usar todas as letras em maiúsculo para acrônimos.

```go
var localApi bool // NÃO!
var localAPI bool // Sim!
```

- Não repita nomes desnecessariamente.

```go
player.PlayerScore // NÃO!
player.Score // Sim!
```

## Initialization

Quando você quer declarar uma variável e já sabe seu valor (ou expressão).

```go
package main

func main(){
    var safe bool = true
    // ...
}
```

O seguinte também funciona:

```go
package main

func main(){
    var safe = true
    // ...
}
```

Graças à inferência de tipos do Go. Isso significa que o Go pode adivinhar o tipo automagicamente deduzindo o tipo do valor. Depois, utiliza esse tipo adivinhado para declarar a variável.

## Short declaration

Não é nem necessário utilizar `var`. Utilizar apenas dois pontos antes do igual já é suficiente:

```go
package main

func main(){
    safe := true
    // ...
}
```

Com essa sintaxe, você consegue declarar e inicializar a variável.

Isso só é possível a escopo de função. A escopo de pacote, esse tipo de declaração vai gerar um erro.

```go
package main

safe := false // erro!
var safe = true // isso pode!

func main(){
    // ...
}
```

A escopo de pacote, você só pode utilizar declarações que iniciam com uma palavra-chave.

## Multiple short declarations

É possível declarar e inicializar várias variáveis ao mesmo tempo utilizando o formato curto.

```go
package main

func main(){
    safe, speed := true, 50
    // safe = true, bool
    // speed = 50, int

    firstName, lastName := "Nikola", "Tesla"
    // firstName = Nikola, string
    // lastName = Tesla, string

    birthYear, deathYear := 1856, 1943
    // birthYear = 1856, int
    // deathYear = 1943, int

    on, off := true, false
    // on = true, bool
    // off = false, bool

    degree, ratio, heat := 10.55, 30.5, 20.
    // degree = 10.55, float64
    // ratio = 30.5, float64
    // heat = 20, float64

    // ...
}
```

Não há limite para a quantidade de declarações, mas mantenha poucas declarações para melhor legibilidade.

## Redeclaration

A redeclaração te permite atribuir novos valores a variáveis existentes. A declaração curta também pode ser utilizada com variáveis existentes. O programa a seguir funciona:

```go
package main

func main(){
    var safe bool
    safe, speed := true, 50 // redeclaração
    // ...
}
```

Nesse exemplo, `safe` já existe e o mesmo espaço na memória é utilizado, enquanto que `speed` é uma variável nova e um novo espaço na memória é alocado.

A regra é que pelo menos uma das variáveis nesse formato de declaração deve ser nova.

O seguinte não é possível:

```go
package main

func main(){
    safe := true
    safe := false // erro!
    // ...
}
```

Isso sim:

```go
package main

func main(){
    safe := true
    safe = false
    // ...
}
```

## Short vs. Normal

### Normal

- Se você não sabe o valor inicial
- Quando você precisa de uma variável a escopo de pacote
- Quando você quer agrupar variáveis para melhorar a legibilidade

### Short

- É o estilo mais utilizado e preferido
- Se você sabe o valor inicial
- Para manter o código consiso
- Para redeclaração

Tomar cuidado com [shadow declaration](https://rpeshkov.net/blog/golang-variable-shadowing/).
