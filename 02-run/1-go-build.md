# go build

Compila o código do seu projeto em um único executável/binário. É melhor quando você trabalha com aplicações maiores ou quando quer fazer o deploy do executável em algum lugar.

## Tempo de compilação x tempo de execução

O código compilado continua sendo um código, mas de forma que a máquina consiga ler.

- Código fonte

```go
package main
import "fmt"

func main(){
    fmt.Println("Oi!")
}
```

- Código compilado

```
MOVQ GS: 0x8a0, CX
CMPQ 0x10(CX), SP
JBE 0x108e7c7
SUBQ $0x48, SP
MOVQ BP, 0x40(SP)
...
```

O código compilado não faz nada até que você o execute. A partir daí, ele começa a trabalhar com a memória do computador, com a CPU, comunica com a rede e assim vai.

Em linguagens como PHP, Ruby, Python ou Javascript você não precisa se preocupar com isso, pois são linguagens interpretadas, não compiladas.
