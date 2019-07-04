# String length

Obter o comprimento de uma `string`.

Existe uma função nativa chamada `len()` que retorna o tamanho de uma `string` em `bytes`.

Funções nativas não precisam ter seus pacotes importados \(na realidade, elas nem pertencem a um pacote\).

```go
func main(){
    name := "batata"
    fmt.Println(len(name)) // printa: 6
}
```

O valor acima só é verdadeiro quando a `string` contém caracteres pertencentes ao latim.

Conforme comentado antes, a função `len()` retorna quantos `bytes` tem em uma `string`.

Em alguns alfabetos, como o japonês, um caracter tem mais de um byte.

No Go, as strings são compostas de `caracteres unicode`. Os caracteres unicode podem conter de 1 a 4 bytes cada.

Também chamamos esses caracteres unicode de `runes`. Runas são feitas de `bytes`

No exemplo abaixo, apenas uma runa contém 3 bytes:

```go
func main(){
    fmt.Println(len("ア")) // printa: 3
}
```

Logo, a função `len()` não é confiável para medir o comprimento de uma string.

É possível utilizar uma função mais confiável, presente no pacote `unicode/utf8`:

```go
import ("fmt"; "unicode/utf8")

func main(){
    name := "ローレン"
    fmt.Println(len("ローレン")) // printa: 12
    fmt.Println(utf8.RuneCountInString(name)) // printa: 4
}
```

Como pode ver acima, não existe o pacote `utf8` isolado. Ele está dentro do grupo `unicode`. Não é possível chamar apenas o grupo `unicode` como pacote. Não existe submódulo no Go. Da forma como fizemos, importar o `unicode/utf8` importa um pacote chamado `utf8`.

