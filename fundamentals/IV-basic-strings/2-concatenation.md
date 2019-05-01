# Concatenation

O operador de concatenação `+` permite a combinação de várias strings, criando uma nova.

```go
func main(){
    name, last := "carl", "sagan"

    fmt.Println(name + " " + last) // printa: carl sagan

    name += " edward"

    fmt.Println(name + " " + last) // printa: carl edward sagan
}
```

Também é possível concatenar strings com acento grave:

```go
func main(){
    fmt.Println(`olar` + `, ` + "joia?") // printa: olar, joia?
}
```

## Convert integer to string

```go
func main(){
    eq := "1 + 2 = "
    sum := 1 + 2
    fmt.Println(eq + strconv.Itoa(sum)) // printa: "1+ 2 = 3"
}
```

## Convert bool to string

```go
func main(){
    eq := strconv.FormatBool(true) + " " + strconv.FormatBool(false)
    fmt.Println(eq) // printa: "true false"
}
```
