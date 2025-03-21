<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 📊 Tipos de Dados

JavaScript possui diversos tipos de dados que podem ser divididos em duas categorias principais: **Primitivos** e **Referência**.

## Tipos Primitivos
- `String`: Sequências de caracteres, por exemplo: `'Olá'` ou `"Mundo"`.
- `Number`: Números, como `42` ou `3.14`.
- `Boolean`: Verdadeiro (`true`) ou falso (`false`).
- `Undefined`: Variável declarada sem valor.
- `Null`: Representa ausência intencional de valor.
- `Symbol`: Valor único e imutável (ES6+).
- `BigInt`: Números inteiros de precisão arbitrária (ES2020+).

## Tipos de Referência
- `Object`: Coleção de pares chave-valor.
- `Array`: Lista ordenada de valores.
- `Function`: Bloco de código reutilizável.
- `Date`: Representa datas e horários.
- `RegExp`: Expressões regulares.
- `Map`, `Set`, etc.: Estruturas de dados especializadas (ES6+).

## Exemplo Básico:

```js
// Primitivos
let nome = "João";      // String
let idade = 25;         // Number
let ativo = true;       // Boolean
let indefinido;         // Undefined
let nulo = null;        // Null

// Referência
let pessoa = { nome: "Maria", idade: 30 };  // Object
let numeros = [1, 2, 3, 4, 5];              // Array
let somar = function(a, b) { return a + b }; // Function
```

Para uma explicação mais detalhada sobre as diferenças entre tipos primitivos e de referência, consulte [Tipos Primitivos vs Tipos de Referência](tipos-primitivos-referencia.md).

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>