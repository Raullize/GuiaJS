<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 📄 Como criar e usar um arquivo JavaScript 

Para adicionar um arquivo JavaScript ao seu projeto, siga estes passos:

1. Crie um arquivo com a extensão `.js`, por exemplo, `app.js`.
2. Adicione o script ao seu arquivo HTML utilizando a tag `<script>`.

Exemplo básico:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GuiaJS</title>
</head>
<body>
    <h1>Olá, JavaScript!</h1>
    <script src="app.js" defer></script>
</body>
</html>
```

## Sobre o atributo `defer` ⏳
- O atributo `defer` garante que o arquivo JavaScript será carregado em segundo plano e executado apenas após o carregamento completo do HTML.
- Isso melhora o desempenho da página e evita problemas de acesso a elementos DOM que ainda não foram renderizados.

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>