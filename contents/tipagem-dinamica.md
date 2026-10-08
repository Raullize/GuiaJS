<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# Tipagem Dinâmica em JavaScript

JavaScript é uma linguagem de **tipagem dinâmica**, o que significa que o tipo de uma variável é determinado automaticamente pelo valor que ela armazena e pode mudar durante a execução do programa.

## Compreendendo a Tipagem Dinâmica

Em linguagens de tipagem estática (como Java, C++ ou TypeScript), você precisa declarar o tipo de uma variável explicitamente, e esse tipo não pode mudar:

```java
// Java - tipagem estática
String nome = "Maria";
int idade = 30;

// Isso causaria um erro de compilação
nome = 42; // Erro: não é possível atribuir um int a uma String
```

Em JavaScript, no entanto, os tipos são flexíveis:

```js
// JavaScript - tipagem dinâmica
let variavel = "texto";  // variavel é string
console.log(typeof variavel); // "string"

variavel = 42;           // agora variavel é número
console.log(typeof variavel); // "number"

variavel = true;         // agora variavel é booleano
console.log(typeof variavel); // "boolean"

variavel = { nome: "valor" }; // agora variavel é objeto
console.log(typeof variavel); // "object"
```

## Conversão Automática de Tipos

Devido à tipagem dinâmica, JavaScript realiza conversões automáticas (implícitas) de tipos em muitas operações.

### Exemplo com operações matemáticas:

```js
let resultado = "5" + 2;
console.log(resultado); // "52" (string)
// O número 2 foi convertido para string e concatenado

resultado = "5" - 2;
console.log(resultado); // 3 (number)
// A string "5" foi convertida para número

resultado = "5" * "2";
console.log(resultado); // 10 (number)
// Ambas as strings foram convertidas para números
```

### Exemplo com comparações:

```js
console.log(5 == "5");   // true (comparação loose, valores são considerados iguais)
console.log(5 === "5");  // false (comparação strict, tipos diferentes)

console.log(0 == false); // true (conversão implícita)
console.log(0 === false); // false (tipos diferentes)

console.log("" == 0);    // true (string vazia é convertida para 0)
console.log("" === 0);   // false (tipos diferentes)
```

## Conversão Explícita de Tipos

Para controlar melhor o comportamento do seu código, você pode realizar conversões explícitas de tipos:

```js
// Conversão para string
let num = 42;
let texto = String(num);  // "42"
// ou
texto = num.toString();   // "42"
// ou
texto = num + "";         // "42" (conversão implícita via concatenação)

// Conversão para número
let str = "42";
let numero = Number(str);  // 42
// ou
numero = parseInt(str, 10); // 42 (base 10)
// ou
numero = parseFloat(str);   // 42.0
// ou
numero = +str;              // 42 (operador unário +)

// Conversão para booleano
let valor = "texto";
let booleano = Boolean(valor); // true
// ou
booleano = !!valor;            // true (dupla negação)
```

## Valores Truthy e Falsy

Devido à conversão implícita para booleano, JavaScript tem o conceito de valores "truthy" e "falsy":

### Valores Falsy (avaliam como false):
- `false`
- `0`, `-0`, `0n` (BigInt zero)
- `""`, `''`, ` `` ` (string vazia)
- `null`
- `undefined`
- `NaN`

### Valores Truthy (avaliam como true):
- Qualquer outro valor, incluindo:
  - `true`
  - Qualquer número diferente de zero
  - Qualquer string não vazia
  - Objetos (mesmo vazios)
  - Arrays (mesmo vazios)
  - Funções

```js
if ("texto") {
  console.log("String não vazia é truthy");
}

if ({}) {
  console.log("Objeto vazio é truthy");
}

if (!0) {
  console.log("Zero é falsy");
}

if (!"") {
  console.log("String vazia é falsy");
}
```

## Vantagens e Desvantagens da Tipagem Dinâmica

### ✅ Vantagens:
- **Flexibilidade**: código mais conciso e adaptável
- **Prototipagem rápida**: menos preocupação com definições de tipo
- **Menos boilerplate**: reduz a quantidade de código necessário

### ⚠️ Desvantagens:
- **Erros sutis**: problemas podem surgir devido a conversões implícitas inesperadas
- **Debugging mais difícil**: erros de tipo são detectados apenas em tempo de execução
- **Performance**: pode ser menos eficiente que tipagem estática

## Melhores Práticas com Tipagem Dinâmica

1. **Use comparações estritas** (`===` e `!==`) para evitar conversões implícitas
2. **Verifique tipos** explicitamente quando necessário (`typeof`, `instanceof`)
3. **Faça conversões explícitas** para tornar suas intenções claras
4. **Considere usar TypeScript** para projetos mais complexos
5. **Use ferramentas de análise estática** como ESLint para detectar problemas potenciais

```js
// Exemplo de boas práticas
function calcular(a, b) {
  // Verificação explícita de tipos
  if (typeof a !== 'number' || typeof b !== 'number') {
    throw new TypeError('Os argumentos devem ser números');
  }
  
  return a + b;
}
```

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>