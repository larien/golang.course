# $GOPATH

```bash
> go env GOPATH
%USERPROFILE%/go
```

```bash
> cd ~/go
    /bin
    /pkg
    /src
```

É uma boa prática criar os seus projetos no diretório src do seu GOPATH. Dessa forma, um arquivo `main.go` dentro de um repositório `repository` na conta `user` no GitHub teria a seguinte estrutura:

```text
- $GOPATH/
    - src/
        - github.com/
            - user/
                - repository/
                    - main.go
```

O `$GOPATH` é uma variável de ambiente que mostra um local físico no seu computador. Por padrão, o Go presume que esse caminho está na sua pasta de Users.

Você não precisa definir seu `$GOPATH`.

Também chamamos o $GOPATH de workspace. Ele também mostra ferramentas do Go onde as pessoas podem encontrar arquivos de código fonte e outras coisas relacionadas, como pacotes compilados, binários executáveis etc.

Por convenção, todo projeto Go usa essa pasta.

Então, por exemplo, quando você baixa um projeto em Go, ele também será armazenado dentro da pasta workspace.

O VS já usa isso como padrão e cria os projetos lá automaticamente.

O diretório src contém os arquivos código fonte do Go.

Então nós, gophers, armazenamos todos os nossos arquivos de código fonte na pasta src dentro do GOPATH. No Go, todo programa executável precisa de seu próprio diretório.

Seguindo essas convenções, você evita que conflito de nomes com outros pacotes.

Para criar seu primeiro projeto já utilizando VS Code, você pode digitar no terminal:

```bash
code ~/go/src
```

Para Windows:

```bash
code %USERPROFILE%\go\src
```

