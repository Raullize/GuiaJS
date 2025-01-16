# Guia Completo de JavaScript (GuiaJS) 🚀

Bem-vindo ao GuiaJS, um recurso prático e abrangente para aprender JavaScript, desde conceitos básicos até tópicos mais avançados. Este guia é perfeito para iniciantes e intermediários que desejam aprender ou revisar os fundamentos dessa poderosa linguagem de programação.

## O que é JavaScript? 🤔
JavaScript é uma linguagem de programação leve, interpretada e baseada em protótipos. É amplamente utilizada para adicionar interatividade às páginas web, manipular elementos HTML/CSS e desenvolver aplicações modernas.

## Como criar e usar um arquivo JavaScript 📄

Para adicionar um arquivo JavaScript ao seu projeto, siga estes passos:

1. Crie um arquivo com a extensão `.js`, por exemplo, `app.js`.
2. Adicione o script ao seu arquivo HTML utilizando a tag `<script>`.

Exemplo básico:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GuiaJS</title>
</head>
<body>
    <h1>Olá, JavaScript!</h1>
    <script src="app.js" defer></script>
</body>
</html>
```

### Sobre o atributo `defer`
- O atributo `defer` garante que o arquivo JavaScript será carregado em segundo plano e executado apenas após o carregamento completo do HTML.
- Isso melhora o desempenho da página e evita problemas de acesso a elementos DOM que ainda não foram renderizados.

## Tipos de Dados 📦

JavaScript possui diferentes tipos de dados para armazenar valores. Os mais comuns incluem:

- `String`: Sequências de caracteres, por exemplo: `'Olá'` ou `"Mundo"`.
- `Number`: Números, como `42` ou `3.14`.
- `Boolean`: Verdadeiro (`true`) ou falso (`false`).
- `Object`: Coleção de pares chave-valor.
- `Array`: Lista ordenada de valores.
- `Undefined`: Variável declarada sem valor.
- `Null`: Representa ausência intencional de valor.

Exemplo:

```javascript
let nome = "Raul";  // String
let idade = 25;      // Number
let ativo = true;    // Boolean
```

## Variáveis ✏️

Em JavaScript, você pode declarar variáveis utilizando `var`, `let` ou `const`:

- **`let`**: Declara variáveis locais e mutáveis.
- **`const`**: Declara variáveis locais imutáveis.
- **`var`**: Modo antigo de declarar variáveis (evite usar em projetos modernos).

Exemplo:

```javascript
let nome = "João";    // Pode ser alterado
const idade = 30;     // Não pode ser alterado
```

## Operadores e Expressões ➕➖✖️➗

Operadores em JavaScript permitem manipular valores. Alguns exemplos incluem:

- **Aritméticos**: `+`, `-`, `*`, `/`, `%`
- **Atribuição**: `=`, `+=`, `-=`, `*=`
- **Comparação**: `==`, `===`, `!=`, `<`, `>`
- **Lógicos**: `&&`, `||`, `!`

Exemplo:

```javascript
let a = 10;
let b = 20;
console.log(a + b); // Soma: 30
console.log(a > b); // Comparação: false
```

## Comentários 📝

Comentários ajudam a explicar partes do código e são ignorados pelo interpretador. Use:

- **Linha única**: `//`.
- **Multilinha**: `/* */`.

Exemplo:

```javascript
// Isso é um comentário de linha única

/*
Isso é um comentário
multilinha
*/
```

## Estruturas Condicionais 🔀

### **`if` e `else`**
A estrutura condicional `if` avalia uma condição e executa um bloco de código se ela for verdadeira. O `else` é opcional e é executado quando a condição é falsa.

Exemplo:

```javascript
let idade = 18;

if (idade >= 18) {
    console.log("Você é maior de idade.");
} else {
    console.log("Você é menor de idade.");
}
```

### **`switch`**
Usado para avaliar uma variável contra vários casos.

Exemplo:

```javascript
let cor = "azul";

switch (cor) {
    case "vermelho":
        console.log("A cor é vermelho.");
        break;
    case "azul":
        console.log("A cor é azul.");
        break;
    default:
        console.log("Cor desconhecida.");
}
```

## Estruturas de Repetição ♻️

### **`while`**
Executa um bloco de código enquanto a condição for verdadeira.

Exemplo:

```javascript
let contador = 0;

while (contador < 5) {
    console.log(contador);
    contador++;
}
```

### **`do...while`**
Semelhante ao `while`, mas garante que o bloco será executado pelo menos uma vez.

Exemplo:

```javascript
let contador = 0;

do {
    console.log(contador);
    contador++;
} while (contador < 5);
```

