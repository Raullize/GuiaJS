<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 📦 ES Modules (ECMAScript Modules)

OS ES Modules são o sistema de módulos padrão do JavaScript moderno, introduzido no ES6 (ES2015). Eles permitem organizar código em arquivos separados e reutilizáveis.

## 🎯 Conceitos Fundamentais

### O que são Módulos?

Módulos são arquivos JavaScript que exportam funcionalidades (funções, classes, variáveis) para serem utilizadas em outros arquivos.

**Vantagens dos ES Modules:**
- ✅ Organização melhor do código
- ✅ Reutilização de funcionalidades
- ✅ Escopo isolado (evita poluição global)
- ✅ Carregamento assíncrono
- ✅ Tree shaking (eliminação de código não utilizado)

## 📤 Export (Exportação)

### Named Exports (Exportações Nomeadas)

Permite exportar múltiplas funcionalidades de um módulo:

```javascript
// utils.js
export const PI = 3.14159;

export function somar(a, b) {
    return a + b;
}

export function multiplicar(a, b) {
    return a * b;
}

export class Calculadora {
    constructor() {
        this.resultado = 0;
    }
    
    adicionar(valor) {
        this.resultado += valor;
        return this;
    }
    
    obterResultado() {
        return this.resultado;
    }
}

// Exportação em lote
const subtrair = (a, b) => a - b;
const dividir = (a, b) => a / b;

export { subtrair, dividir };
```

### Default Export (Exportação Padrão)

Cada módulo pode ter uma exportação padrão:

```javascript
// matematica.js
class Matematica {
    static somar(a, b) {
        return a + b;
    }
    
    static multiplicar(a, b) {
        return a * b;
    }
    
    static calcularArea(raio) {
        return Math.PI * raio * raio;
    }
}

// Exportação padrão
export default Matematica;
```

### Exportação Mista

Combinando named exports e default export:

```javascript
// config.js
export const API_URL = 'https://api.exemplo.com';
export const TIMEOUT = 5000;

const configuracaoPadrao = {
    url: API_URL,
    timeout: TIMEOUT,
    headers: {
        'Content-Type': 'application/json'
    }
};

export default configuracaoPadrao;
export { configuracaoPadrao as config };
```

## 📥 Import (Importação)

### Importando Named Exports

```javascript
// app.js
import { somar, multiplicar, PI, Calculadora } from './utils.js';

console.log(somar(5, 3)); // 8
console.log(PI); // 3.14159

const calc = new Calculadora();
console.log(calc.adicionar(10).adicionar(5).obterResultado()); // 15
```

### Importando Default Export

```javascript
// app.js
import Matematica from './matematica.js';

console.log(Matematica.somar(10, 20)); // 30
console.log(Matematica.calcularArea(5)); // 78.54
```

### Importação com Alias

Renomeando importações para evitar conflitos:

```javascript
// app.js
import { somar as somarNumeros, multiplicar as mult } from './utils.js';
import Matematica as Mat from './matematica.js';

console.log(somarNumeros(2, 3)); // 5
console.log(mult(4, 5)); // 20
console.log(Mat.somar(1, 1)); // 2
```

### Importação de Namespace

Importando todas as exportações nomeadas:

```javascript
// app.js
import * as Utils from './utils.js';
import configuracao from './config.js';

console.log(Utils.somar(1, 2)); // 3
console.log(Utils.PI); // 3.14159

const calc = new Utils.Calculadora();
console.log(calc.adicionar(5).obterResultado()); // 5
```

### Importação Mista

```javascript
// app.js
import configuracaoPadrao, { API_URL, TIMEOUT } from './config.js';

console.log(configuracaoPadrao.url); // 'https://api.exemplo.com'
console.log(API_URL); // 'https://api.exemplo.com'
console.log(TIMEOUT); // 5000
```

## 🔄 Re-exportação

Exportando funcionalidades de outros módulos:

```javascript
// index.js - Arquivo barrel
export { somar, multiplicar } from './utils.js';
export { default as Matematica } from './matematica.js';
export * from './constantes.js';

// Também pode re-exportar com alias
export { API_URL as URL_API } from './config.js';
```

## 🌐 Importação Dinâmica

Carregamento de módulos em tempo de execução:

```javascript
// Importação dinâmica com async/await
async function carregarModulo() {
    try {
        const { somar, multiplicar } = await import('./utils.js');
        console.log(somar(5, 3)); // 8
        
        const Matematica = await import('./matematica.js');
        console.log(Matematica.default.somar(2, 2)); // 4
    } catch (error) {
        console.error('Erro ao carregar módulo:', error);
    }
}

// Importação condicional
if (condicao) {
    import('./modulo-especial.js')
        .then(modulo => {
            modulo.funcaoEspecial();
        })
        .catch(error => {
            console.error('Erro:', error);
        });
}
```

## 🏗️ Estrutura de Projeto com Módulos

```
project/
├── src/
│   ├── components/
│   │   ├── Button.js
│   │   ├── Modal.js
│   │   └── index.js
│   ├── utils/
│   │   ├── api.js
│   │   ├── helpers.js
│   │   └── index.js
│   ├── config/
│   │   ├── database.js
│   │   ├── app.js
│   │   └── index.js
│   └── main.js
└── package.json
```

### Exemplo de Estrutura Modular

```javascript
// src/utils/api.js
export class ApiClient {
    constructor(baseURL) {
        this.baseURL = baseURL;
    }
    
    async get(endpoint) {
        const response = await fetch(`${this.baseURL}${endpoint}`);
        return response.json();
    }
    
    async post(endpoint, data) {
        const response = await fetch(`${this.baseURL}${endpoint}`, {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(data)
        });
        return response.json();
    }
}

export const api = new ApiClient('https://api.exemplo.com');
```

