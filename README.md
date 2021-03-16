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
- A separação em módulos/pastas (namespaces do php) ajuda a identificar melhor a arquitetura. É normal um módulo precisar de outro ou de um compartilhado para existir.
- Domínio x Aplicação: O primeiro são referentes a regras de entidades e o segundo sobre o que a aplicação se propõe a fazer. Ambas são regras de negócio em camadas distintas.
    - *Interfaces* na camada de domínio e aplicação são implementações de bibliotecas. No primeiro caso participam ativamente das **Entidades** e no segundo dos **UseCases**.
    > É possível concluir que **interfaces** da camada de domínio são obrigações da empresa, onde que mesmo se não houvesse aplicação elas existiriam e da camada de aplicação o contrário. ~~Ponto que não ficou muito claro, pois não vejo sentido na empresa entender o que é persistência no banco (repository)~~
- **UseCases** são utilizados para centralizar algoritmos sem se comprometer com framework. Fora das controllers as regras de negócio ficam agnósticas de bibliotecas e testáveis.
- **DTOs** deve possuir tipos primitivos de propriedades
- Não necessariamente uma arquitetura bem robusta faça sentido em qualquer projeto, pois não compensa gastar um tiro de canhão em uma mosca e assinar todas burocracias de uma arquitetura mais complexa.

 <img width="300" alt="sword meme" src="sword.png">

### Padrões de arquitetura

#### Hexagonal

```txt
                                    /                 /
  +----------------+          +----/---+         +---/-+
  |WebApp/MobileApp+--------->|Adapters+-------->|Ports|      +--------+ 
  +----------------+          +--/-----+         +-/---+      |Business| 
                                /    infra        /  domain   | Domain | 
  +--------+             +-----/--+          +---/-+          +--------+
  |Database+------------>|Adapters+--------->|Ports|  
  +--------+             +-----\--+          +---\-+          +--------+
                                \    infra        \  domain   |Services|
  +------------------+        +--\-----+         +-\---+      +--------+
  |UnitTesting/CLIApp+------->|Adapters+-------->|Ports|
  +------------------+        +----\---+         +---\-+
                                    \                 \
```

#### Clean

```txt
                  |                     |                     |     
                  |                     |                     |     
   Frameworks     |      Interface      |     Application     |     Enterprises
   & Drivers      |      Adapters       |      Business       |      Business
              -------->             -------->   Rules     -------->   Rules
     Web          |      Gateways       |                     |     
     UI           |     Presenters      |      Use Cases      |      Entities
     DB           |     Controllers     |                     |     
                  |                     |                     |     
                  |                     |                     |     
```
