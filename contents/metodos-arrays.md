<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# Métodos de Arrays

Os arrays em JavaScript possuem diversos métodos poderosos que facilitam a manipulação de dados. Vamos explorar os mais importantes:

## Localizando Elementos

### Para Arrays de Tipos Primitivos

```js
const numeros = [1, 2, 3, 4, 5, 2];

// indexOf - retorna o índice da primeira ocorrência ou -1 se não encontrar
console.log(numeros.indexOf(2));     // 1
console.log(numeros.indexOf(6));     // -1

// lastIndexOf - retorna o índice da última ocorrência
console.log(numeros.lastIndexOf(2)); // 5

// includes - verifica se o elemento existe (retorna boolean)
console.log(numeros.includes(3));    // true
console.log(numeros.includes(6));    // false
```

### Para Arrays de Tipos de Referência

```js
const pessoas = [
  { id: 1, nome: 'Ana' },
  { id: 2, nome: 'Bruno' },
  { id: 3, nome: 'Carlos' }
];

// find - retorna o primeiro elemento que satisfaz o teste
const pessoa = pessoas.find(p => p.id === 2);
console.log(pessoa); // { id: 2, nome: 'Bruno' }

// findIndex - retorna o índice do primeiro elemento que satisfaz o teste
const indice = pessoas.findIndex(p => p.nome === 'Carlos');
console.log(indice); // 2
```

## ➕ Adicionando Elementos

```js
let frutas = ['maçã', 'banana'];

// push - adiciona ao final (retorna o novo tamanho)
frutas.push('laranja');
console.log(frutas); // ['maçã', 'banana', 'laranja']

// unshift - adiciona ao início (retorna o novo tamanho)
frutas.unshift('morango');
console.log(frutas); // ['morango', 'maçã', 'banana', 'laranja']

// concat - combina arrays (não modifica o original, retorna novo array)
const maisFrutas = frutas.concat(['uva', 'pera']);
console.log(maisFrutas); // ['morango', 'maçã', 'banana', 'laranja', 'uva', 'pera']
```

## ➖ Removendo Elementos

```js
let letras = ['a', 'b', 'c', 'd', 'e'];

// pop - remove do final (retorna o elemento removido)
const ultima = letras.pop();
console.log(ultima); // 'e'
console.log(letras); // ['a', 'b', 'c', 'd']

// shift - remove do início (retorna o elemento removido)
const primeira = letras.shift();
console.log(primeira); // 'a'
console.log(letras); // ['b', 'c', 'd']

// splice - remove elementos a partir de um índice
// splice(índice, quantidade)
const removidos = letras.splice(1, 1);
console.log(removidos); // ['c']
console.log(letras); // ['b', 'd']
```

## Esvaziando um Array

```js
let numeros = [1, 2, 3, 4, 5];

// Método 1: Reatribuição (eficaz se não houver outras referências)
numeros = [];

// Método 2: Definir length como 0
numeros = [1, 2, 3, 4, 5];
numeros.length = 0;
console.log(numeros); // []

// Método 3: Usando splice (remove todos os elementos)
numeros = [1, 2, 3, 4, 5];
numeros.splice(0, numeros.length);
console.log(numeros); // []
```

## Transformando Arrays

```js
const numeros = [1, 2, 3, 4, 5];

// join - converte array em string com separador
console.log(numeros.join('-')); // "1-2-3-4-5"

// reverse - inverte a ordem (modifica o original)
numeros.reverse();
console.log(numeros); // [5, 4, 3, 2, 1]

// sort - ordena o array (modifica o original)
const frutas = ['banana', 'maçã', 'abacaxi', 'laranja'];
frutas.sort();
console.log(frutas); // ['abacaxi', 'banana', 'laranja', 'maçã']

// Para ordenar números:
const nums = [5, 10, 2, 25, 1];
nums.sort((a, b) => a - b); // ordem crescente
console.log(nums); // [1, 2, 5, 10, 25]
```

## Iteração e Transformação

```js
const numeros = [1, 2, 3, 4, 5];

// forEach - executa função para cada elemento
numeros.forEach(num => console.log(num * 2));

// map - cria novo array com resultados da função
const dobrados = numeros.map(num => num * 2);
console.log(dobrados); // [2, 4, 6, 8, 10]

// filter - cria novo array com elementos que passam no teste
const pares = numeros.filter(num => num % 2 === 0);
console.log(pares); // [2, 4]

// reduce - reduz array a um valor único
const soma = numeros.reduce((acumulador, atual) => acumulador + atual, 0);
console.log(soma); // 15

// every - verifica se todos os elementos passam no teste
const todosMaioresQueZero = numeros.every(num => num > 0);
console.log(todosMaioresQueZero); // true

// some - verifica se pelo menos um elemento passa no teste
const algumMaiorQueDez = numeros.some(num => num > 10);
console.log(algumMaiorQueDez); // false
```

## Métodos Modernos (ES6+)

```js
// flat - "achata" arrays aninhados
const aninhado = [1, [2, 3], [4, [5, 6]]];
console.log(aninhado.flat());     // [1, 2, 3, 4, [5, 6]]
console.log(aninhado.flat(2));    // [1, 2, 3, 4, 5, 6]

// flatMap - map seguido de flat(1)
const frases = ["Olá mundo", "JavaScript é incrível"];
const palavras = frases.flatMap(frase => frase.split(' '));
console.log(palavras); // ["Olá", "mundo", "JavaScript", "é", "incrível"]

// Array.from - cria array a partir de iterable
const letras = Array.from("hello");
console.log(letras); // ["h", "e", "l", "l", "o"]

// Array.of - cria array com os argumentos
const novo = Array.of(1, 2, 3);
console.log(novo); // [1, 2, 3]
```

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>