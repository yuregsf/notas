# Node

O Node é baseado em módulos, cada arquivo é um módulo. Então para outro arquivo, ou módulo, utilizar funções, objetos de outros módulos, este precisa exportar os atributos que serão visíveis a outros arquivos.

## Instâncias

O Node faz cache das variáveis, ou seja, se um mesmo módulo é exportado para dois objetos diferentes, seu valores serão compartilhados. Agora, para que cada objeto seja único, é necessário exportar uma função factory, pois dessa forma será criada uma nova instância do módulo sempre que ele for requerido.

instanciaUnica.js

    module.exports = { 
        valor: 1,
        inc(){
            this.valor++
        }
    }

instanciaNova.js

    module.exports = () => {
        return
        {
            valor: 1,
            inc()
            {
                this.valor++
            }
        }
    }

instanciaCliente.js

    /*
    * contadorA e contadorB recebem o mesmo objeto
    */
    const contadorA = require('./instanciaUnica')
    const contadorB = require('./instanciaUnica')

    /*
    * contadorC e contadorD são independentes
    */
    const contadorC = require('./instanciaNova')()
    const contadorD = require('./instanciaNova')()

    contadorA.inc()
    contadorA.inc()
    console.log(contadorA.valor, contadorB.valor)
    console.log(`contadorA é igual a contadorB? ${contadorA === contadorB}`) //Sim

    contadorC.inc()
    contadorC.inc()
    console.log(contadorC.valor, contadorD.valor)
    console.log(`contadorC é igual a contadorD? ${contadorC === contadorD}`) //Não

## Global

Objeto global ao sistema. Ao ser carregado pela primeira vez, este se torna disponível à toda aplicação.

Exemplo:

    global.legal = {
        fun1(){
            ...
        },
        dia = 'Bom dia'
    }

PRERIGO!!

O `this` dentro de uma função aponta para o objeto `global`! Fora dela aponta para `module.exports`.

## Passando parâmetros entre módulos

Se o módulo exportador for uma função, esta pode receber parâmetros diretamente no `require`.

    //modulo.js

    module.exports = function(...nomes){
        return nomes.map(nome => `Boa semana ${nome}!`)
    }

    //client.js

    const saudacoes = require('./modulo.js')('João', 'Pedro', 'Maria')

## Scripts

É possível definir scripts de execução no arquivo `package.json`. Existem scripts padrões, já esperados pelo node. para executar scripts criados, não definidos pela documentação, utilize:

    npm run <script-name>

## Chain of responsability

Uma função sem reuso. Refatorar o processo. Eliminar os acoplamentos, tornando os passos independentes atráves do conceito de middleware. Onde, por exemplo, temos 3 funções, de um processo A, que se comunicam entre si. Porém são funções que podem ser refatoradas de forma que podem ser reutilizadas. Daí os middlewares. As funções recebem uma request e passam para a próxima função, se existente, uma response. Dessa forma as funções podem ser colocadas de outras formas, sem prender uma a outra.