### **`for`**
Ideal para laços com um número definido de iterações.

Exemplo:

```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

## Arrays e Arrays Bidimensionais 🔢

### Arrays
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

### Arrays Bidimensionais

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

## Objetos 🔧

Objetos são coleções de pares chave-valor.

Exemplo:

```javascript
let pessoa = {
    nome: "João",
    idade: 25,
    saudacao: function() {
        return `Olá, meu nome é ${this.nome}`;
    }
};
console.log(pessoa.saudacao());
```

## Funções 🔢

### O que são Funções?
Funções são blocos de código reutilizáveis que realizam uma tarefa específica. Elas ajudam a organizar e modularizar o código, tornando-o mais legível e fácil de manter. Uma função pode receber parâmetros como entrada e retornar um resultado.

### Declaração de Função
A maneira mais comum de criar uma função é utilizando a palavra-chave `function`.

Exemplo:

```javascript
function soma(a, b) {
    return a + b; // Retorna a soma de a e b
}
console.log(soma(2, 3)); // Saída: 5
```
- **Parâmetros (a, b)**: São os valores de entrada fornecidos à função.
- **Retorno**: O valor produzido pela função (neste caso, a soma).

### Funções Anônimas
Funções anônimas são aquelas que não têm um nome e geralmente são atribuídas a uma variável. Elas são úteis quando você deseja criar uma função rapidamente ou utilizá-la como argumento.

Exemplo:

```javascript
const multiplica = function(a, b) {
    return a * b;
};
console.log(multiplica(3, 4)); // Saída: 12
```

### Funções de Alta Ordem
Funções de alta ordem são aquelas que podem:

1. Receber outras funções como argumento.
2. Retornar uma função como resultado.

Essas funções são muito úteis para manipular arrays e implementar lógica de forma concisa.

### Exemplo:

```javascript
const numeros = [1, 2, 3, 4];
const dobrados = numeros.map(n => n * 2); // Aplica a função para cada elemento do array
console.log(dobrados); // Saída: [2, 4, 6, 8]
```

### Recursão
Recursão ocorre quando uma função se chama novamente até atingir uma condição de parada. É útel para resolver problemas como cálculos matemáticos ou navegação em estruturas de dados.

Exemplo:

```javascript
function fatorial(n) {
    if (n === 0) return 1; // Condição de parada
    return n * fatorial(n - 1); // Chama a função novamente
}
console.log(fatorial(5)); // Saída: 120
```

- A função **fatorial** calcula o produto de todos os números inteiros positivos até `n`.
- A condição de parada (`n === 0`) é essencial para evitar loops infinitos.

## Objetos Globais 🌐

Os Objetos Globais em JavaScript estão sempre disponíveis, sem a necessidade de importação. Eles oferecem funcionalidades úteis que podem ser utilizadas em diferentes contextos.

#### Math
O objeto `Math` fornece métodos e propriedades para realizar operações matemáticas.

Exemplos:

```javascript
console.log(Math.random()); // Número aleatório entre 0 e 1
console.log(Math.max(10, 20, 30)); // Maior número: 30
console.log(Math.pow(2, 3)); // Potência: 8 (2³)
```

#### Date
O objeto `Date` trabalha com datas e horários.

Exemplos:

```javascript
const agora = new Date();
console.log(agora); // Data e hora atual
console.log(agora.getFullYear()); // Ano atual
console.log(agora.toLocaleDateString()); // Data formatada
```

O `Date` é frequentemente usado para calcular diferenças de tempo, exibir a data atual ou criar aplicativos que dependem de datas.

#### JSON
O objeto `JSON` é utilizado para manipular dados no formato JSON (JavaScript Object Notation). É muito comum no envio e recebimento de dados em APIs.

Exemplo:

```javascript
const dados = { nome: "Raul", idade: 25 };
const stringJSON = JSON.stringify(dados); // Converte objeto em string JSON
console.log(stringJSON); // Saída: '{"nome":"Raul","idade":25}'

const objeto = JSON.parse(stringJSON); // Converte string JSON em objeto
console.log(objeto.nome); // Saída: Raul
```

- `JSON.stringify`: Converte objetos em strings JSON.
- `JSON.parse`: Converte strings JSON de volta em objetos.

## 🌐 Recursos Adicionais
- [MDN Web Docs: JavaScript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
- [W3Schools: JavaScript](https://www.w3schools.com/js/)
- [JavaScript.info](https://javascript.info)

---

Esperamos que este guia tenha sido útil para você! 😄 Continuaremos expandindo com mais dicas e exemplos.

🎯 **Contribuições são bem-vindas!** Caso queira adicionar algo, faça um pull request no repositório.
