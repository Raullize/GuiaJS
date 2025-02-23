<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🚀 Node.js

## O que é Node.js?

**Node.js** é um ambiente de execução para JavaScript fora do navegador, construído no motor **V8** do Google Chrome. Ele permite que você execute código JavaScript no lado do servidor, tornando-o ideal para criar aplicações escaláveis e de alta performance.

---

## 🛠️ Para que serve o Node.js?

O Node.js é amplamente utilizado para:

- **Criar servidores e APIs**: Desenvolver backends para aplicações web e móveis.
- **Executar JavaScript no servidor**: Executar scripts e aplicações sem depender de um navegador.
- **Desenvolver aplicações em tempo real**: Como chats, jogos online e ferramentas de colaboração.
- **Automatizar tarefas**: Criar scripts para build, deploy e outras tarefas de desenvolvimento.

---

## 📥 Como instalar o Node.js?

Para instalar o Node.js, siga os passos abaixo:

1. Acesse o site oficial: [nodejs.org](https://nodejs.org).
2. Baixe a versão **recomendada** (LTS - Long Term Support) para maior estabilidade.
3. Siga o assistente de instalação no seu sistema operacional (Windows, macOS ou Linux).

Após a instalação, verifique se o Node.js e o **npm** (Node Package Manager) foram instalados corretamente executando os seguintes comandos no terminal:

```bash
node -v
npm -v
```

Isso exibirá as versões instaladas do Node.js e do npm.

---

## 🚀 Primeiros passos com Node.js

### Criando um servidor simples

Aqui está um exemplo básico de como criar um servidor HTTP com Node.js:

```bash
// Importando o módulo 'http'
const http = require('http');

// Criando o servidor
const server = http.createServer((req, res) => {
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('Olá, mundo!');
});

// Escutando na porta 3000
server.listen(3000, () => {
    console.log('Servidor rodando em http://localhost:3000');
});
```

- Salve o código em um arquivo, por exemplo, `server.js`.
- Execute o servidor com o comando: `node server.js`.
- Acesse `http://localhost:3000` no navegador para ver a mensagem "Olá, mundo!".

---

## 📦 Gerenciando pacotes com npm

O **npm** é o gerenciador de pacotes do Node.js e permite instalar bibliotecas e frameworks de terceiros. Aqui estão alguns comandos úteis:

- **Instalar um pacote**:
  ```bash
  npm install nome-do-pacote
  ```

- **Instalar um pacote globalmente**:
  ```bash
  npm install -g nome-do-pacote
  ```

- **Criar um arquivo `package.json`**:
  ```bash
  npm init
  ```

- **Instalar dependências de um projeto**:
  ```bash
  npm install
  ```

---

## 🌟 Frameworks populares no ecossistema Node.js

- **Express.js**: Um framework minimalista para criar servidores e APIs.
- **NestJS**: Um framework robusto e escalável, inspirado no Angular.
- **Socket.IO**: Para aplicações em tempo real.
- **Next.js**: Para renderização de aplicações React no servidor.

---

## 🖼️ Logo do Node.js

Aqui está a logo oficial do Node.js:

![Node.js Logo](https://nodejs.org/static/images/logo.svg)

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>