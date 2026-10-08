<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# Manipulação de Strings

## Concatenação de Strings

Em JavaScript, existem várias formas de concatenar (unir) strings:

### Operador `+`

```js
const nome = "Maria";
const sobrenome = "Silva";
const nomeCompleto = nome + " " + sobrenome;
console.log(nomeCompleto); // "Maria Silva"
```

### Concatenando Strings e Variáveis

```js
const idade = 25;
const mensagem = "Minha idade é " + idade + " anos.";
console.log(mensagem); // "Minha idade é 25 anos."
```

### Método `concat()`

```js
const parte1 = "Olá";
const parte2 = "mundo";
const saudacao = parte1.concat(", ", parte2, "!");
console.log(saudacao); // "Olá, mundo!"
```

## Template Literals (ES6+)

Os template literals, introduzidos no ES6, proporcionam uma maneira mais elegante de concatenar strings e variáveis:

### Sintaxe Básica

```js
const nome = "João";
const idade = 30;

// Usando template literals (observe as crases ` `)
const mensagem = `Olá, meu nome é ${nome} e tenho ${idade} anos.`;
console.log(mensagem); // "Olá, meu nome é João e tenho 30 anos."
```

### Expressões em Template Literals

Template literals podem conter expressões JavaScript:

```js
const preco = 19.99;
const quantidade = 3;
const mensagem = `Total: R$ ${(preco * quantidade).toFixed(2)}`;
console.log(mensagem); // "Total: R$ 59.97"
```

### Strings Multilinhas

Template literals preservam quebras de linha:

```js
const poema = `
Roses are red,
Violets are blue,
JavaScript is fun,
And so are you!
`;
console.log(poema);
/*
Roses are red,
Violets are blue,
JavaScript is fun,
And so are you!
*/
```

## Vantagens dos Template Literals

- Código mais legível
- Facilidade para incluir variáveis e expressões
- Suporte nativo a strings multilinhas
- Menos propenso a erros de sintaxe

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>