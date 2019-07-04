# Type code in main.go

```go
    (1) package main (2)

    (7) import "fmt" (8)

    (3) func main(){ (4)
        (5) fmt.Println("Hello, Gopher!") (6)
    }
```

1. `package`: cláusula package, que sempre deve ser a primeira linha do arquivo.
2. `main`: nome do pacote a que esse arquivo pertence. Todo arquivo deve pertencer a somente um pacote.
3. `func`: bloco de código reutilizável e executável.
4. `func main()`: função especial que diz ao Go por onde começar a executar o programa.
5. `fmt`: nome de um pacote presente na biblioteca padrão. A biblioteca padrão tem sido desenvolvida pela comunidade e pela equipe mantenedora do Go na Google desde o princípio e contém métodos e funções úteis para o dia a dia da pessoa desenvolvedora. Os pacotes da biblioteca padrão vêm junto com a linguagem ao ser instalada e não precisam ser baixados.
6. `.Println()`: quando utilizamos o `.` após o nome do pacote, você tem acesso a todas as funcionalidades desse pacote. As funcionalidades incluem métodos, funções, contantes e variáveis públicas pertencentes ao pacote. Nesse exemplo, utilizamos a função `Println`, que recebe um conjunto de dados \(frase, bytes\) como parâmetro e printa essa informação no console, já pulando linha com um `\n` automático.
7. `import`: quando você utiliza alguma funcionalidade de algum pacote, seja ele da biblioteca padrão ou não, é necessário importá-lo para dentro do seu arquivo. Isso é feito através dessa cláusula.
8. `"fmt"`: e aqui vai o nome do pacote. Também é possível colocar um alias, que ficaria, por exemplo, `f "fmt"` e sua utilização seria `f.Println("Hello, Gopher!")`.

