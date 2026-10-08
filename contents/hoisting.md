<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# Hoisting em JavaScript

## O que é Hoisting?

**Hoisting** (elevação) é um comportamento do JavaScript onde declarações de variáveis e funções são movidas para o topo de seu escopo atual antes da execução do código. Isso significa que você pode usar variáveis e funções antes de declará-las no código.

## Como funciona o Hoisting?

### 1. Hoisting com Variáveis

#### Variáveis declaradas com `var`

Quando você declara uma variável com `var`, a declaração é "elevada" para o topo do escopo, mas a inicialização permanece no local original:

```js
console.log(nome); // undefined (não dá erro)
var nome = "Maria";

// O código acima é interpretado como:
var nome;
console.log(nome); // undefined
nome = "Maria";
```

#### Variáveis declaradas com `let` e `const`

Variáveis declaradas com `let` e `const` também são hoisted, mas ficam em uma "zona morta temporal" (Temporal Dead Zone) até o ponto da declaração:

```js
// console.log(idade); // Erro: Cannot access 'idade' before initialization
let idade = 25;

// console.log(PI); // Erro: Cannot access 'PI' before initialization
const PI = 3.14;
```

### 2. Hoisting com Funções

#### Function Declarations (Declarações de Função)

Declarações de função são completamente hoisted com seu corpo:

```js
// Isso funciona!
console.log(somar(2, 3)); // 5

// A função foi "elevada" para o topo
function somar(a, b) {
  return a + b;
}
```

#### Function Expressions (Expressões de Função)

Expressões de função se comportam como variáveis:

```js
// console.log(subtrair(5, 2)); // Erro: subtrair is not a function
var subtrair = function(a, b) {
  return a - b;
};

// O código acima é interpretado como:
var subtrair;
// console.log(subtrair(5, 2)); // Erro: subtrair is not a function
subtrair = function(a, b) {
  return a - b;
};
```

#### Arrow Functions

Arrow functions se comportam como expressões de função:

```js
// console.log(multiplicar(3, 4)); // Erro: multiplicar is not a function
var multiplicar = (a, b) => a * b;
```

## Implicações Práticas

### Vantagens

- Permite organizar o código, colocando funções no final do arquivo
- Facilita a leitura de algumas estruturas de código

### Desvantagens e Armadilhas

```js
// Problema comum com loops
var funcs = [];
for (var i = 0; i < 3; i++) {
  funcs[i] = function() {
    console.log("Valor: " + i);
  };
}

funcs[0](); // "Valor: 3" (não 0!)
funcs[1](); // "Valor: 3" (não 1!)
funcs[2](); // "Valor: 3" (não 2!)

// Solução com let (escopo de bloco)
var funcs2 = [];
for (let j = 0; j < 3; j++) {
  funcs2[j] = function() {
    console.log("Valor: " + j);
  };
}

funcs2[0](); // "Valor: 0"
funcs2[1](); // "Valor: 1"
funcs2[2](); // "Valor: 2"
```

## Boas Práticas

1. **Declare variáveis no topo do escopo**:
   ```js
   function exemplo() {
     var a, b, c; // Todas as declarações no topo
  
     // resto do código...
     a = 5;
     b = 10;
   }
   ```

2. **Prefira `let` e `const` ao invés de `var`**:
   - Reduz problemas relacionados ao hoisting
   - Escopo de bloco mais previsível

3. **Declare funções antes de usá-las**:
   - Mesmo que function declarations sejam hoisted, declare-as antes de usá-las para melhor legibilidade

4. **Entenda o hoisting, mas não dependa dele**:
   - Código que depende de hoisting pode ser difícil de entender e manter

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>