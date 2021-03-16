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
- **Entidades** devem possuir um identificador que a distingua de outra classe com as mesmas propriedades (dois alunos chamados Felipe não são o mesmo aluno), pois possue uma identidade **única**. Enquanto que classes que não precisem de distinção (dois e-mails de mesmo endereço são iguais em qualquer contexto) são chamadas de **ValueObjects**
    > [Martin Fowler](https://martinfowler.com/bliki/ValueObject.html)
- **Named constructors**: métodos estáticos que sabem como criar a própria classe, podem ajudar na legibilidade do código com construtores mais complexos. Dependendo da complexidade faz mais sentido usar um [Builder](https://refactoring.guru/pt-br/design-patterns/builder/php/example)
