# Bit & Bytes

## Why do you need a type system?

O objetivo máximo de um sistema de tipos é prevenir bugs o mais cedo possível.

Linguagens de tipagem `dinâmica` postergam a verificação de tipos para o `tempo de execução` (ou `runtime`), em que você roda seu programa. Em muitas linguagens, essa verificação nem mesmo é feita e não existe uma etapa de compilação.

Linguagens de tipagem `estática` fazem essa verificação de tipos no `tempo de compilação` (ou `compile-time`), antes do `tempo de execução`. Você precisa dar um tipo para todo valor, então todo valor precisa ter um tipo.

## Questions answered by type system

- Quais tipos podem ser utilizados?
- Como cada tipo interage um com o outro?
- O que é permitido e o que não é?
- Como criar novos tipos?

## Bits

Um `bit` pode ser 0 ou 1. Não há um valor intermediário. Ou é ou não é.

Você pode utilizar `bits` para `codificar` informação.

- on/off
- true/false

Logo, um `bit` pode ter somente dois estados. No caso de termos apenas 1 bit, 2¹ = 2 estados. Quanto mais bits, mais valores você pode representar.

É possível printar valores em bit no Go com o formatador `%b`:

```go
fmt.Printf("%b", 0)
```

Para 2 bits: 2² = 2 \* 2 = 4 estados.

```go
fmt.Printf("%02b", 2) // printa: 10
```

## Bytes

Diferentemente do bit, o byte representa o menor e mínimo pedaço de informação. É muito utilizado para armazenar e transferir dados de um lugar para outro.

Por exemplo, você pode armazenar ou ler um arquivo escrito em bytes.

Geralmente, vários bytes se unem para formar números, strings, textos, imagens, vídeos, músicas etc.

Bytes são bem importantes para o Go.

1 `byte` consiste de `8 bits`.

1 byte = 8 bits = 2^8 = 256 valores
2 bytes = 16 bits = 2^16 = 65.536 valores
4 bytes = 32 bits = 2^32 = 4 bilhões de valores

Um byte é um `uint8` - pode representar de 0 a 255 valores.

```go
func main(){
    var b byte
    b = 0
    fmt.Printf("%08b = %d\n", b, b) // printa: 00000000 = 0

    b = 255
    fmt.Printf("%08b = %d\n", b, b) // printa: 11111111 = 255

}
```
