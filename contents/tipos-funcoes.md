<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🔢 Tipos de Funções em JavaScript

JavaScript oferece diversas formas de declarar e usar funções, cada uma com características específicas.

## 📝 Function Declaration (Declaração de Função)

A forma tradicional de definir funções, com o identificador `function` seguido do nome da função.

```js
function somar(a, b) {
  return a + b;
}

console.log(somar(5, 3)); // 8
```

**Características:**
- É **hoisted** (elevada): pode ser chamada antes de sua declaração no código
- Tem nome obrigatório
- Boa para funções principais do programa

## 📝 Function Expression (Expressão de Função)

Funções definidas dentro de uma expressão, geralmente atribuídas a uma variável.

```js
const multiplicar = function(a, b) {
  return a * b;
};

console.log(multiplicar(4, 2)); // 8
```

**Características:**
- **Não** é hoisted como uma função (apenas a variável, se for `var`)
- O nome da função é opcional (funções anônimas)
- Útil para funções que serão passadas como argumentos

## 🏹 Arrow Functions (Funções Flecha)

Introduzidas no ES6, são uma sintaxe mais concisa para escrever funções.

```js
// Arrow function básica
const dividir = (a, b) => {
  return a / b;
};

// Com um único parâmetro (parênteses opcionais)
const dobrar = a => a * 2;

// Com retorno implícito (sem chaves)
const subtrair = (a, b) => a - b;

console.log(dividir(10, 2)); // 5
console.log(dobrar(4));      // 8
console.log(subtrair(7, 3)); // 4
```

**Características:**
- Sintaxe mais concisa
- Não possui seu próprio `this` (herda do contexto de criação)
- Não tem `arguments`, `super` ou `new.target`
- Não pode ser usada como construtora (`new`)
- Ideal para funções curtas e callbacks

## 🏭 Funções Construtoras

Usadas para criar objetos usando o operador `new`.

```js
function Pessoa(nome, idade) {
  this.nome = nome;
  this.idade = idade;
  this.apresentar = function() {
    return `Olá, meu nome é ${this.nome} e tenho ${this.idade} anos`;
  };
}

const pessoa1 = new Pessoa("Ana", 28);
console.log(pessoa1.apresentar()); // "Olá, meu nome é Ana e tenho 28 anos"
```

**Características:**
- Usa convenção de nome com inicial maiúscula
- Usado com o operador `new`
- `this` refere-se ao novo objeto criado
- Alternativa às classes para criação de objetos (antes do ES6)

## 🎯 Métodos em Objetos

Funções definidas como propriedades de objetos.

```js
const calculadora = {
  a: 0,
  b: 0,
  
  definirValores(a, b) {
    this.a = a;
    this.b = b;
  },
  
  somar() {
    return this.a + this.b;
  },
  
  multiplicar() {
    return this.a * this.b;
  }
};

calculadora.definirValores(5, 3);
console.log(calculadora.somar()); // 8
```

**Características:**
- `this` refere-se ao objeto que contém o método
- Sintaxe concisa disponível no ES6+ (`metodo(){}` em vez de `metodo: function(){}`)

## 🏭 Factory Functions (Funções Fábrica)

Funções que criam e retornam objetos, sem usar `new`.

```js
function criarPessoa(nome, idade) {
  return {
    nome,
    idade,
    apresentar() {
      return `Olá, meu nome é ${this.nome} e tenho ${this.idade} anos`;
    }
  };
}

const pessoa2 = criarPessoa("Carlos", 32);
console.log(pessoa2.apresentar()); // "Olá, meu nome é Carlos e tenho 32 anos"
```

**Características:**
- Alternativa às funções construtoras e classes
- Não usa `new`
- Facilita a criação de closures e encapsulamento

## 🧮 IIFE (Immediately Invoked Function Expression)

Funções que são executadas imediatamente após serem definidas.

```js
(function() {
  const mensagem = "Esta função é executada imediatamente";
  console.log(mensagem);
})();

// Com parâmetros
(function(texto) {
  console.log(`Mensagem: ${texto}`);
})("Olá mundo");
```

**Características:**
- Cria um escopo isolado
- Evita poluir o escopo global
- Útil para isolar variáveis e evitar conflitos

## 🎭 Funções Geradoras (Generator Functions)

Funções que podem ser pausadas e retomadas, retornando um iterador.

```js
function* contador() {
  let i = 0;
  while (true) {
    yield i++;
  }
}

const gerador = contador();
console.log(gerador.next().value); // 0
console.log(gerador.next().value); // 1
console.log(gerador.next().value); // 2
```

**Características:**
- Definidas com `function*`
- Usam `yield` para pausar e retornar valores
- Mantém o estado entre chamadas
- Úteis para criar iteradores e lidar com sequências infinitas

## ⚙️ Hoisting e Funções

O "hoisting" é um comportamento do JavaScript que move declarações para o topo do escopo atual.

```js
// Function Declaration - hoisted
console.log(soma(2, 3)); // 5 - funciona antes da declaração
function soma(a, b) {
  return a + b;
}

// Function Expression - não hoisted da mesma forma
// console.log(subtracao(5, 2)); // Erro: subtracao is not a function
const subtracao = function(a, b) {
  return a - b;
};
```

> 📚 **Para uma explicação completa sobre hoisting em JavaScript, incluindo como ele afeta variáveis e funções, consulte o [guia dedicado sobre hoisting](hoisting.md).**

## 🔧 Parâmetros Default (Padrão)

A partir do ES6, é possível definir valores padrão para parâmetros de funções.

```js
function saudar(nome = "Visitante", saudacao = "Olá") {
  return `${saudacao}, ${nome}!`;
}

console.log(saudar());                  // "Olá, Visitante!"
console.log(saudar("Maria"));           // "Olá, Maria!"
console.log(saudar("João", "Bem-vindo")); // "Bem-vindo, João!"
```

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/> 