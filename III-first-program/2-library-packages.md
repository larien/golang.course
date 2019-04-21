# Library packages

São os dois tipos de pacotes em Go: `executável` e `biblioteca`.

## Executable package

`package main`

Como o próprio nome diz, você pode executá-las.

O pacote executável deve ter um programa executável e deve pertencer ao pacote `main`. São executáveis pelos comandos `go run` e `go main`.

## Library package

`package fmt`

Não é possível executá-las, apenas importá-las.

## Executable vs. Library

| Library                   | Executable            |
| ------------------------- | --------------------- |
| criados para reutilização | criados para execução |
| não-executável            | executável            |
| importável                | não-importável        |
| pode ter qualquer nome    | sempre deve ser main  |
| sem `func main`           | com `func main`       |
