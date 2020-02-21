# Uso do `this`

`this` pode variar de acordo com o contexto.

## Browser console  
Nesse contexto o `this` é o mesmo que `window`

    function f1() { console.log(this === window) }
    f1()

> **Output:** `true`

Quando chamado por um evento `onclick`.  
Atribuindo a função `f1()` ao evento:

    document.getElementsByTagName('body')[0].onclick = f1

e clicando na página, percebemos que seu comportamento é diferente do anterior.  
> **Output:** `false`  

Nesse caso, quem chama o `this`? Será o `document`?  
Fazendo

    function f2() { console.log(this === document) }
    document.getElementsByTagName('body')[0].onclick = f2

> **Output:** `false`  

Agora faça  

    const body = document.getElementsByTagName('body')[0]
    function f2() { console.log(this === body) }
    document.getElementsByTagName('body')[0].onclick = f2

>**Output:** `true`

Perceba que agora o retorno é verdadeiro. Então concluímos que nesse caso quem chama o `this` é o próprio elemento!

***
## Arrow Function

O `this` dentro de uma arrow function não varia.  
Faça:

    const f3 = () => console.log(this === window)

Se a função `f3` for chamada diretamente no console, seu resultado é verdadeiro. Quando chamada por um evento, como no exemplo anterior, seu resultado também é verdadeiro.

    document.getElementsByTagName('body')[0].onclick = f3

>**Output:** `true`

**Observação:** Nesse caso o `this` é definido no mesmo escopo em que a função foi definida. No nosso caso, o escopo global, `window`. Esse comportamento é chamado de "this léxico"

***
## Função `bind`
`bind` resolve o `this`, recebendo o objeto que você quer resolver, como argumento.

    const pessoa = {
        saudacao = 'Bom dia!',
        falar(){
            console.log(this.saudacao)
        }
    }

Utilizando o objeto `pessoa` como exemplo.

Se fizermos
    
    pessoa.falar()

>**Output:** Bom dia!

Agora atribua essa função a uma constante e faça a chamada

    const falar = pessoa.falar
    falar()

>**Output:** undefined

Perceba que a saída é inesperada. Mas isso ocorre pois o contexto no qual a constante `falar` foi chamada é diferente, logo o `this` é diferente.

Para podermos amarrar o `this` ao objeto correto, utilizamos `bind`.

    const falarDePessoa = pessoa.falar.bind(pessoa)
    falarDePessoa()

>**Output:** Bom dia!