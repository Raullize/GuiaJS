<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🔧 Objetos em JavaScript

Objetos são coleções de pares chave-valor e uma das estruturas de dados mais importantes em JavaScript.

## 📋 Criação de Objetos

### Sintaxe Literal

```javascript
const pessoa = {
    nome: "João",
    idade: 25,
    cidade: "São Paulo",
    saudacao: function() {
        return `Olá, meu nome é ${this.nome}`;
    }
};

console.log(pessoa.saudacao()); // "Olá, meu nome é João"
```

### Construtor Object

```javascript
const pessoa = new Object();
pessoa.nome = "Maria";
pessoa.idade = 30;
pessoa.cidade = "Rio de Janeiro";
```

## 🎯 Short Syntax (Sintaxe Abreviada)

O ES6 introduziu várias formas de simplificar a criação de objetos:

### Property Shorthand

Quando o nome da propriedade é igual ao nome da variável:

```javascript
const nome = "Ana";
const idade = 28;
const profissao = "Desenvolvedora";

// Sintaxe tradicional
const pessoa1 = {
    nome: nome,
    idade: idade,
    profissao: profissao
};

// Short syntax (ES6+)
const pessoa2 = {
    nome,
    idade,
    profissao
};

console.log(pessoa2); // { nome: "Ana", idade: 28, profissao: "Desenvolvedora" }
```

### Method Shorthand

Sintaxe simplificada para métodos:

```javascript
// Sintaxe tradicional
const calculadora = {
    somar: function(a, b) {
        return a + b;
    },
    multiplicar: function(a, b) {
        return a * b;
    }
};

// Method shorthand (ES6+)
const calculadoraModerna = {
    somar(a, b) {
        return a + b;
    },
    multiplicar(a, b) {
        return a * b;
    }
};

console.log(calculadoraModerna.somar(5, 3)); // 8
```

### Computed Property Names

Propriedades com nomes dinâmicos:

```javascript
const propriedade = "cor";
const valor = "azul";

const objeto = {
    [propriedade]: valor,
    [`${propriedade}Secundaria`]: "verde"
};

console.log(objeto); // { cor: "azul", corSecundaria: "verde" }
```

## 🎁 Desestruturação de Objetos

A desestruturação permite extrair propriedades de objetos de forma concisa:

### Desestruturação Básica

```javascript
const pessoa = {
    nome: "Carlos",
    idade: 35,
    cidade: "Brasília",
    profissao: "Engenheiro"
};

// Extraindo propriedades
const { nome, idade } = pessoa;
console.log(nome); // "Carlos"
console.log(idade); // 35

// Extraindo todas as propriedades
const { nome: nomePessoa, idade: idadePessoa, cidade, profissao } = pessoa;
console.log(nomePessoa); // "Carlos"
```

### Renomeando Variáveis

```javascript
const usuario = {
    id: 123,
    email: "usuario@email.com",
    isActive: true
};

// Renomeando durante a desestruturação
const { id: userId, email: userEmail, isActive: ativo } = usuario;
console.log(userId); // 123
console.log(userEmail); // "usuario@email.com"
console.log(ativo); // true
```

### Valores Padrão

```javascript
const config = {
    host: "localhost",
    port: 3000
};

// Definindo valores padrão para propriedades que podem não existir
const { host, port, protocol = "http", timeout = 5000 } = config;
console.log(protocol); // "http" (valor padrão)
console.log(timeout); // 5000 (valor padrão)
```

### Desestruturação Aninhada

```javascript
const empresa = {
    nome: "TechCorp",
    endereco: {
        rua: "Rua das Flores, 123",
        cidade: "São Paulo",
        cep: "01234-567"
    },
    funcionarios: [
        { nome: "Ana", cargo: "Dev" },
        { nome: "Bruno", cargo: "Designer" }
    ]
};

// Desestruturação aninhada
const {
    nome: nomeEmpresa,
    endereco: { cidade, cep },
    funcionarios: [primeiroFuncionario]
} = empresa;

console.log(nomeEmpresa); // "TechCorp"
console.log(cidade); // "São Paulo"
console.log(primeiroFuncionario); // { nome: "Ana", cargo: "Dev" }
```

### Desestruturação em Parâmetros de Função

```javascript
// Função que recebe um objeto como parâmetro
function criarPerfil({ nome, idade, email, cidade = "Não informado" }) {
    return `${nome}, ${idade} anos, ${email}, mora em ${cidade}`;
}

const usuario = {
    nome: "Laura",
    idade: 27,
    email: "laura@email.com"
};

console.log(criarPerfil(usuario));
// "Laura, 27 anos, laura@email.com, mora em Não informado"
```

## 🔄 Rest em Desestruturação

```javascript
const dados = {
    id: 1,
    nome: "Produto A",
    preco: 99.99,
    categoria: "Eletrônicos",
    descricao: "Um ótimo produto",
    disponivel: true
};

// Extraindo algumas propriedades e agrupando o resto
const { id, nome, ...outrasPropriedades } = dados;

console.log(id); // 1
console.log(nome); // "Produto A"
console.log(outrasPropriedades);
// { preco: 99.99, categoria: "Eletrônicos", descricao: "Um ótimo produto", disponivel: true }
```

## 🛠️ Métodos Úteis para Objetos

### Object.keys(), Object.values(), Object.entries()

```javascript
const produto = {
    nome: "Notebook",
    preco: 2500,
    marca: "TechBrand"
};

// Obtendo as chaves
console.log(Object.keys(produto)); // ["nome", "preco", "marca"]

// Obtendo os valores
console.log(Object.values(produto)); // ["Notebook", 2500, "TechBrand"]

// Obtendo pares chave-valor
console.log(Object.entries(produto));
// [["nome", "Notebook"], ["preco", 2500], ["marca", "TechBrand"]]
```

### Object.assign() e Spread Operator

```javascript
const base = { a: 1, b: 2 };
const extensao = { c: 3, d: 4 };

// Usando Object.assign()
const combinado1 = Object.assign({}, base, extensao);

// Usando spread operator (mais moderno)
const combinado2 = { ...base, ...extensao };

console.log(combinado2); // { a: 1, b: 2, c: 3, d: 4 }
```

## 📌 Exemplos Práticos

### Sistema de Usuário

```javascript
// Função para criar usuário com short syntax
function criarUsuario(nome, email, idade) {
    return {
        nome,
        email,
        idade,
        ativo: true,
        criadoEm: new Date(),
        
        // Method shorthand
        saudar() {
            return `Olá, eu sou ${this.nome}!`;
        },
        
        desativar() {
            this.ativo = false;
        }
    };
}

// Usando desestruturação para extrair dados
function exibirInfoUsuario(usuario) {
    const { nome, email, idade, ativo } = usuario;
    
    return {
        resumo: `${nome} (${email})`,
        status: ativo ? "Ativo" : "Inativo",
        categoria: idade >= 18 ? "Adulto" : "Menor"
    };
}

const usuario = criarUsuario("Pedro", "pedro@email.com", 25);
console.log(exibirInfoUsuario(usuario));
```

### Configuração de API

```javascript
// Configuração com valores padrão usando desestruturação
function configurarAPI({
    baseURL = "https://api.exemplo.com",
    timeout = 5000,
    headers = {},
    retries = 3
} = {}) {
    return {
        baseURL,
        timeout,
        headers: {
            "Content-Type": "application/json",
            ...headers
        },
        retries
    };
}

// Uso com configuração personalizada
const config = configurarAPI({
    baseURL: "https://minha-api.com",
    headers: {
        "Authorization": "Bearer token123"
    }
});

console.log(config);
```

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>