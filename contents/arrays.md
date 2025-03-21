<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🔢 Arrays e Arrays Bidimensionais 

## Arrays
Um array é uma lista ordenada de elementos que pode armazenar valores de qualquer tipo de dados. Em JavaScript, os arrays são objetos dinâmicos, ou seja, podem crescer ou diminuir de tamanho.

### Criando Arrays

```javascript
// Criando um array vazio
let vazio = [];

// Array com elementos
let numeros = [1, 2, 3, 4, 5];

// Array com diferentes tipos de dados
let misturado = [42, "texto", true, null, {nome: "João"}];

// Usando o construtor Array
let construido = new Array(3); // Cria array com 3 posições vazias
```

### Acessando Elementos

```javascript
let frutas = ["maçã", "banana", "laranja"];

console.log(frutas[0]); // "maçã"
console.log(frutas[1]); // "banana"
console.log(frutas[2]); // "laranja"
console.log(frutas.length); // 3 (tamanho do array)
```

### Manipulação Básica

```javascript
let numeros = [1, 2, 3];
numeros.push(4);         // Adiciona ao final: [1, 2, 3, 4]
numeros.unshift(0);      // Adiciona ao início: [0, 1, 2, 3, 4]
numeros.pop();           // Remove do final: [0, 1, 2, 3]
numeros.shift();         // Remove do início: [1, 2, 3]
```

Para uma lista completa de métodos de array e exemplos detalhados, consulte [Métodos de Arrays](metodos-arrays.md).

## Arrays Bidimensionais

Um array bidimensional é essencialmente um "array de arrays", útil para representar tabelas, matrizes e dados em grade.

```javascript
let matriz = [
    [1, 2, 3],    // linha 0
    [4, 5, 6],    // linha 1
    [7, 8, 9]     // linha 2
];

// Acessando elementos (linha, coluna)
console.log(matriz[0][0]); // 1
console.log(matriz[1][2]); // 6
console.log(matriz[2][1]); // 8

// Iterando sobre uma matriz
for (let i = 0; i < matriz.length; i++) {
    for (let j = 0; j < matriz[i].length; j++) {
        console.log(`Elemento na posição [${i}][${j}]: ${matriz[i][j]}`);
    }
}
```

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>