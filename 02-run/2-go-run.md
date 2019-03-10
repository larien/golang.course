# go run

Compila o código e já executa. É utilizado da seguinte forma:

```bash
go run <nome-do-arquivo>
```

É melhor na hora de criar protótipos e testar coisas, por ser mais prático.

Por baixo dos panos, o `go run` de fato compila seu código fonte e gera um executável que depois é utilizado na execução. Ele salva o seu arquivo executável na pasta temporária do seu sistema operacional e o executa de lá.

## Por baixo dos panos

`go run -x main.go`

```
WORK=/tmp/go-build251133865
mkdir -p $WORK/b001/ # (1)
cat >$WORK/b001/importcfg << 'EOF' # internal
# import config
packagefile fmt=/usr/local/go/pkg/linux_amd64/fmt.a
packagefile runtime=/usr/local/go/pkg/linux_amd64/runtime.a
EOF
cd /home/larien/go/src/github.com/laurenmariaferreira
/usr/local/go/pkg/tool/linux_amd64/compile -o $WORK/b001/_pkg_.a -trimpath $WORK/b001 -p main -complete -buildid -gXgbSSsdfq30rHIfxXn/-gXgbSSsdfq30rHIfxXn -dwarf=false -goversion go1.11.5 -D _/home/larien/go/src/github.com/laurenmariaferreira -importcfg $WORK/b001/importcfg -pack -c=4 ./main.go
/usr/local/go/pkg/tool/linux_amd64/buildid -w $WORK/b001/_pkg_.a # internal
cp $WORK/b001/_pkg_.a /home/larien/.cache/go-build/3e/3eea278e11a799a3bf0c4c3b6285fb9129493c3b93756467d1efa13a39fa7b09-d # internal
cat >$WORK/b001/importcfg.link << 'EOF' # internal
packagefile command-line-arguments=$WORK/b001/_pkg_.a
packagefile fmt=/usr/local/go/pkg/linux_amd64/fmt.a # (2)
packagefile runtime=/usr/local/go/pkg/linux_amd64/runtime.a # (3)
packagefile errors=/usr/local/go/pkg/linux_amd64/errors.a
packagefile io=/usr/local/go/pkg/linux_amd64/io.a
packagefile math=/usr/local/go/pkg/linux_amd64/math.a
packagefile os=/usr/local/go/pkg/linux_amd64/os.a
packagefile reflect=/usr/local/go/pkg/linux_amd64/reflect.a
packagefile strconv=/usr/local/go/pkg/linux_amd64/strconv.a
packagefile sync=/usr/local/go/pkg/linux_amd64/sync.a
packagefile unicode/utf8=/usr/local/go/pkg/linux_amd64/unicode/utf8.a
packagefile internal/bytealg=/usr/local/go/pkg/linux_amd64/internal/bytealg.a
packagefile internal/cpu=/usr/local/go/pkg/linux_amd64/internal/cpu.a
packagefile runtime/internal/atomic=/usr/local/go/pkg/linux_amd64/runtime/internal/atomic.a
packagefile runtime/internal/sys=/usr/local/go/pkg/linux_amd64/runtime/internal/sys.a
packagefile sync/atomic=/usr/local/go/pkg/linux_amd64/sync/atomic.a
packagefile internal/poll=/usr/local/go/pkg/linux_amd64/internal/poll.a
packagefile internal/syscall/unix=/usr/local/go/pkg/linux_amd64/internal/syscall/unix.a
packagefile internal/testlog=/usr/local/go/pkg/linux_amd64/internal/testlog.a
packagefile syscall=/usr/local/go/pkg/linux_amd64/syscall.a
packagefile time=/usr/local/go/pkg/linux_amd64/time.a
packagefile unicode=/usr/local/go/pkg/linux_amd64/unicode.a
packagefile math/bits=/usr/local/go/pkg/linux_amd64/math/bits.a
packagefile internal/race=/usr/local/go/pkg/linux_amd64/internal/race.a
EOF
mkdir -p $WORK/b001/exe/
cd .
/usr/local/go/pkg/tool/linux_amd64/link -o $WORK/b001/exe/main -importcfg $WORK/b001/importcfg.link -s -w -buildmode=exe -buildid=HTsxxXkUK-B21ZIhxyFU/-gXgbSSsdfq30rHIfxXn/5SHcuBMHR8wIDhTaA6FF/HTsxxXkUK-B21ZIhxyFU -extld=gcc $WORK/b001/_pkg_.a
$WORK/b001/exe/main
Hello, world!
```

1. De forma resumida, o Go começa sua compilação dentro de uma pasta temporária. Ele cria uma pasta chamada `b001` dentro dessa pasta, que é utilizada para importar as configurações necessárias para fazer o seu programa rodar.

2. Podemos ver que o primeiro pacote que ele importa é o que utilizamos no nosso programa para printar o `Hello, world`: o pacote `fmt`. Dá pra ver que ele utiliza um arquivo `fmt.a`, encontrado no \$GOPATH, dentro da pasta `pkg`, na pasta referente ao seu sistema operacional. Esse é um arquivo que foi pré-compilado no momento de instalação do Go na sua máquina, ou seja, é um arquivo assembly contendo o código fonte da biblioteca padrão compilado em linguagem de máquina para ser utilizado nos seus programas. Por ter sido pré-compilado, a compilação do seu programa é muito mais rápida e eficiente, porque o compilador não precisa recompilar o código fonte da biblioteca padrão. Quando você instala um pacote externo com `go get` ou `go install`, o Go já gera esse arquivo pré-compilado para você.

3. Nas linhas de `packagefile`, o que o Go faz é linkar os pacotes necessários no executável final. Isso significa que o compilador está adicionando esses códigos de máquina ao executável do meu programa. É por isso que importar pacotes são importantes.

- Criar um executável para OS X:
  `GOOS=darwin GOARCH=386 go build`

- Criar um executável para Windows:
  `GOOS=windows GOARCH=386 go build`

- Criar um executável para Linux:
  `GOOS=linux GOARCH=arm GOARM=7 go build`

- Ler a [documentação online](https://golang.org/pkg/)

- Fazer um [tour](https://tour.golang.org/welcome/1)
