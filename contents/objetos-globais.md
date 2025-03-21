<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🌐 Objetos Globais em JavaScript

Os Objetos Globais em JavaScript estão sempre disponíveis em qualquer contexto, sem a necessidade de importação. Eles fornecem funcionalidades essenciais e úteis que podem ser utilizadas em diferentes partes do seu código.

## 🧮 Math

O objeto `Math` fornece métodos e propriedades para operações matemáticas avançadas.

### Propriedades comuns:
- `Math.PI`: Retorna o valor de π (3.141592...)
- `Math.E`: Retorna o número de Euler (2.718281...)

### Métodos úteis:

```javascript
// Arredondamento
console.log(Math.round(4.7));    // 5 - Arredonda para o inteiro mais próximo
console.log(Math.floor(4.7));    // 4 - Arredonda para baixo
console.log(Math.ceil(4.3));     // 5 - Arredonda para cima
console.log(Math.trunc(4.7));    // 4 - Remove a parte decimal

// Operações matemáticas
console.log(Math.random());      // Número aleatório entre 0 e 1
console.log(Math.max(10, 20, 30)); // 30 - Retorna o maior valor
console.log(Math.min(10, 20, 30)); // 10 - Retorna o menor valor
console.log(Math.pow(2, 3));     // 8 - Potência (2³)
console.log(Math.sqrt(16));      // 4 - Raiz quadrada
console.log(Math.abs(-5));       // 5 - Valor absoluto

// Exemplo prático: número aleatório entre 1 e 100
const aleatorio = Math.floor(Math.random() * 100) + 1;
console.log(aleatorio);
```

## 📅 Date

O objeto `Date` permite trabalhar com datas e horários, essencial para aplicações que envolvem agendamentos, cálculos de tempo ou exibição de datas.

```javascript
// Criando objetos Date
const agora = new Date();                    // Data e hora atual
const data1 = new Date('2023-12-25');        // Data específica
const data2 = new Date(2023, 11, 25, 20, 30); // Ano, mês (0-11), dia, hora, minuto

// Obtendo componentes
console.log(agora.getFullYear());            // Ano (ex: 2023)
console.log(agora.getMonth());               // Mês (0-11, onde 0 é janeiro)
console.log(agora.getDate());                // Dia do mês (1-31)
console.log(agora.getDay());                 // Dia da semana (0-6, onde 0 é domingo)
console.log(agora.getHours());               // Hora (0-23)
console.log(agora.getMinutes());             // Minutos (0-59)

// Formatação de datas
console.log(agora.toLocaleDateString('pt-BR')); // Data no formato brasileiro
console.log(agora.toLocaleTimeString('pt-BR')); // Hora no formato brasileiro
console.log(agora.toLocaleString('pt-BR'));     // Data e hora completas

// Exemplo prático: cálculo de diferença entre datas (em dias)
const dataInicial = new Date('2023-01-01');
const dataFinal = new Date('2023-12-31');
const diferencaEmMs = dataFinal - dataInicial;
const diferencaEmDias = Math.floor(diferencaEmMs / (1000 * 60 * 60 * 24));
console.log(`Diferença: ${diferencaEmDias} dias`); // 364 dias
```

## 📋 JSON

O objeto `JSON` (JavaScript Object Notation) é fundamental para a comunicação com APIs e armazenamento de dados estruturados.

```javascript
// Convertendo objeto JavaScript para string JSON
const usuario = { 
  nome: "Ana", 
  idade: 28,
  ativo: true,
  habilidades: ["JavaScript", "HTML", "CSS"]
};
const jsonString = JSON.stringify(usuario);
console.log(jsonString);
// Saída: {"nome":"Ana","idade":28,"ativo":true,"habilidades":["JavaScript","HTML","CSS"]}

// Convertendo string JSON para objeto JavaScript
const objetoUsuario = JSON.parse(jsonString);
console.log(objetoUsuario.nome);      // Ana
console.log(objetoUsuario.habilidades[0]); // JavaScript

// Formatando JSON para facilitar leitura (com indentação)
console.log(JSON.stringify(usuario, null, 2));
```

## 🌐 Global Functions

JavaScript fornece funções globais que podem ser chamadas diretamente:

```javascript
// parseInt e parseFloat
console.log(parseInt("42"));          // 42 (número)
console.log(parseInt("42px"));        // 42 (ignora caracteres não numéricos)
console.log(parseInt("0xFF", 16));    // 255 (interpreta como hexadecimal)
console.log(parseFloat("3.14"));      // 3.14

// encodeURI e decodeURI
const url = "https://exemplo.com/pesquisa?q=JavaScript é incrível";
const urlCodificada = encodeURI(url);
console.log(urlCodificada); // https://exemplo.com/pesquisa?q=JavaScript%20%C3%A9%20incr%C3%ADvel
console.log(decodeURI(urlCodificada)); // volta para a URL original

// setTimeout e setInterval
setTimeout(() => {
  console.log("Executado após 2 segundos");
}, 2000);

let contador = 0;
const intervalo = setInterval(() => {
  console.log(`Contador: ${++contador}`);
  if (contador >= 5) {
    clearInterval(intervalo); // Para o intervalo após 5 execuções
  }
}, 1000);
```

