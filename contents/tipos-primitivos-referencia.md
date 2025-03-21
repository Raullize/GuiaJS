<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🧩 Tipos Primitivos vs Tipos de Referência

O JavaScript tem dois grandes grupos de tipos de dados: **primitivos** e **referência**. Entender a diferença entre eles é crucial para evitar bugs sutis em seu código.

## 📊 Tipos Primitivos

São valores imutáveis e armazenados diretamente na posição de memória que a variável acessa.

### Tipos Primitivos em JavaScript:

1. **String** - Texto entre aspas: `"Olá"`, `'Mundo'`
2. **Number** - Valores numéricos: `42`, `3.14`
3. **Boolean** - Valores lógicos: `true`, `false`
4. **undefined** - Valor de variáveis não inicializadas
5. **null** - Representa ausência intencional de valor
6. **Symbol** (ES6) - Valor único e imutável
7. **BigInt** (ES2020) - Números inteiros de precisão arbitrária

```js
// Exemplos de valores primitivos
const nome = "Maria";
const idade = 30;
const ativo = true;
const indefinido = undefined;
const nulo = null;
const simbolo = Symbol("descrição");
const numeroGrande = 9007199254740991n; // BigInt
```

## 🧬 Tipos de Referência

São objetos armazenados por referência. Variáveis destes tipos não contêm diretamente o valor, mas uma referência (ponteiro) para o local na memória onde o objeto está armazenado.

### Tipos de Referência em JavaScript:

1. **Object** - Objetos literais, instâncias
2. **Array** - Coleções ordenadas
3. **Function** - Funções e métodos
4. **Date** - Datas
5. **RegExp** - Expressões regulares
6. **Map**, **Set**, etc. (Coleções ES6)

```js
// Exemplos de valores de referência
const pessoa = { nome: "João", idade: 25 };
const frutas = ["maçã", "banana", "laranja"];
const somar = function(a, b) { return a + b; };
const hoje = new Date();
const regex = /\d+/g;
```

## 🔄 Comportamento na Atribuição e Comparação

### Primitivos: Cópia por Valor

```js
let a = 5;
let b = a; // 'b' recebe uma cópia do valor de 'a'

a = 10;
console.log(a); // 10
console.log(b); // 5 - não foi afetado pela mudança em 'a'
```

### Referências: Cópia por Referência

```js
let obj1 = { nome: "Ana" };
let obj2 = obj1; // 'obj2' aponta para o mesmo objeto que 'obj1'

obj1.nome = "Maria";
console.log(obj1.nome); // "Maria"
console.log(obj2.nome); // "Maria" - foi afetado pela mudança em 'obj1'
```

### Comparações

```js
// Primitivos: comparação por valor
console.log(5 === 5);           // true
console.log("abc" === "abc");   // true

// Referências: comparação por referência
console.log({} === {});         // false (referências diferentes)
console.log([] === []);         // false (referências diferentes)

const obj = {};
console.log(obj === obj);       // true (mesma referência)
```

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/> 