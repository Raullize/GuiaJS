<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🔄 Loops Específicos em JavaScript

Além dos loops tradicionais (`for`, `while`, `do...while`), JavaScript oferece loops especializados para iteração em objetos e arrays.

## 🔍 Loop `for...in`

O loop `for...in` é utilizado para percorrer as **propriedades enumeráveis** de um objeto.

```js
const pessoa = {
  nome: "Ana",
  idade: 28,
  profissao: "Desenvolvedora"
};

for (let propriedade in pessoa) {
  console.log(`${propriedade}: ${pessoa[propriedade]}`);
}
// Saída:
// nome: Ana
// idade: 28
// profissao: Desenvolvedora
```

⚠️ **Cuidado:** Não é recomendado usar `for...in` em arrays, pois ele itera sobre todas as propriedades enumeráveis, incluindo as herdadas do protótipo.

```js
// Exemplo de problema com for...in em arrays
const numeros = [10, 20, 30];
numeros.propriedade = "teste";

for (let i in numeros) {
  console.log(`${i}: ${numeros[i]}`);
}
// Saída:
// 0: 10
// 1: 20
// 2: 30
// propriedade: teste
```

## 🔍 Loop `for...of`

O loop `for...of` é utilizado para iterar sobre elementos de objetos **iteráveis** (arrays, strings, Map, Set, etc.).

```js
// Com arrays
const frutas = ["maçã", "banana", "laranja"];
for (let fruta of frutas) {
  console.log(fruta);
}
// Saída:
// maçã
// banana
// laranja

// Com strings
const palavra = "hello";
for (let letra of palavra) {
  console.log(letra);
}
// Saída:
// h
// e
// l
// l
// o
```

### Diferenças entre `for...in` e `for...of`

| `for...in`                               | `for...of`                             |
|------------------------------------------|----------------------------------------|
| Itera sobre **propriedades** do objeto   | Itera sobre **valores** do iterável    |
| Funciona com qualquer objeto             | Funciona apenas com objetos iteráveis  |
| Inclui propriedades da cadeia de protótipos | Apenas valores do próprio iterável  |
| Retorna chaves/índices                   | Retorna valores                        |

## 🛑 Controlando Loops: `break` e `continue`

### `break`

O comando `break` interrompe a execução do loop completamente:

```js
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    break; // Sai do loop quando i é 5
  }
  console.log(i);
}
// Saída: 0, 1, 2, 3, 4
```

### `continue`

O comando `continue` pula a iteração atual e continua com a próxima:

```js
for (let i = 0; i < 5; i++) {
  if (i === 2) {
    continue; // Pula a iteração quando i é 2
  }
  console.log(i);
}
// Saída: 0, 1, 3, 4
```

## 🔄 Loop `forEach` para Arrays

Embora não seja um loop de sintaxe, o método `forEach` é uma forma moderna de iterar sobre arrays:

```js
const numeros = [1, 2, 3, 4, 5];

numeros.forEach((numero, indice, array) => {
  console.log(`Número ${numero} no índice ${indice}`);
});
```

⚠️ Não é possível usar `break` ou `continue` com `forEach`.

## 🧠 Escolhendo o Loop Certo

| Loop         | Uso Recomendado                                       |
|--------------|-------------------------------------------------------|
| `for`        | Quando você precisa de controle explícito sobre o iterador |
| `while`      | Quando a condição de término não é conhecida previamente |
| `do...while` | Quando o loop deve executar pelo menos uma vez          |
| `for...in`   | Para percorrer propriedades de objetos                  |
| `for...of`   | Para percorrer valores de iteráveis (arrays, strings)   |
| `forEach`    | Para operações simples em cada elemento de um array     |

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/> 