## 📐 Array

O objeto global `Array` fornece métodos estáticos e protótipos para manipular arrays:

```javascript
// Métodos estáticos
const numeros = Array.from("123"); // Cria array a partir de um iterável
console.log(numeros); // ['1', '2', '3']

console.log(Array.isArray([1, 2, 3])); // true
console.log(Array.isArray("123"));    // false

// Criando arrays com preenchimento
const zeros = Array(5).fill(0);
console.log(zeros); // [0, 0, 0, 0, 0]

// Encontrando elementos
const frutas = ["maçã", "banana", "laranja", "uva"];
console.log(frutas.includes("banana")); // true
console.log(frutas.indexOf("laranja"));  // 2

// Transformação de arrays
const dobrados = [1, 2, 3].map(n => n * 2);
console.log(dobrados); // [2, 4, 6]

const soma = [1, 2, 3, 4].reduce((acc, n) => acc + n, 0);
console.log(soma); // 10
```

## 🔤 String

O objeto global `String` fornece métodos para manipulação de texto:

```javascript
const texto = "JavaScript é incrível!";

// Buscando informações
console.log(texto.length);            // 23 (comprimento)
console.log(texto.indexOf("Script"));  // 4 (posição onde começa)
console.log(texto.includes("incrível")); // true

// Transformação
console.log(texto.toUpperCase());      // JAVASCRIPT É INCRÍVEL!
console.log(texto.toLowerCase());      // javascript é incrível!
console.log(texto.replace("incrível", "fantástico")); // JavaScript é fantástico!

// Extração
console.log(texto.substring(0, 10));  // JavaScript
console.log(texto.slice(-10));        // incrível!
console.log(texto.split(" "));        // ['JavaScript', 'é', 'incrível!']

// Remoção de espaços
const textoComEspacos = "  texto com espaços  ";
console.log(textoComEspacos.trim());  // "texto com espaços"
```

## 🔢 Number

O objeto `Number` fornece métodos para trabalhar com valores numéricos:

```javascript
// Constantes
console.log(Number.MAX_VALUE);       // Maior número representável
console.log(Number.MIN_VALUE);       // Menor número positivo representável
console.log(Number.POSITIVE_INFINITY); // Infinito positivo

// Verificação
console.log(Number.isInteger(42));   // true
console.log(Number.isInteger(42.5)); // false
console.log(Number.isNaN(NaN));      // true

// Formatação
const preco = 1234.56;
console.log(preco.toFixed(2));       // "1234.56" (2 casas decimais)
console.log(preco.toLocaleString('pt-BR', {
  style: 'currency',
  currency: 'BRL'
})); // "R$ 1.234,56"
```

## 📝 Promise

O objeto global `Promise` é essencial para programação assíncrona:

```javascript
// Criando uma Promise
const minhaPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    const sucesso = true;
    if (sucesso) {
      resolve("Operação concluída com sucesso!");
    } else {
      reject("Ocorreu um erro!");
    }
  }, 1000);
});

// Consumindo a Promise
minhaPromise
  .then(resultado => console.log(resultado))
  .catch(erro => console.error(erro))
  .finally(() => console.log("Processamento finalizado"));

// Exemplo prático: simulando requisição de API
function buscarDados(id) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (id > 0) {
        resolve({ id, nome: "Produto X", preco: 99.99 });
      } else {
        reject("ID inválido");
      }
    }, 1500);
  });
}

buscarDados(123)
  .then(produto => console.log(`Produto encontrado: ${produto.nome}`))
  .catch(erro => console.error(`Erro: ${erro}`));
```

## 🔍 RegExp

O objeto `RegExp` permite trabalhar com expressões regulares para busca e manipulação de padrões em strings:

```javascript
// Criando expressões regulares
const padrao1 = /\d{2}-\d{9}/;           // Sintaxe literal
const padrao2 = new RegExp('\\d{2}-\\d{9}'); // Sintaxe com construtor

// Testando padrões
const telefone = "11-987654321";
console.log(padrao1.test(telefone));     // true

// Encontrando correspondências
const texto = "Contatos: 11-987654321 e 21-123456789";
const matches = texto.match(/\d{2}-\d{9}/g);
console.log(matches); // ["11-987654321", "21-123456789"]

// Substituição com regex
const resultado = texto.replace(/(\d{2})-(\d{9})/g, "($1) $2");
console.log(resultado); // "Contatos: (11) 987654321 e (21) 123456789"
```

---

> 💡 **Dica**: Os objetos globais tornam o JavaScript uma linguagem poderosa para diversas tarefas, desde manipulação de dados até operações assíncronas. Familiarize-se com estes objetos para escrever código mais eficiente e expressivo.

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>