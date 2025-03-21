<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🔢 Funções 

## O que são Funções?
Funções são blocos de código reutilizáveis que realizam uma tarefa específica. Elas ajudam a organizar e modularizar o código, tornando-o mais legível e fácil de manter. Uma função pode receber parâmetros como entrada e retornar um resultado.

## Estrutura Básica de uma Função

```javascript
// Sintaxe básica
function nomeDaFuncao(parametro1, parametro2) {
    // Código a ser executado
    return resultado; // Valor retornado (opcional)
}

// Exemplo prático
function soma(a, b) {
    return a + b;
}

console.log(soma(2, 3)); // Saída: 5
```

## Parâmetros e Argumentos

- **Parâmetros**: São variáveis listadas na definição da função.
- **Argumentos**: São os valores reais passados para a função quando ela é chamada.

```javascript
function saudar(nome, hora) {
    if (hora < 12) return `Bom dia, ${nome}!`;
    if (hora < 18) return `Boa tarde, ${nome}!`;
    return `Boa noite, ${nome}!`;
}

console.log(saudar("Maria", 15)); // "Boa tarde, Maria!"
```

## Retorno de Funções

Uma função pode retornar um valor usando a declaração `return`. Quando encontrado, o `return` encerra a execução da função e devolve o valor especificado.

```javascript
function calcularArea(largura, altura) {
    return largura * altura;
}

const area = calcularArea(5, 3);
console.log(area); // 15
```

Se nenhum valor for retornado explicitamente, a função retorna `undefined`.

## Escopo de Variáveis

Variáveis declaradas dentro de uma função são locais a ela e não podem ser acessadas fora da função.

```javascript
function teste() {
    const local = "Eu sou local";
    console.log(local); // "Eu sou local"
}

teste();
// console.log(local); // Erro: local não está definido
```

Para uma explicação detalhada sobre os diferentes tipos de funções em JavaScript (function declarations, function expressions, arrow functions, etc.), consulte [Tipos de Funções](tipos-funcoes.md).

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>