```javascript
// src/utils/helpers.js
export const formatarMoeda = (valor) => {
    return new Intl.NumberFormat('pt-BR', {
        style: 'currency',
        currency: 'BRL'
    }).format(valor);
};

export const formatarData = (data) => {
    return new Intl.DateTimeFormat('pt-BR').format(new Date(data));
};

export const validarEmail = (email) => {
    const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return regex.test(email);
};
```

```javascript
// src/utils/index.js (Barrel export)
export * from './api.js';
export * from './helpers.js';

// Ou exportações específicas
export { ApiClient, api } from './api.js';
export { formatarMoeda, formatarData, validarEmail } from './helpers.js';
```

```javascript
// src/main.js
import { api, formatarMoeda, validarEmail } from './utils/index.js';

async function iniciarApp() {
    // Validar email
    const emailValido = validarEmail('usuario@exemplo.com');
    console.log('Email válido:', emailValido);
    
    // Fazer requisição
    try {
        const dados = await api.get('/usuarios');
        console.log('Usuários:', dados);
    } catch (error) {
        console.error('Erro na API:', error);
    }
    
    // Formatar valor
    console.log(formatarMoeda(1234.56)); // R$ 1.234,56
}

iniciarApp();
```

## ⚙️ Configuração para ES Modules

### No Node.js

```json
// package.json
{
  "name": "meu-projeto",
  "version": "1.0.0",
  "type": "module",
  "main": "src/main.js",
  "scripts": {
    "start": "node src/main.js",
    "dev": "node --watch src/main.js"
  }
}
```

### No Browser

```html
<!DOCTYPE html>
<html>
<head>
    <title>ES Modules</title>
</head>
<body>
    <!-- Importante: type="module" -->
    <script type="module" src="./src/main.js"></script>
    
    <!-- Ou inline -->
    <script type="module">
        import { somar } from './utils.js';
        console.log(somar(2, 3));
    </script>
</body>
</html>
```

## 🔧 Boas Práticas

### 1. Organização de Arquivos

```javascript
// ✅ Bom: Um conceito por arquivo
// user.js
export class User {
    constructor(name, email) {
        this.name = name;
        this.email = email;
    }
}

// userService.js
export class UserService {
    static async createUser(userData) {
        // lógica de criação
    }
}
```

### 2. Barrel Exports

```javascript
// src/components/index.js
export { Button } from './Button.js';
export { Modal } from './Modal.js';
export { Card } from './Card.js';

// Uso mais limpo
import { Button, Modal, Card } from './components/index.js';
```

### 3. Evitar Importações Circulares

```javascript
// ❌ Evitar
// a.js
import { funcaoB } from './b.js';
export const funcaoA = () => funcaoB();

// b.js
import { funcaoA } from './a.js';
export const funcaoB = () => funcaoA();

// ✅ Melhor: Extrair para um terceiro módulo
// shared.js
export const funcaoCompartilhada = () => { /* lógica */ };
```

### 4. Nomes Descritivos

```javascript
// ✅ Bom
import { calcularImpostos } from './impostos.js';
import { validarCPF } from './validadores.js';

// ❌ Evitar
import { calc } from './utils.js';
import { validate } from './helpers.js';
```

## 📊 Comparação: ES Modules vs CommonJS

| Característica | ES Modules | CommonJS |
|---|---|---|
| **Sintaxe** | `import/export` | `require/module.exports` |
| **Carregamento** | Assíncrono | Síncrono |
| **Tree Shaking** | ✅ Suportado | ❌ Limitado |
| **Análise Estática** | ✅ Sim | ❌ Não |
| **Browser Nativo** | ✅ Sim | ❌ Não |
| **Node.js** | ✅ Sim (v12+) | ✅ Padrão |

## 🚀 Exemplo Prático: Sistema de Tarefas

```javascript
// models/Task.js
export class Task {
    constructor(id, title, completed = false) {
        this.id = id;
        this.title = title;
        this.completed = completed;
        this.createdAt = new Date();
    }
    
    toggle() {
        this.completed = !this.completed;
    }
    
    toJSON() {
        return {
            id: this.id,
            title: this.title,
            completed: this.completed,
            createdAt: this.createdAt
        };
    }
}
```

```javascript
// services/TaskService.js
import { Task } from '../models/Task.js';

export class TaskService {
    constructor() {
        this.tasks = [];
        this.nextId = 1;
    }
    
    addTask(title) {
        const task = new Task(this.nextId++, title);
        this.tasks.push(task);
        return task;
    }
    
    removeTask(id) {
        this.tasks = this.tasks.filter(task => task.id !== id);
    }
    
    toggleTask(id) {
        const task = this.tasks.find(task => task.id === id);
        if (task) {
            task.toggle();
        }
        return task;
    }
    
    getAllTasks() {
        return this.tasks;
    }
    
    getCompletedTasks() {
        return this.tasks.filter(task => task.completed);
    }
}

export const taskService = new TaskService();
```

```javascript
// app.js
import { taskService } from './services/TaskService.js';

// Adicionar tarefas
taskService.addTask('Estudar ES Modules');
taskService.addTask('Praticar JavaScript');
taskService.addTask('Fazer exercícios');

// Marcar uma como concluída
taskService.toggleTask(1);

// Exibir todas as tarefas
console.log('Todas as tarefas:');
taskService.getAllTasks().forEach(task => {
    console.log(`${task.id}. ${task.title} ${task.completed ? '✅' : '⏳'}`);
});

// Exibir apenas concluídas
console.log('\nTarefas concluídas:');
taskService.getCompletedTasks().forEach(task => {
    console.log(`${task.id}. ${task.title} ✅`);
});
```

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>