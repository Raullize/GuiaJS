<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🏗️ Estruturação de Projetos JavaScript

Um guia completo para estruturar seus projetos JavaScript de forma profissional e escalável.

## 📦 Gerenciamento de Pacotes

O gerenciamento de pacotes é fundamental para qualquer projeto JavaScript moderno. O `package.json` serve como um manifesto do seu projeto, contendo todas as informações necessárias para sua configuração e execução.

### Importância do package.json

O arquivo `package.json` é essencial porque:
- Define as dependências do projeto
- Especifica scripts para automatização
- Contém metadados importantes
- Permite controle de versão das dependências
- Facilita a replicação do ambiente de desenvolvimento

### Estrutura Básica do package.json

```json
{
  "name": "meu-projeto",
  "version": "1.0.0",
  "description": "Descrição do projeto",
  "main": "src/index.js",
  "scripts": {
    "start": "node src/index.js",
    "dev": "nodemon src/index.js",
    "test": "jest",
    "lint": "eslint .",
    "format": "prettier --write ."
  },
  "dependencies": {
    "express": "^4.18.2"
  },
  "devDependencies": {
    "eslint": "^8.0.0",
    "prettier": "^3.0.0",
    "jest": "^29.0.0"
  }
}
```

### Versionamento Semântico

O versionamento semântico (SemVer) é crucial para o gerenciamento de dependências:
- **MAJOR**: Mudanças que quebram compatibilidade
- **MINOR**: Novas funcionalidades mantendo compatibilidade
- **PATCH**: Correções de bugs mantendo compatibilidade

Exemplo: `^4.18.2` significa:
- 4: Versão major
- 18: Versão minor
- 2: Versão patch
- ^: Permite atualizações de minor e patch

## 🔍 Linting e Formatação

A consistência do código é vital para a manutenibilidade e legibilidade. Linting e formatação automatizada ajudam a manter padrões de código consistentes em toda a equipe.

### Por que usar ESLint?

O ESLint é essencial porque:
- Identifica erros potenciais
- Enforce padrões de código
- Melhora a qualidade do código
- Facilita a revisão de código
- Reduz bugs e problemas de manutenção

### Configuração do ESLint

```bash
# Instalação
npm install -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin

# Configuração (.eslintrc.js)
module.exports = {
  env: {
    node: true,
    es2021: true
  },
  extends: [
    'eslint:recommended',
    'plugin:@typescript-eslint/recommended'
  ],
  parser: '@typescript-eslint/parser',
  plugins: ['@typescript-eslint'],
  rules: {
    'no-console': 'warn',
    'semi': ['error', 'always']
  }
};
```

### Integração com Prettier

O Prettier complementa o ESLint focando na formatação do código:
- Formatação consistente
- Elimina debates sobre estilo
- Integração com editores
- Configuração mínima

## 🔗 Git Hooks

Git Hooks são scripts que automatizam tarefas durante o ciclo de vida do Git. Eles são cruciais para garantir a qualidade do código antes de ser commitado.

### Benefícios dos Git Hooks

- Prevenção de código quebrado
- Execução automática de testes
- Verificação de padrões de código
- Validação de mensagens de commit
- Integração com ferramentas de CI/CD

### Configuração com Husky

```bash
# Instalação
npm install -D husky lint-staged

# Configuração (package.json)
{
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "*.{js,ts}": [
      "eslint --fix",
      "prettier --write"
    ]
  }
}
```

## 🔒 Variáveis de Ambiente

As variáveis de ambiente são fundamentais para a configuração segura e flexível de aplicações.

### Boas Práticas

- Nunca versionar arquivos .env
- Usar diferentes arquivos por ambiente
- Validar variáveis obrigatórias
- Documentar variáveis necessárias
- Usar valores padrão quando apropriado

### Configuração com dotenv

```bash
# Instalação
npm install dotenv

# Configuração (.env)
DATABASE_URL=mongodb://localhost:27017/meu-banco
PORT=3000
NODE_ENV=development

# Uso no código
require('dotenv').config();
const port = process.env.PORT;
```

## 🏛️ Arquitetura Limpa

A Clean Architecture promove a separação de responsabilidades e a independência entre camadas.

### Princípios Fundamentais

1. **Independência de Frameworks**
   - Não depender de bibliotecas específicas
   - Facilita migrações e atualizações

2. **Testabilidade**
   - Código fácil de testar
   - Dependências injetáveis

3. **Independência de UI**
   - Interface pode mudar sem afetar regras de negócio
   - Suporte a diferentes interfaces

4. **Independência de Banco de Dados**
   - Troca de banco sem afetar regras
   - Persistência como detalhe

### Estrutura de Diretórios

```
src/
├── application/    # Casos de uso e regras de negócio
├── domain/         # Entidades e interfaces
├── infrastructure/ # Implementações concretas
├── presentation/   # Controllers e rotas
└── main/          # Configuração e inicialização
```

## 📝 Documentação

Documentação clara e atualizada é crucial para a manutenibilidade do projeto.

### Tipos de Documentação

1. **Documentação de Código**
   - JSDoc para funções e classes
   - Comentários explicativos
   - Exemplos de uso

2. **Documentação de API**
   - Endpoints e parâmetros
   - Exemplos de requisições
   - Respostas esperadas

3. **Documentação de Arquitetura**
   - Diagramas de componentes
   - Fluxos de dados
   - Decisões arquiteturais

### Exemplo de JSDoc

```javascript
/**
 * Classe que representa um usuário do sistema
 * @class
 */
class User {
  /**
   * Cria uma nova instância de User
   * @param {string} name - Nome do usuário
   * @param {string} email - Email do usuário
   */
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }
}
```

## 🐳 Docker

Docker permite empacotar aplicações com todas as suas dependências em containers isolados.

### Benefícios do Docker

- Ambiente consistente
- Fácil replicação
- Isolamento de dependências
- Escalabilidade
- Integração com CI/CD

### Configuração de Ambiente

```dockerfile
# Desenvolvimento
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
CMD ["npm", "run", "dev"]

# Produção
FROM node:18-alpine as builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM node:18-alpine
WORKDIR /app
COPY --from=builder /app/dist ./dist
COPY package*.json ./
RUN npm install --production
CMD ["npm", "start"]
```

## 🌱 Seeds e Migrations

Seeds e migrations são essenciais para manter a consistência do banco de dados entre ambientes.

### Boas Práticas

1. **Migrations**
   - Versionamento de esquema
   - Reversibilidade
   - Testes de integração
   - Documentação clara

2. **Seeds**
   - Dados de teste realistas
   - Dados essenciais
   - Ambiente específico
   - Performance

### Exemplo de Seed

```javascript
// seeds/users.js
const User = require('../src/domain/entities/User');

async function seedUsers() {
  const users = [
    new User('Admin', 'admin@example.com'),
    new User('User', 'user@example.com')
  ];

  for (const user of users) {
    await userRepository.save(user);
  }
}
```

---

> 💡 **Dica**: Mantenha sua estrutura de projeto organizada desde o início. Isso facilitará a manutenção e escalabilidade do seu código.

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/> 