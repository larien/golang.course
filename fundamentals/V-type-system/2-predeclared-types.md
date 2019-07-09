# Predeclared types

Um tipo pré-declarado é um tipo nativo (vem junto do próprio compilador) que você pode usar em qualquer lugar, fora do escopo.

Um tipo pré-declarado tem um nome (como um nome de variável) que pode ser usado em qualquer escopo e você não precisa declarar e uma representação que determina como você vê e como utilizá-lo no código. Também representa qual valor e qual tipo pode representar. Além disso, também tem um tamanho (em bytes). O tamanho diz o quanto de memória esse tipo precisa para ser armazenado e também determina o range de valores que pode representar.

Já utilizamos esses tipos pré-declarados antes:

## Tabela de tipos pré-declarados

| nome            | representação               | tamanho em bytes   |
| --------------- | --------------------------- | ------------------ |
| bool            | true ou false               | 1 byte             |
| int             | depende se int32 ou int64   | 32 bits ou 64 bits |
| int8            | -128 a 127                  | 8 bits/1 byte      |
| int16           | -32.768 a 32.767            | 16 bits/2 bytes    |
| int32 (rune)    | -2 a +2 bilhões             | 32 bits/ 4 bytes   |
| int64           | -9 a +9 quintilhões         | 64 bits/8 bytes    |
| uint            | depende se uint32 ou uint64 | 32 bits ou 64 bits |
| uint8 (byte)    | 0 a 255                     | 8 bits/1 byte      |
| uint16          | 0 a 65.535                  | 16 bits/2 bytes    |
| uint32 (rune)   | 0 a 4 bilhões               | 32 bits/ 4 bytes   |
| uint64          | 0 a 18 quintilhões          | 64 bits/8 bytes    |
| float32         | 3.1415927                   | 32 bits/4 bytes    |
| float64         | 3.141592653589793           | 64 bits/8 bytes    |
| complex64       | dois float32                |                    |
| complex128      | dois float64                |                    |
| string ([]byte) | "hello köstebek"            |                    |

Int pode ter o tamanho de 32 bits ou 64 bits (dependendo da máquina).

String literals são codificados em UTF-8 e por isso podem receber caracteres especiais como "hello köstebek".

```go
"Isso é um string literal"
`Isso também é`
```

String values podem ser codificados por qualquer coisa

```go
var stringValue string
// essa variável tem um valor de string
// mas também pode ter qualquer codificação
```

## Inteiros

Os tipos `int8`, `int16`, `int32` e `int64` armazenam valores inteiros. O bit-size, que é o número em frente à palavra reservada, representa o range de valores que o tipo representa. Quanto maior o bit-size, mais memória o tipo ocupa e vice-versa.

[imagem] int64 é o dobro de int32, que é o dobro de int16, que é o dobro de int8.

Tipos `unsigned` só podem representar números positivos.

## Overflow

O que acontece quando você ultrapassa o tamanho dos tipos.

```go
package main

func main(){
    var(
        largura uint8 = 255
        altura = 255
    )

    // vamos somar um em largura, ultrapassando os 255 possíveis
    largura++ // 256?

    if largura < altura {
        // operação inválida: largura < altura (tipos diferentes entre uint8 e int)
    }

    if int(largura) < altura {
        fmt.Println("altura é maior")
    }
}
```

Se executarmos o programa, ele vai mostrar "altura é maior". O valor máximo de um `uint8` é 255. Quando somamos mais um, ultrapassamos esse valor. O Go reage a isso resetando a variável para seu valor mínimo, que é 0.

```go
fmt.Println("largura: %d, altura: %d", largura, altura) // largura: 0, altura: 255
```

Logo, nunca compare valores numéricos além de seu mínimo ou máximo.

```go
package main

import "math"

func main(){
    int8(math.MaxInt8 + 1) // constant 128 overflows int8
    // o Go captura erros de overflow em tempo de compilação (quando a expressão pertence ao tempo de compilação)
    // já uma variável pertence ao tempo de execução
    // seu valor não pode ser capturado no tempo de compilação

    var n int8 = math.MaxInt8
    fmt.Println("max int8: ", n) // 127
    fmt.Println("max int8 + 1: ", n+1) // -128
}
```

No Go, um inteiro nunca dá overflow em tempo de execução; ele é resetado. Logo, depois que ultrapassa seu valor máximo, ele volta ao valor mínimo do tipo.

```go
    n = math.MinInt8
    fmt.Println("min int8: ", n) // -128
    fmt.Println("min int8 - 1: ", n-1) // 127
```

Para tipos unsigned é algo semelhante:

```go
    var un uint8
    fmt.Println("max uint8: ", un) // 0
    fmt.Println("max uint8 - 1: ", un-1) // 255
```

Para pontos flutuantes:

```go
    f := float32(math.MaxFloat32)
    fmt.Println("max float: ", f*1.2) // +inf
```

```go
package main

import (
    "fmt"
    "strconv"
)

## Exemplo

func main() {
	// note: ^ means power of.
	//       for example: 2^2 means 2 * 2     = 4
	//                or: 2^3 means 2 * 2 * 2 = 8

	// 0 0 0 0 0 0 1 0 is equal to 2 because:
	// | | | | | | | |
	// | | | | | | | |
	// | | | | | | | +-> 2^0 * 0 = 0
	// | | | | | | +---> 2^1 * 1 = 2
	// | | | | | +-----> 2^2 * 0 = 0
	// | | | | +-------> 2^3 * 0 = 0
	// | | | +---------> 2^4 * 0 = 0
	// | | +-----------> 2^5 * 0 = 0
	// | +-------------> 2^6 * 0 = 0
	// +---------------> 2^7 * 0 = 0
	//                   ------------+
	//                             2

	i, _ := strconv.ParseInt("00000010", 2, 64)
	fmt.Println(i)

	// 0 0 0 1 0 1 1 0 is equal to 2 because:
	// | | | | | | | |
	// | | | | | | | |
	// | | | | | | | +-> 2^0 * 0 = 0
	// | | | | | | +---> 2^1 * 1 = 2
	// | | | | | +-----> 2^2 * 1 = 4
	// | | | | +-------> 2^3 * 0 = 0
	// | | | +---------> 2^4 * 1 = 16
	// | | +-----------> 2^5 * 0 = 0
	// | +-------------> 2^6 * 0 = 0
	// +---------------> 2^7 * 0 = 0
	//                   ------------+
	//                             22


	i, _ = strconv.ParseInt("00010110", 2, 64)
	fmt.Println(i)
}
```
