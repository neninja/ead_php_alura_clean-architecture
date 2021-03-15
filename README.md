# ead_php_alura_clean-architecture

> Projeto referente a [este](https://cursos.alura.com.br/course/php-introducao-clean-achitecture) curso.

## Requisitos

- PHP 7.4

## Setup inicial

```sh
composer i
```

## Execução dos testes

```sh
composer test
```

## Resumos sobre o curso

- **Arquitetura**: forma da organização do código que facilita/dificulta manutenção e extensão do código.
    > [phprio](https://dev.to/phprio/o-que-e-arquitetura-17ob)
- A aplicação é desenvolvida a partir de seu domínio mais básico e importante. ~~Essas classes que compõe o domínio são as entidades.~~ (não é possível ter uma aplicação composta somente por ValueObjects?)
- **Entidades** devem possuir um identificador que a distingua de outra classe com as mesmas propriedades (dois alunos chamados Felipe não são o mesmo aluno). Enquanto que classes que não precisem de distinção (dois e-mails de mesmo endereço são iguais em qualquer contexto) são chamadas de **ValueObjects**
