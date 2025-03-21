<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🌐 Client Side vs Server Side

## 💻 JavaScript no Cliente (Client Side)
O JavaScript foi inicialmente criado para ser executado no lado do cliente (navegador). Neste contexto, ele:

- Manipula o DOM (Document Object Model)
- Responde a interações do usuário
- Cria efeitos visuais e animações
- Valida formulários antes do envio
- Realiza requisições assíncronas (AJAX)

```js
// Exemplo de JS no lado do cliente
document.getElementById("meuBotao").addEventListener("click", function() {
    alert("Botão clicado!");
});
```

## 🖥️ JavaScript no Servidor (Server Side)
Com o surgimento do Node.js, o JavaScript passou a ser executado também no lado do servidor:

- Manipula arquivos do sistema
- Conecta-se a bancos de dados
- Processa requisições HTTP
- Cria APIs RESTful
- Executa tarefas em background

```js
// Exemplo de JS no lado do servidor (Node.js)
const http = require('http');

http.createServer((req, res) => {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World\n');
}).listen(3000);
```

## 🧐 Principais Diferenças

| Característica | Client Side | Server Side |
|----------------|-------------|-------------|
| Ambiente | Navegador | Node.js ou similar |
| Acesso | DOM, cookies, localStorage | Sistema de arquivos, banco de dados |
| Segurança | Código visível ao usuário | Código protegido no servidor |
| Performance | Limitado aos recursos do dispositivo | Escalável conforme hardware |

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/> 