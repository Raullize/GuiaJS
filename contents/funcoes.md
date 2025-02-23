<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🔢 Funções 

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

## Funções Anônimas
Funções anônimas são aquelas que não têm um nome e geralmente são atribuídas a uma variável. Elas são úteis quando você deseja criar uma função rapidamente ou utilizá-la como argumento.

Exemplo:

```javascript
const multiplica = function(a, b) {
    return a * b;
};
console.log(multiplica(3, 4)); // Saída: 12
```

## Funções de Alta Ordem
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

## Recursão
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

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>