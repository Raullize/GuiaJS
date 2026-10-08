<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# Operadores de Comparação

Os operadores de comparação em JavaScript são utilizados para comparar valores e retornar um valor booleano (`true` ou `false`).

## Operadores Básicos

| Operador | Nome | Descrição | Exemplo |
|----------|------|-----------|---------|
| `==` | Igualdade | Compara se os valores são iguais (com conversão de tipo) | `5 == "5"` → `true` |
| `===` | Igualdade estrita | Compara se os valores e tipos são iguais | `5 === "5"` → `false` |
| `!=` | Desigualdade | Compara se os valores são diferentes (com conversão de tipo) | `5 != "6"` → `true` |
| `!==` | Desigualdade estrita | Compara se os valores ou tipos são diferentes | `5 !== "5"` → `true` |
| `>` | Maior que | Verifica se o valor da esquerda é maior que o da direita | `10 > 5` → `true` |
| `<` | Menor que | Verifica se o valor da esquerda é menor que o da direita | `10 < 5` → `false` |
| `>=` | Maior ou igual | Verifica se o valor da esquerda é maior ou igual ao da direita | `10 >= 10` → `true` |
| `<=` | Menor ou igual | Verifica se o valor da esquerda é menor ou igual ao da direita | `5 <= 10` → `true` |

## Igualdade vs. Igualdade Estrita

### Operador de Igualdade (`==`)

O operador `==` compara valores depois de converter ambos para um tipo comum.

```js
console.log(5 == 5);     // true
console.log(5 == "5");   // true (string "5" é convertida para número 5)
console.log(0 == false); // true (false é convertido para 0)
console.log(1 == true);  // true (true é convertido para 1)
console.log(null == undefined); // true
```

### Operador de Igualdade Estrita (`===`)

O operador `===` compara valores sem fazer conversão de tipo. Tanto o valor quanto o tipo devem ser iguais.

```js
console.log(5 === 5);     // true
console.log(5 === "5");   // false (tipos diferentes: number vs string)
console.log(0 === false); // false (tipos diferentes: number vs boolean)
console.log(1 === true);  // false (tipos diferentes: number vs boolean)
console.log(null === undefined); // false (tipos diferentes)
```

## Comparação de Objetos

Operadores de comparação comparam referências, não conteúdo, quando usados com objetos.

```js
const obj1 = { valor: 10 };
const obj2 = { valor: 10 };
const obj3 = obj1;

console.log(obj1 == obj2);  // false (referências diferentes)
console.log(obj1 === obj2); // false (referências diferentes)
console.log(obj1 == obj3);  // true (mesma referência)
console.log(obj1 === obj3); // true (mesma referência)
```

## Comparações Especiais

### NaN

`NaN` (Not a Number) tem um comportamento especial: ele não é igual a nada, nem a ele mesmo.

```js
console.log(NaN == NaN);  // false
console.log(NaN === NaN); // false

// Para verificar se um valor é NaN:
console.log(isNaN(NaN));       // true
console.log(Number.isNaN(NaN)); // true (mais preciso, ES6+)
```

### Null e Undefined

```js
console.log(null == undefined);  // true
console.log(null === undefined); // false

console.log(null == 0);  // false
console.log(undefined == 0); // false
```

## Operadores de Comparação em Condicionais

Esses operadores são frequentemente usados em estruturas condicionais:

```js
const idade = 18;

if (idade >= 18) {
  console.log("Maior de idade");
} else {
  console.log("Menor de idade");
}

// Com operador ternário
const status = idade >= 18 ? "Maior de idade" : "Menor de idade";
console.log(status);
```

## Comparações com Booleanos

```js
// Evite estas comparações
if (isValid == true) { ... }  // redundante
if (isValid == false) { ... } // redundante

// Prefira estas
if (isValid) { ... }         // mais conciso
if (!isValid) { ... }        // mais conciso
```

## Melhores Práticas

1. **Use `===` (igualdade estrita) por padrão** para evitar conversões de tipo inesperadas
2. **Entenda as regras de conversão de tipo** quando precisar usar `==`
3. **Seja explícito ao comparar com `null` ou `undefined`**
4. **Evite comparações diretas com `NaN`**; use `isNaN()` ou `Number.isNaN()`
5. **Para objetos, compare propriedades específicas** em vez do objeto inteiro

```js
// Exemplo de boa prática para comparação de objetos
function saoObjetosIguais(obj1, obj2) {
  return obj1.id === obj2.id && obj1.nome === obj2.nome;
}

// Verificando null e undefined de forma segura
const valor = obterValor();
if (valor === null || valor === undefined) {
  console.log("Valor não disponível");
}
// Ou de forma mais concisa (ES2020+)
if (valor === null || valor === undefined) {
  console.log("Valor não disponível");
}
```

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>