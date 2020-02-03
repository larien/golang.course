# Defined types

Tipos definidos só podem ser criados a partir de outro tipo existente. Ele tem seu próprio nome e métodos.

## Criando um tipo definido

```golang
type Duracao int64
```

`Duracao` é um tipo definido cujo tipo base é um `int64`. Na prática, é seu tipo real. Suas operações (+ - / * %), representações (-1, 0, 1, 2...) e temanho equivalem ao `int64`. No entanto, `Duracao` e `int64` são tipos diferentes e não é possível atribuir um valor para outro.

Só que um tipo pode ser convertido para outro tipo se tieverem a mesma base de tipagem. Por exemplo, isso é possível:

```golang
var ms int64 = 1000
var ns Duration

ns = Duration(ms)
```

## Tipo fundamental

A definição do tipo fundamental do `int64` é ele mesmo:

```golang
type int64 int64
```

Logo, faz sentido que seja possível converter Duration para int64.

## Por que criar tipos?

Para "dar os nomes" aos valores cujos tipos fundamentais são primitivos. Por exemplo, se eu chamar uma variável como Minutos e ela ainda fora int64, ela representa os minutos de alguma coisa e deixa de ser apenas um int64.

Com essa trava lógica, temos também a segurança de tipos (int64 não podem interagir com Minutos) e melhora a legibilidade.

> Se você se dá ao esforço de dar nomes para Pint e Xint, é porque você quer que ambos sejam diferentes. Isso não é C, onde um `typedef` é apenas um `alias`.

- Rob Pike, um dos criadores do Go

