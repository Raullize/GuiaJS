<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# Clean Code em JavaScript

Clean Code (Código Limpo) é um conjunto de práticas e princípios que visam tornar seu código mais legível, manutenível e menos propenso a erros. Estas práticas foram popularizadas por Robert C. Martin em seu livro "Clean Code" e adaptadas para diversas linguagens, incluindo JavaScript.

## Por que código limpo é importante?

Um código bem escrito:
- É mais fácil de entender e manter
- Reduz o tempo de depuração
- Facilita a colaboração entre desenvolvedores
- Diminui o custo de manutenção a longo prazo
- Melhora a qualidade do software como um todo

## Princípios Fundamentais

### 1. Nomenclatura Clara e Significativa

Os nomes de variáveis, funções e classes devem revelar claramente sua intenção e responsabilidade.

**Ruim:**
```javascript
const us = ['Brasil', 'Argentina', 'Chile'];
const yyyymmdstr = moment().format('YYYY/MM/DD');
function sv(d) { localStorage.setItem('dt', d); }
```

**Bom:**
```javascript
const southAmericanCountries = ['Brasil', 'Argentina', 'Chile'];
const currentDate = moment().format('YYYY/MM/DD');
function saveDocument(document) { localStorage.setItem('document', document); }
```

### 2. Funções Pequenas e Focadas

Cada função deve ter uma única responsabilidade e fazer apenas uma coisa.

**Ruim:**
```javascript
function emailClients(clients) {
  clients.forEach(client => {
    const clientRecord = database.lookup(client);
    if (clientRecord.isActive()) {
      email(client);
    }
  });
}
```

**Bom:**
```javascript
function emailActiveClients(clients) {
  const activeClients = filterActiveClients(clients);
  activeClients.forEach(client => email(client));
}

function filterActiveClients(clients) {
  return clients.filter(client => isActiveClient(client));
}

function isActiveClient(client) {
  const clientRecord = database.lookup(client);
  return clientRecord.isActive();
}
```

### 3. Evite Efeitos Colaterais

Funções não devem modificar valores externos inesperadamente.

**Ruim:**
```javascript
let name = 'Ryan McDermott';

function splitIntoFirstAndLastName() {
  name = name.split(' ');
}

splitIntoFirstAndLastName();
console.log(name); // ['Ryan', 'McDermott']
```

**Bom:**
```javascript
function splitIntoFirstAndLastName(name) {
  return name.split(' ');
}

const name = 'Ryan McDermott';
const newName = splitIntoFirstAndLastName(name);

console.log(name); // 'Ryan McDermott'
console.log(newName); // ['Ryan', 'McDermott']
```

### 4. DRY (Don't Repeat Yourself)

Evite duplicação de código. Abstraia funcionalidades comuns em funções reutilizáveis.

**Ruim:**
```javascript
function showDeveloperList(developers) {
  developers.forEach(developer => {
    const expectedSalary = developer.calculateExpectedSalary();
    const experience = developer.getExperience();
    const githubLink = developer.getGithubLink();
    
    const data = {
      expectedSalary,
      experience,
      githubLink
    };
    
    render(data);
  });
}

function showManagerList(managers) {
  managers.forEach(manager => {
    const expectedSalary = manager.calculateExpectedSalary();
    const experience = manager.getExperience();
    const portfolio = manager.getMBAProjects();
    
    const data = {
      expectedSalary,
      experience,
      portfolio
    };
    
    render(data);
  });
}
```

**Bom:**
```javascript
function showEmployeeList(employees) {
  employees.forEach(employee => {
    const commonData = {
      expectedSalary: employee.calculateExpectedSalary(),
      experience: employee.getExperience()
    };
    
    const data = {
      ...commonData,
      ...(employee.type === 'developer' 
          ? { githubLink: employee.getGithubLink() }
          : { portfolio: employee.getMBAProjects() })
    };
    
    render(data);
  });
}
```

### 5. Prefira Programação Funcional

