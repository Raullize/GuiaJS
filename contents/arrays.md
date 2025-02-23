<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🔢 Arrays e Arrays Bidimensionais 

## Arrays
Um array é uma lista ordenada de elementos.

Métodos comuns:
- **`push`**: Adiciona um elemento ao final do array.
- **`unshift`**: Adiciona um elemento ao início do array.
- **`pop`**: Remove o último elemento.
- **`shift`**: Remove o primeiro elemento.
- **`includes`**: Verifica se um valor está presente.
- **`indexOf`**: Retorna o índice de um valor.
- **`slice`**: Retorna uma cópia parcial do array.
- **`concat`**: Junta dois arrays.
- **`splice`**: Adiciona ou remove elementos.

Exemplo:

```javascript
let numeros = [1, 2, 3];
numeros.push(4); // [1, 2, 3, 4]
numeros.shift(); // [2, 3, 4]
console.log(numeros.includes(2)); // true
```

## Arrays Bidimensionais

Um array dentro de outro array.

Exemplo:

```javascript
let matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];
console.log(matriz[1][2]); // 6
```

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>