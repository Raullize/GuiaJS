<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# Operadores de Atribuição

Os operadores de atribuição são utilizados para atribuir valores a variáveis. JavaScript oferece vários operadores que combinam operações com atribuição.

## Operadores Básicos

| Operador | Descrição | Exemplo | Equivalente a |
|----------|-----------|---------|---------------|
| `=`      | Atribuição simples | `x = y` | `x = y` |
| `+=`     | Atribuição com adição | `x += y` | `x = x + y` |
| `-=`     | Atribuição com subtração | `x -= y` | `x = x - y` |
| `*=`     | Atribuição com multiplicação | `x *= y` | `x = x * y` |
| `/=`     | Atribuição com divisão | `x /= y` | `x = x / y` |
| `%=`     | Atribuição com resto | `x %= y` | `x = x % y` |

## Exemplos Básicos

```js
let x = 10;

// Atribuição com adição
x += 5; // x agora é 15 (10 + 5)
console.log(x); // 15

// Atribuição com subtração
x -= 3; // x agora é 12 (15 - 3)
console.log(x); // 12

// Atribuição com multiplicação
x *= 2; // x agora é 24 (12 * 2)
console.log(x); // 24

// Atribuição com divisão
x /= 4; // x agora é 6 (24 / 4)
console.log(x); // 6

// Atribuição com resto
x %= 4; // x agora é 2 (6 % 4 = 2)
console.log(x); // 2
```

## Operadores Avançados

JavaScript também oferece operadores de atribuição para operações bit a bit e de deslocamento.

| Operador | Descrição | Exemplo | Equivalente a |
|----------|-----------|---------|---------------|
| `**=`    | Atribuição com exponenciação | `x **= y` | `x = x ** y` |
| `<<=`    | Atribuição com deslocamento à esquerda | `x <<= y` | `x = x << y` |
| `>>=`    | Atribuição com deslocamento à direita | `x >>= y` | `x = x >> y` |
| `>>>=`   | Atribuição com deslocamento à direita sem sinal | `x >>>= y` | `x = x >>> y` |
| `&=`     | Atribuição com AND bit a bit | `x &= y` | `x = x & y` |
| `\|=`    | Atribuição com OR bit a bit | `x \|= y` | `x = x \| y` |
| `^=`     | Atribuição com XOR bit a bit | `x ^= y` | `x = x ^ y` |
| `&&=`    | Atribuição com AND lógico (ES2021) | `x &&= y` | `x = x && y` |
| `\|\|=`  | Atribuição com OR lógico (ES2021) | `x \|\|= y` | `x = x \|\| y` |
| `??=`    | Atribuição com operador de coalescência nula (ES2021) | `x ??= y` | `x = x ?? y` |

## Exemplos Avançados

```js
// Atribuição com exponenciação (ES2016)
let num = 2;
num **= 3; // num agora é 8 (2 elevado a 3)
console.log(num); // 8

// Operadores lógicos de atribuição (ES2021)
let a;
let b = "valor padrão";

// Atribuição com OR lógico - atribui apenas se o valor atual for falsy
a ||= b; // Equivalente a: a = a || b
console.log(a); // "valor padrão"

// Atribuição com AND lógico - atribui apenas se o valor atual for truthy
a = "valor existente";
a &&= "novo valor"; // Equivalente a: a = a && "novo valor"
console.log(a); // "novo valor"

// Atribuição com coalescência nula - atribui apenas se o valor atual for null ou undefined
let c = null;
c ??= "valor não nulo"; // Equivalente a: c = c ?? "valor não nulo"
console.log(c); // "valor não nulo"

let d = false; // falsy, mas não é null nem undefined
d ??= "teste";
console.log(d); // false (mantém o valor original)
```

## Aplicações Práticas

### 1. Contador Simples

```js
let contador = 0;

function incrementar() {
  contador += 1;
  return contador;
}

console.log(incrementar()); // 1
console.log(incrementar()); // 2
```

### 2. Valores Padrão (antes do ES2020)

```js
function configurarOpcoes(opcoes) {
  opcoes = opcoes || {};
  opcoes.tamanho ||= "médio";
  opcoes.cor ||= "azul";
  
  return opcoes;
}

const minhasOpcoes = configurarOpcoes({cor: "vermelho"});
console.log(minhasOpcoes); // {tamanho: "médio", cor: "vermelho"}
```

### 3. Acumulação em Loops

```js
const numeros = [1, 2, 3, 4, 5];
let soma = 0;

for (let num of numeros) {
  soma += num;
}

console.log(soma); // 15
```

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>