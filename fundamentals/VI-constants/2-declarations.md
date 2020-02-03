# Declaration syntax

É preciso definir quase qualquer coisa em Go para utilizá-las.

## Valores mágicos

Números ou valores mágicos são valores sem nome. Logo, não é tão simples entender o que eles são ou o que fazem:

```golang
func main(){
    cm := 100
    m := cm/100

    fmt.Printf("%dcm id %dm\n", cm, m)
}
```

Em programas maiores, isso prejudica a legibilidade. Podemos usar as constantes para melhorar isso:

```golang
func main(){
    const meters int = 100

    cm := 100
    m := cm/meters

    fmt.Printf("%dcm id %dm\n", cm, m)
}
```

Constantes sempre precisam começar com um valor.

## Detecção de erros

O Go não consegue detectar erros em tempo de compilação.

```golang
func main(){
    total, numberOf := 5, 0

    fmt.Printf(total/numberOf) // RUNTIME ERROR: Integer divide by zero
}
```

Trocando para constantes, é possível capturar esse casos:

```golang
func main(){
    const total int = 5
    const numberOf int = 0

    fmt.Printf(total/numberOf) // COMPILE-TIME ERROR: Division by zero
}
```

## Regras

- Não é possível mudar valores de constantes (imutabilidade)
- Não é possível inicializar uma constante em tempo de execução, menos quando utiliza a função `len`, já que seu argumento sempre é uma constante.

## Tipos de constantes

Não precisam ser tipos numéricos:

```golang
func main(){
    const min int = 1
    const pi int = 3.14
    const version int = "2.0.1"
    const debug int = true

    fmt.Println(min, pi, version, debug)
}
```

Nem é necessário declarar seus tipos:

```golang
func main(){
    const min = 1
    const pi = 3.14
    const version = "2.0.1"
    const debug = true

    fmt.Println(min, pi, version, debug)
}
```

É possível utilizar expressões quando se inicializa constantes, desde que sejam constantes:

```golang
func main(){
    const min = 1 + 1
    const pi = 3.14 * min
    const version = "2.0.1" + "-beta"
    const debug = !true
```

## Declaração de várias constantes

```golang
func main(){
    const min, max = 1, 1000

    fmt.Println(min, max)
```

Ou:

```golang
func main(){
    const (
        min int = 1
        max
    )

    fmt.Println(min, max) // 1 1
```

O Go repete o valor anterior da constante e/ou expressão automaticamente.
