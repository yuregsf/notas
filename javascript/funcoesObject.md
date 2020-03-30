# Funções importantes do `Object`

`Object.keys`

Retorna um array com as chaves de um objeto.


`Object.values`

Retorna um array com os valores de um objeto.

`Object.entries`

Retorna um array com as chaves e os valores de um objeto.

`Object.defineProperty`

Define uma nova propriedade dentro de um objeto. Exemplo:
    
    Object.defineProperty(pessoa, 'dataNascimento', {
        enumerable: true,
        writable: false,
        value: '01/01/1900'
    })

`Object.assign`

Concatena objetos. Se a chave já existe, o valor é sobrescrito.

`Object.freeze`

"Congela" um objeto, desabilitando sua edição. 

`Object.setPrototypeOf`

Define o protótipo de um objeto.

`Object.create`

Cria um novo objeto, tomando o argumento como protótipo. Além disso recebe um objeto com atributos que deseja alterar ou criar.