<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 📊 Precedência de Operadores

A precedência de operadores em JavaScript determina a ordem na qual as operações são processadas em uma expressão.

## 📋 Tabela de Precedência

Os operadores abaixo estão listados em ordem decrescente de precedência (dos mais prioritários para os menos prioritários):

| Precedência | Categoria | Operadores |
|-------------|-----------|------------|
| 1 | Agrupamento | `( ... )` |
| 2 | Acesso a membros/índices | `obj.prop`, `obj["prop"]`, `array[i]` |
| 3 | Chamada de função/expressões `new` | `func()`, `new Objeto()` |
| 4 | Incremento/Decremento | `++`, `--` (como sufixo ou prefixo) |
| 5 | Negação/Conversão de tipos | `!`, `+`, `-`, `typeof`, `void`, `delete` |
| 6 | Exponenciação | `**` |
| 7 | Multiplicação/Divisão/Módulo | `*`, `/`, `%` |
| 8 | Adição/Subtração | `+`, `-` |
| 9 | Operadores bit a bit | `<<`, `>>`, `>>>` |
| 10 | Comparações | `<`, `<=`, `>`, `>=`, `instanceof`, `in` |
| 11 | Igualdade | `==`, `!=`, `===`, `!==` |
| 12 | AND bit a bit | `&` |
| 13 | XOR bit a bit | `^` |
| 14 | OR bit a bit | `\|` |
| 15 | AND lógico | `&&` |
| 16 | OR lógico | `\|\|` |
| 17 | Operador nulo opcional | `?.` |
| 18 | Condicional (ternário) | `? :` |
| 19 | Atribuição | `=`, `+=`, `-=`, `*=`, etc. |
| 20 | Vírgula | `,` |

## 📚 Exemplos Práticos

### Expressões Matemáticas

```js
// Precedência entre multiplicação e adição
console.log(2 + 3 * 4);     // 14 (não 20)
console.log((2 + 3) * 4);   // 20 (parênteses alteram a precedência)

// Exponenciação tem precedência sobre multiplicação
console.log(2 * 3 ** 2);    // 18 (não 36)
console.log((2 * 3) ** 2);  // 36
```

### Operadores Lógicos

```js
// && tem precedência maior que ||
console.log(true || false && false); // true
console.log((true || false) && false); // false
```

### Múltiplos Operadores

```js
let a = 5;
let b = 10;
let c = 15;

// Avaliação complexa
let resultado = a + b * c / 5 - 3;
console.log(resultado); // 32

// Equivalente a:
let resultadoDecomposto = a + ((b * c) / 5) - 3;
console.log(resultadoDecomposto); // 32
```

### Operadores de Incremento/Decremento

```js
let x = 5;
let y = 10;
let z;

// Precedência entre incremento e atribuição
z = x++ + y;
console.log(z);  // 15 (x é usado e depois incrementado)
console.log(x);  // 6

// Redefinindo
x = 5;
z = ++x + y;
console.log(z);  // 16 (x é incrementado primeiro)
console.log(x);  // 6
```

## 🔧 Dicas para Evitar Problemas de Precedência

1. **Use parênteses** para deixar claro a ordem desejada de operações
2. **Divida expressões complexas** em expressões menores e mais simples
3. **Atribua resultados intermediários** a variáveis para maior clareza
4. **Evite confiar implicitamente** na precedência de operadores para código mais legível

```js
// Expressão complexa
let resultado = a && b || c && d;

// Mais claro com parênteses
let resultadoClaro = (a && b) || (c && d);

// Ainda mais claro com variáveis intermediárias
let parte1 = a && b;
let parte2 = c && d;
let resultadoMuitoClaro = parte1 || parte2;
```

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/> 