Métodos funcionais como `map`, `filter`, `reduce` são mais declarativos e legíveis do que loops imperativos.

**Ruim:**
```javascript
const programmerOutput = [
  { name: 'Uncle Bobby', linesOfCode: 500 },
  { name: 'Suzie Q', linesOfCode: 1500 },
  { name: 'Jimmy Gosling', linesOfCode: 150 },
  { name: 'Gracie Hopper', linesOfCode: 1000 }
];

let totalOutput = 0;
for (let i = 0; i < programmerOutput.length; i++) {
  totalOutput += programmerOutput[i].linesOfCode;
}
```

**Bom:**
```javascript
const programmerOutput = [
  { name: 'Uncle Bobby', linesOfCode: 500 },
  { name: 'Suzie Q', linesOfCode: 1500 },
  { name: 'Jimmy Gosling', linesOfCode: 150 },
  { name: 'Gracie Hopper', linesOfCode: 1000 }
];

const totalOutput = programmerOutput
  .map(programmer => programmer.linesOfCode)
  .reduce((total, lines) => total + lines, 0);
```

### 6. Tratamento de Erros Adequado

Nunca ignore erros capturados. Trate-os apropriadamente.

**Ruim:**
```javascript
try {
  functionThatMightThrow();
} catch (error) {
  console.log(error);
}
```

**Bom:**
```javascript
try {
  functionThatMightThrow();
} catch (error) {
  console.error(error);
  notifyUserOfError(error);
  reportErrorToService(error);
}
```

### 7. Princípios SOLID

Os princípios SOLID são fundamentais para o design orientado a objetos:

#### S - Single Responsibility Principle (Princípio da Responsabilidade Única)

Uma classe deve ter apenas um motivo para mudar.

**Ruim:**
```javascript
class UserSettings {
  constructor(user) {
    this.user = user;
  }
  
  changeSettings(settings) {
    if (this.verifyCredentials()) {
      // Muda as configurações
    }
  }
  
  verifyCredentials() {
    // Verifica as credenciais
  }
}
```

**Bom:**
```javascript
class UserAuth {
  constructor(user) {
    this.user = user;
  }
  
  verifyCredentials() {
    // Verifica as credenciais
  }
}

class UserSettings {
  constructor(user) {
    this.user = user;
    this.auth = new UserAuth(user);
  }
  
  changeSettings(settings) {
    if (this.auth.verifyCredentials()) {
      // Muda as configurações
    }
  }
}
```

#### O - Open/Closed Principle (Princípio Aberto/Fechado)

Entidades de software devem ser abertas para extensão, mas fechadas para modificação.

**Ruim:**
```javascript
class HttpRequester {
  constructor(adapter) {
    this.adapter = adapter;
  }
  
  fetch(url) {
    if (this.adapter.name === 'ajax') {
      return makeAjaxCall(url);
    } else if (this.adapter.name === 'http') {
      return makeHttpCall(url);
    }
  }
}
```

**Bom:**
```javascript
class HttpRequester {
  constructor(adapter) {
    this.adapter = adapter;
  }
  
  fetch(url) {
    return this.adapter.request(url);
  }
}

class AjaxAdapter {
  request(url) {
    return makeAjaxCall(url);
  }
}

class HttpAdapter {
  request(url) {
    return makeHttpCall(url);
  }
}
```

#### L - Liskov Substitution Principle (Princípio da Substituição de Liskov)

Subtipos devem ser substituíveis por seus tipos base.

**Ruim:**
```javascript
class Rectangle {
  constructor() {
    this.width = 0;
    this.height = 0;
  }
  
  setWidth(width) {
    this.width = width;
  }
  
  setHeight(height) {
    this.height = height;
  }
  
  getArea() {
    return this.width * this.height;
  }
}

class Square extends Rectangle {
  setWidth(width) {
    this.width = width;
    this.height = width;
  }
  
  setHeight(height) {
    this.width = height;
    this.height = height;
  }
}
```

