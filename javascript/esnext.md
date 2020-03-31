
# ESNext (ES 6, 7, 8)

## `let` e `const`

`let` e `const` possui escopo de bloco, ou seja, só pode ser acessada dentro daquele bloco.

## Template String

Definida por \`\` é uma string onde é possível utilizar variáveis.

## Destructuring

Desestruturar uma estrutura, seja array ou objeto.

Exemplo

    const [l, e, ...tras] = "Legal"
    const [x, , y] = [1, 2, 3]
    const { idade, nome } = { nome: 'Ana', idade: 30 }
    const { idade: i, nome } = { nome: 'Ana', idade: 30 }

## Arrow function

Sintaxe reduzida, com retorno implícito, caso não possua corpo. São funções anônimas.

    const soma = (a, b) => a + b

O `this` dentro de uma arrow function não varia, sempre aponta para o contexto em que foi declarado.

## Parâmetro default

A variável assume um valor padrão caso nenhum valor seja passado como parâmetro.

    function fun(text = 'Legal'){}

## Operador rest/spread

É chamado rest quando agrupa vários elementos em uma estrutura, como por exemplo.

    function total(...numeros){
        let total = 0
        numeros.forEach(n => total += n)
        return total
    }

Já no caso do spread é quando "espalha" elementos em uma estrutura.

    const funcionario = { nome: 'Maria', salario: 12345.99 }
    const clone = { ative: true, ...funcionario }
    // O objeto funcionário é espalhado dentro do objeto clone

## `Object.entries`

Uma matriz com chaves e valores de um objeto.

## Melhorias na notação literal

    const nome = 'Carla'
    const pessoa = {
        nome,
        ola(){

        }
    }

    //Antes..
    const nome = 'Carla'
    const pessoa = {
        nome: nome,
        ola: function (){

        }
    }

## `Class`

Por debaixo dos panos é como uma função, mas para quem já trabalha com POO se torna mais simples.

    class Animal{}
    class Cachorro extends Animal{}

Exemplo de herança de classes. No fundo é uma herança por `prototype`.