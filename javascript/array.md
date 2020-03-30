# Array

Array é um tipo especial de objeto. É uma estrutura indexada. Possui próprias funções.
Cresce dinamicamente.

Pode ser declarado de várias formas.

    let aprovados = new Array('Ana', 'Bernardo', 'Carlos')

    aprovados = ['Ana', 'Bernardo', 'Carlos']

Se declararmos um elemento em um espaço aleatório, todos os espaços anteriores a esse serão declarados como undefined.

`Array.push(param)`

Adiciona um novo elemento no final do array

`Array.sort()`

Ordena o array.

`delete array[1]`

    array[1] = undefined

`Array.splice(start, deleteN, ...)`

Trabalha no array a partir do elemento _start_, deleta _deleteN_ elementos e adiciona elementos no índice _start_.

`Array.pop()`

Remove o último elemento do array.

`Array.shift()`

Remove o primeiro elemento do array.

`Array.unshift()`

Adiciona um elemento no início do array.

`Array.slice(idx, idf)`

Retorna um novo array apartir do índice _idx_, até o _idf_. Se _idf_ não for declarado, até o final do array.

`Array.forEach(callback)`

Percorre o array e para cada elemento encontrado, executa a função callback passando _value_, _index_ e _array_.

`Array.map(callback)`

Percorre o array e transforma os dados, retornando outro array, de mesmo tamanho do original.

`Array.filter(callback, thisOpcional)`

Percorre o array e filtra os dados, retornando outro array, esse menor ou igual que o array original.

`Array.reduce(callback)`

Possui uma variável "acumuladora", ou seja, uma variável que guarda o valor retornado de cada passagem.

`Array.concat(...)`

Concatena arrays e elementos. 

`FlatMap`

Map junto com concat. Essa função pode ser produzida de forma simples.

    Array.prototype.flatMap = function(callback)
    {
        return Array.prototype.concat.apply([], this.map(callback))
    }

