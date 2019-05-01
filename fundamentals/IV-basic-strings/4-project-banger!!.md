# Project: BANGER

## Main idea

get input + bang it

```bash
go run main.go hey
HEY!!!
go run main.go olar
OLAR!!!!
```

## Code

```go
func main(){
    msg := os.Args[1]
    l := len(msg)

    s := msg + strings.Repeat("!", l)
    s = strings.ToUpper(s)

    fmt.Println(s)
}
```
