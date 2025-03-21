<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🎯 Programação Orientada a Objetos em JavaScript

JavaScript é uma linguagem multi-paradigma que suporta programação orientada a objetos (POO), embora sua implementação tenha características únicas baseadas em protótipos, diferente das linguagens baseadas em classes tradicionais.

## 🧩 Fundamentos da POO em JavaScript

### Objetos

Em JavaScript, objetos são coleções de pares chave-valor, onde os valores podem ser propriedades ou métodos.

```js
// Criando um objeto literal
const pessoa = {
  nome: "Ana",
  idade: 28,
  saudar() {
    return `Olá, meu nome é ${this.nome}`;
  }
};

console.log(pessoa.saudar()); // "Olá, meu nome é Ana"
```

### Classes em JavaScript (ES6+)

Introduzidas no ES6, as classes são uma sintaxe mais familiar para desenvolvedores de outras linguagens orientadas a objetos.

```js
class Pessoa {
  constructor(nome, idade) {
    this.nome = nome;
    this.idade = idade;
  }
  
  saudar() {
    return `Olá, meu nome é ${this.nome}`;
  }
  
  static criarPessoaAnônima() {
    return new Pessoa("Anônimo", 0);
  }
}

const pessoa1 = new Pessoa("João", 30);
console.log(pessoa1.saudar()); // "Olá, meu nome é João"

const anônimo = Pessoa.criarPessoaAnônima();
console.log(anônimo.nome); // "Anônimo"
```

## 🌟 Pilares da POO em JavaScript

### 1. Encapsulamento

Limita o acesso direto aos dados de um objeto, protegendo o estado interno.

```js
// Usando closures para encapsulamento
function criarConta(saldoInicial) {
  let saldo = saldoInicial;
  
  return {
    depositar(valor) {
      saldo += valor;
      return saldo;
    },
    sacar(valor) {
      if (valor > saldo) {
        throw new Error("Saldo insuficiente");
      }
      saldo -= valor;
      return saldo;
    },
    verSaldo() {
      return saldo;
    }
  };
}

const minhaConta = criarConta(1000);
console.log(minhaConta.verSaldo()); // 1000
minhaConta.depositar(500);
console.log(minhaConta.verSaldo()); // 1500
// Não é possível acessar `saldo` diretamente
```

#### Propriedades Privadas (ES2022)

```js
class ContaBancaria {
  #saldo; // Propriedade privada (suporte moderno)
  
  constructor(saldoInicial) {
    this.#saldo = saldoInicial;
  }
  
  depositar(valor) {
    this.#saldo += valor;
    return this.#saldo;
  }
  
  get saldo() {
    return this.#saldo;
  }
}

const conta = new ContaBancaria(1000);
console.log(conta.saldo); // 1000
// console.log(conta.#saldo); // Erro: propriedade privada
```

### 2. Herança

Permite que uma classe herde propriedades e métodos de outra classe.

```js
class Animal {
  constructor(nome) {
    this.nome = nome;
  }
  
  emitirSom() {
    return "Som genérico";
  }
}

class Cachorro extends Animal {
  constructor(nome, raça) {
    super(nome); // Chama o construtor da classe pai
    this.raça = raça;
  }
  
  emitirSom() {
    return "Au au!";
  }
  
  abanarRabo() {
    return `${this.nome} está abanando o rabo!`;
  }
}

const rex = new Cachorro("Rex", "Pastor Alemão");
console.log(rex.nome); // "Rex"
console.log(rex.emitirSom()); // "Au au!"
console.log(rex.abanarRabo()); // "Rex está abanando o rabo!"
```

### 3. Polimorfismo

Permite que objetos de diferentes classes sejam tratados como objetos de uma classe comum.

```js
class Forma {
  calcularArea() {
    return 0;
  }
}

class Retangulo extends Forma {
  constructor(largura, altura) {
    super();
    this.largura = largura;
    this.altura = altura;
  }
  
  calcularArea() {
    return this.largura * this.altura;
  }
}

class Circulo extends Forma {
  constructor(raio) {
    super();
    this.raio = raio;
  }
  
  calcularArea() {
    return Math.PI * this.raio * this.raio;
  }
}

function mostrarArea(forma) {
  console.log(`Área: ${forma.calcularArea()}`);
}

mostrarArea(new Retangulo(5, 10)); // "Área: 50"
mostrarArea(new Circulo(5));       // "Área: 78.53981633974483"
```

### 4. Abstração

Simplifica conceitos complexos isolando o que é importante para o objeto.

```js
class DispositivoEletronico {
  constructor(nome) {
    this.nome = nome;
    this.ligado = false;
  }
  
  ligar() {
    this.ligado = true;
  }
  
  desligar() {
    this.ligado = false;
  }
}

class Smartphone extends DispositivoEletronico {
  constructor(nome, marca, modelo) {
    super(nome);
    this.marca = marca;
    this.modelo = modelo;
  }
  
  fazerLigacao(numero) {
    if (this.ligado) {
      console.log(`Ligando para ${numero}`);
    } else {
      console.log("Impossível fazer ligação, telefone desligado");
    }
  }
}

const meuTelefone = new Smartphone("Meu Telefone", "Samsung", "Galaxy S21");
meuTelefone.ligar();
meuTelefone.fazerLigacao("123456789");
```

## 🔄 Herança Prototipal

JavaScript originalmente implementa herança através de protótipos, não classes.

```js
// Função construtora
function Pessoa(nome) {
  this.nome = nome;
}

// Adicionando método ao protótipo
Pessoa.prototype.saudar = function() {
  return `Olá, meu nome é ${this.nome}`;
};

// Herança prototipal
function Funcionario(nome, cargo) {
  Pessoa.call(this, nome); // "super()"
  this.cargo = cargo;
}

// Conectando protótipos
Funcionario.prototype = Object.create(Pessoa.prototype);
Funcionario.prototype.constructor = Funcionario;

// Adicionando método ao protótipo do Funcionario
Funcionario.prototype.apresentar = function() {
  return `${this.saudar()}. Sou ${this.cargo}.`;
};

const funcionario = new Funcionario("Carlos", "Desenvolvedor");
console.log(funcionario.apresentar()); // "Olá, meu nome é Carlos. Sou Desenvolvedor."
```

## 🧹 Garbage Collection

JavaScript gerencia a memória automaticamente através do Garbage Collector, que libera a memória de objetos que não são mais referenciados.

```js
// Objeto acessível
let objeto = { data: "alguma informação" };

// Objeto não é mais acessível (candidato para garbage collection)
objeto = null;
```

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/> 