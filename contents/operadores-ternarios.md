<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# Operadores Ternários

O operador ternário é uma forma concisa de escrever uma expressão condicional. É o único operador em JavaScript que aceita três operandos.

## Sintaxe

```js
condição ? expressão_se_verdadeiro : expressão_se_falso
```

## Exemplos Básicos

```js
// Exemplo 1: Verificando idade
const idade = 18;
const status = idade >= 18 ? "Adulto" : "Menor de idade";
console.log(status); // "Adulto"

// Exemplo 2: Verificando se um número é par ou ímpar
const numero = 7;
const parOuImpar = numero % 2 === 0 ? "Par" : "Ímpar";
console.log(parOuImpar); // "Ímpar"
```

## Quando Usar Operadores Ternários

### ✅ Recomendado:
- Para atribuições simples baseadas em condições
- Para retornos condicionais em funções
- Quando a expressão é curta e clara

```js
// Bom uso: atribuição simples
const mensagem = userLogado ? "Bem-vindo de volta!" : "Por favor, faça login";

// Bom uso: retorno condicional
function verificarAcesso(usuario) {
  return usuario.premium ? "Acesso total" : "Acesso básico";
}
```

### ❌ Não Recomendado:
- Condições aninhadas complexas
- Expressões muito longas
- Quando prejudica a legibilidade

```js
// Não recomendado: operadores ternários aninhados
const resultado = a > b 
  ? a > c 
    ? "a é o maior" 
    : "c é o maior" 
  : b > c 
    ? "b é o maior" 
    : "c é o maior";
    
// Melhor usar if/else para casos complexos
```

## Encadeamento de Operadores Ternários

Em alguns casos, é possível encadear operadores ternários, mas use com moderação:

```js
const nota = 85;
const conceito = 
  nota >= 90 ? 'A' : 
  nota >= 80 ? 'B' : 
  nota >= 70 ? 'C' : 
  nota >= 60 ? 'D' : 'F';

console.log(conceito); // 'B'
```

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>