**Bom:**
```javascript
class Shape {
  getArea() {}
}

class Rectangle extends Shape {
  constructor(width, height) {
    super();
    this.width = width;
    this.height = height;
  }
  
  getArea() {
    return this.width * this.height;
  }
}

class Square extends Shape {
  constructor(length) {
    super();
    this.length = length;
  }
  
  getArea() {
    return this.length * this.length;
  }
}
```

#### I - Interface Segregation Principle (Princípio da Segregação de Interface)

Clientes não devem ser forçados a depender de interfaces que não utilizam.

**Ruim:**
```javascript
class DOMTraverser {
  constructor(settings) {
    this.settings = settings;
    this.setup();
  }
  
  setup() {
    this.rootNode = this.settings.rootNode;
    this.animationModule.setup();
  }
  
  traverse() {
    // ...
  }
}

const $ = new DOMTraverser({
  rootNode: document.getElementsByTagName('body'),
  animationModule: function() {} // Raramente precisamos disso
});
```

**Bom:**
```javascript
class DOMTraverser {
  constructor(settings) {
    this.settings = settings;
    this.options = settings.options;
    this.setup();
  }
  
  setup() {
    this.rootNode = this.settings.rootNode;
    if (this.options.animationModule) {
      this.options.animationModule.setup();
    }
  }
  
  traverse() {
    // ...
  }
}

const $ = new DOMTraverser({
  rootNode: document.getElementsByTagName('body'),
  options: {
    animationModule: null
  }
});
```

#### D - Dependency Inversion Principle (Princípio da Inversão de Dependência)

Módulos de alto nível não devem depender de módulos de baixo nível. Ambos devem depender de abstrações.

**Ruim:**
```javascript
class InventoryTracker {
  constructor(items) {
    this.items = items;
    this.requester = new InventoryRequester();
  }
  
  requestItems() {
    this.items.forEach(item => {
      this.requester.requestItem(item);
    });
  }
}

class InventoryRequester {
  constructor() {
    this.REQ_METHODS = ['HTTP'];
  }
  
  requestItem(item) {
    // ...
  }
}
```

**Bom:**
```javascript
class InventoryTracker {
  constructor(items, requester) {
    this.items = items;
    this.requester = requester;
  }
  
  requestItems() {
    this.items.forEach(item => {
      this.requester.requestItem(item);
    });
  }
}

class InventoryRequesterV1 {
  constructor() {
    this.REQ_METHODS = ['HTTP'];
  }
  
  requestItem(item) {
    // ...
  }
}

class InventoryRequesterV2 {
  constructor() {
    this.REQ_METHODS = ['WebSocket'];
  }
  
  requestItem(item) {
    // ...
  }
}

// Podemos mudar nossa implementação facilmente
const inventoryTracker = new InventoryTracker(
  ['apples', 'bananas'],
  new InventoryRequesterV2()
);
```

## Ferramentas e Recursos

Para ajudar a manter seu código limpo, considere usar:

- **Linters**: ESLint, JSLint
- **Formatadores**: Prettier
- **Análise estática**: SonarQube
- **Revisão de código**: Code reviews regulares

## Conclusão

Código limpo não é apenas sobre fazer o código funcionar, mas fazê-lo de uma forma que seja compreensível, manutenível e escalável. Ao seguir esses princípios, você não apenas se tornará um melhor desenvolvedor, mas também facilitará o trabalho de toda a equipe.

> "Qualquer tolo pode escrever código que um computador entenda. Bons programadores escrevem código que humanos conseguem entender." — Martin Fowler

## Recursos Adicionais

- [Clean Code JavaScript (GitHub)](https://github.com/ryanmcdermott/clean-code-javascript)
- [Livro: Clean Code de Robert C. Martin](https://www.amazon.com.br/C%C3%B3digo-Limpo-Habilidades-Pr%C3%A1ticas-Software/dp/8576082675)
- [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>