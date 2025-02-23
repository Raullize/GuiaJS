<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🌐 Objetos Globais 

Os Objetos Globais em JavaScript estão sempre disponíveis, sem a necessidade de importação. Eles oferecem funcionalidades úteis que podem ser utilizadas em diferentes contextos.

## Math
O objeto `Math` fornece métodos e propriedades para realizar operações matemáticas.

Exemplos:

```javascript
console.log(Math.random()); // Número aleatório entre 0 e 1
console.log(Math.max(10, 20, 30)); // Maior número: 30
console.log(Math.pow(2, 3)); // Potência: 8 (2³)
```

## Date
O objeto `Date` trabalha com datas e horários.

Exemplos:

```javascript
const agora = new Date();
console.log(agora); // Data e hora atual
console.log(agora.getFullYear()); // Ano atual
console.log(agora.toLocaleDateString()); // Data formatada
```

O `Date` é frequentemente usado para calcular diferenças de tempo, exibir a data atual ou criar aplicativos que dependem de datas.

## JSON
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

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>