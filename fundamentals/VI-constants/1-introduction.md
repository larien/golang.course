# Constants

> A única coisa constante é o tempo

- Hieráclitus

Como sabemos, uma variável pertence ao tempo de execução e o Go só o cria nesse momento. No momento da compilação, o Go só sabe o tipo da variável, mas não atribui nenhum valor a ela. O valor da variável pode mudar no decorrer do programa.

No entanto, a constante pertence ao tempo de compilação e é criada nesse momento. No tempo de execução, o Go só a transforma em um valor que não pode ser alterado no decorrer do programa.

Constantes podem ter nome ou não. Todos os tipos literais básicos são constantes sem nome: `1`, `3.14`, `hello`, `true`, `false`.

Contantes nomeadas são substituídas por seu valor em tempo de execução. Logo, isso `const One int = 1` criado no tempo de compilação se torna `1` em tempo de execução.

Constantes não precisam ter tipos.