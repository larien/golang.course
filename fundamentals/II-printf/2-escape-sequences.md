# Escape sequences

Permitem que você represente caracteres especiais e dão significados especiais a eles.

As sequências de escape são reconhecidas com uma barra e uma letra (ex.: "\n") e o Go as interpreta dentro de uma string.

```go
func main(){
    fmt.Println("hi\nhi")
    // printa:
    // hi
    // hi
}
```

`\n` - nova linha

Para printar a própria barra, basta utilizar duas barras `\\`.

O mesmo vale para aspas duplas: `\"`.

```go
"hi\\n\"hi\"" // printa: hi\n"hi"
```
