<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=180&section=header&text=GuiaJS&fontSize=30&fontColor=fff&animation=twinkling&fontAlignY=35"/>

# 📘 GuiaJS

Bem-vindo ao **GuiaJS**, um recurso prático e abrangente para aprender JavaScript, desde conceitos básicos até tópicos mais avançados. Este guia é perfeito para iniciantes e intermediários que desejam aprender ou revisar os fundamentos dessa poderosa linguagem de programação.

## 📚 Conteúdo

1. [🤔 O que é JavaScript?](#javascript-intro)
2. [🏹 Os Três Mosqueteiros da Web](contents/os-tres-mosqueteiros.md)
3. [🌐 Client Side vs Server Side](contents/client-vs-server.md)
4. [🖥️ Console do Navegador](contents/console-navegador.md)
5. [💻 Escolhendo uma IDE](contents/ide.md)
6. [🚀 Node.js](contents/nodejs.md)
7. [📄 Como criar e usar um arquivo JavaScript](contents/arquivos-js.md)
8. [📝 Comentários](contents/comentarios.md)
9. [⚠️ ASI (Automatic Semicolon Insertion)](contents/asi.md)
10. [📊 Tipos de Dados](contents/tipos-dados.md)
11. [🧩 Tipos Primitivos vs Tipos de Referência](contents/tipos-primitivos-referencia.md)
12. [🔄 Tipagem Dinâmica em JavaScript](contents/tipagem-dinamica.md)
13. [🔢 Variáveis: var, let, const](contents/variaveis.md)
14. [🔄 Hoisting em JavaScript](contents/hoisting.md)
15. [➗ Operadores Aritméticos](contents/operadores.md)
16. [🔄 Incremento e Decremento](contents/incremento-decremento.md)
17. [📝 Operadores de Atribuição](contents/operadores-atribuicao.md)
18. [🔍 Operadores de Comparação](contents/operadores-comparacao.md)
19. [🔀 Operadores Ternários](contents/operadores-ternarios.md)
20. [📝 Operadores Lógicos com Strings](contents/operadores-logicos-strings.md)
21. [📊 Precedência de Operadores](contents/precedencia-operadores.md)
22. [📝 Manipulação de Strings](contents/strings-concatenacao.md)
23. [🔀 Estruturas Condicionais](contents/condicionais.md)
24. [♻️ Estruturas de Repetição](contents/repeticao.md)
25. [🔄 Loops Específicos em JavaScript](contents/loops-especificos.md)
26. [🔢 Arrays e Arrays Bidimensionais](contents/arrays.md)
27. [🔢 Métodos de Arrays](contents/metodos-arrays.md)
28. [🔧 Objetos](contents/objetos.md)
29. [🎯 Programação Orientada a Objetos](contents/poo.md)
30. [🔢 Funções](contents/funcoes.md)
31. [🔢 Tipos de Funções](contents/tipos-funcoes.md)
32. [🌐 Objetos Globais](contents/objetos-globais.md)
33. [✨ Clean Code em JavaScript](contents/clean-code.md)

---

<h2 id="javascript-intro">🤔 O que é JavaScript?</h2> 

JavaScript é uma linguagem de programação dinâmica, versátil e de alto nível. Criada em 1995, é interpretada pelo navegador e executa do lado do cliente (client-side), permitindo manipular elementos da página em tempo real sem necessidade de recarregamento.

Características principais:
- 🔄 **Dinâmica**: Tipagem flexível e adaptável
- 🌐 **Multiplataforma**: Funciona em todos os navegadores modernos
- 🏗️ **Baseada em protótipos**: Sistema de herança diferente das linguagens tradicionais baseadas em classes
- ⚡ **Execução assíncrona**: Permite operações sem bloquear a interface do usuário

Atualmente, o JavaScript vai muito além dos navegadores, sendo utilizado para:
- 📱 Desenvolvimento de aplicativos móveis (React Native, Ionic)
- 🖥️ Aplicações desktop (Electron)
- 🔙 Servidores e APIs (Node.js, Express, Deno)
- 🤖 Internet das Coisas (IoT) e dispositivos embarcados

É uma linguagem essencial para o desenvolvimento web moderno e uma excelente primeira linguagem para quem está iniciando na programação.

---

<h2 id="clean-code">✨ Clean Code em JavaScript</h2>

Clean Code (Código Limpo) refere-se a um conjunto de práticas que tornam seu código mais legível, manutenível e menos propenso a erros. Baseado nos princípios do livro "Clean Code" de Robert C. Martin, adaptados para JavaScript.

Princípios fundamentais:

- 🔤 **Nomenclatura Clara**: Use nomes que revelem a intenção
  ```javascript
  // Ruim
  const d = new Date() - 86400000;
  
  // Bom
  const MILLISECONDS_IN_A_DAY = 86400000;
  const yesterday = new Date(Date.now() - MILLISECONDS_IN_A_DAY);
  ```

- 🧩 **Funções Pequenas e Focadas**: Cada função deve fazer apenas uma coisa
  ```javascript
  // Ruim
  function getAndSaveUserData(id) {
    const user = fetch(`/users/${id}`);
    localStorage.setItem('user', JSON.stringify(user));
    return user;
  }
  
  // Bom
  function getUser(id) {
    return fetch(`/users/${id}`);
  }
  
  function saveUser(user) {
    localStorage.setItem('user', JSON.stringify(user));
  }
  ```

- 🧪 **Evite Efeitos Colaterais**: Funções não devem modificar valores externos inesperadamente
  ```javascript
  // Ruim - modifica o array original
  function addItem(cart, item) {
    cart.push(item);
    return cart;
  }
  
  // Bom - retorna um novo array sem modificar o original
  function addItem(cart, item) {
    return [...cart, item];
  }
  ```

- 🔍 **DRY (Don't Repeat Yourself)**: Evite código duplicado
  ```javascript
  // Ruim - lógica repetida
  function validateEmail(email) {
    const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return regex.test(email);
  }
  
  function isValidEmail(email) {
    const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return regex.test(email);
  }
  
  // Bom
  function validateEmail(email) {
    const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return regex.test(email);
  }
  ```

- 🧠 **Prefira Programação Funcional**: Use métodos funcionais para arrays
  ```javascript
  // Ruim
  const total = 0;
  for (let i = 0; i < orders.length; i++) {
    total += orders[i].price;
  }
  
  // Bom
  const total = orders.reduce((sum, order) => sum + order.price, 0);
  ```

- 🛡️ **Tratamento de Erros Adequado**: Capture e trate exceções corretamente
  ```javascript
  // Ruim
  try {
    riskyOperation();
  } catch (error) {
    console.log(error);
  }
  
  // Bom
  try {
    riskyOperation();
  } catch (error) {
    logError(error);
    notifyUser(error);
  }
  ```

- 📏 **SOLID**: Princípios de design orientado a objetos
  - **S**ingle Responsibility: Uma classe deve ter apenas um motivo para mudar
  - **O**pen/Closed: Aberto para extensão, fechado para modificação
  - **L**iskov Substitution: Subtipos devem ser substituíveis por seus tipos base
  - **I**nterface Segregation: Interfaces específicas são melhores que uma geral
  - **D**ependency Inversion: Dependa de abstrações, não de implementações

Código limpo não é apenas sobre fazer o código funcionar, mas fazê-lo de forma que outros desenvolvedores (incluindo você no futuro) possam facilmente entendê-lo e mantê-lo.

---

## 🌐 Recursos Adicionais
- [MDN Web Docs: JavaScript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
- [W3Schools: JavaScript](https://www.w3schools.com/js/)
- [JavaScript.info](https://javascript.info)
- [Clean Code JavaScript](https://github.com/ryanmcdermott/clean-code-javascript)

---

Esperamos que este guia tenha sido útil para você! 😄 Continuaremos expandindo com mais dicas e exemplos.

🎯 **Contribuições são bem-vindas!** Caso queira adicionar algo, faça um pull request no repositório.

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>
