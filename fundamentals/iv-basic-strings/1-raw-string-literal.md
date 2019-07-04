# Raw String Literals

Usar acento grave ao invés de aspas duplas em `strings`.

As `strings` com acento grave, diferentemente das aspas duplas, permite múltiplas linhas.

Nas aspas duplas, os caracteres são interpretados pelo Go \(sequências de escape\).

As `strings` com acento grave não são interpretadas e não são processadas pelo Go. Se houver uma sequência de escape, o Go não vai entender como sequência de escape.

```go
func main(){
    var s string
    s = "how are you?"
    s = `how are you?`

    s = "<html>\n\t<body>\"Hello\"</body>\n</html>"
    fmt.Println(s)

    // melhor usar acento grave
    s = `
    <html>
        <body>"Hello"</body>
    </html>`
}
```

Também é melhor utilizar essa forma com caminhos:

```go
func main(){
    fmt.Println("c:\\meu\\arquivo\\\bunitu")
    fmt.Println(`c:\meu\arquivo\bunitu`)
}
```

