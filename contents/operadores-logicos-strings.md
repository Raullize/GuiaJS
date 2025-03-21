<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 📝 Operadores Lógicos com Strings

Em JavaScript, os operadores lógicos (`&&`, `||` e `!`) não se limitam a valores booleanos. Eles podem ser utilizados com strings e outros tipos de dados, seguindo regras específicas de avaliação.

## 🔀 Operador AND (`&&`)

O operador `&&` retorna o **primeiro valor falsy** encontrado ou o **último valor** se todos forem truthy.

```js
// Com strings
console.log("Olá" && "Mundo"); // "Mundo"
console.log("" && "Mundo");    // "" (string vazia é falsy)
console.log("Olá" && "");      // "" (string vazia é falsy)

// Com strings e outros tipos
console.log("Olá" && 0);       // 0 (número 0 é falsy)
console.log("Olá" && null);    // null (null é falsy)
console.log("Olá" && true);    // true (último valor, ambos são truthy)
```

## 🔀 Operador OR (`||`)

O operador `||` retorna o **primeiro valor truthy** encontrado ou o **último valor** se todos forem falsy.

```js
// Com strings
console.log("Olá" || "Mundo"); // "Olá" (primeiro valor truthy)
console.log("" || "Mundo");    // "Mundo" (segundo valor, pois o primeiro é falsy)
console.log("" || "");         // "" (todos são falsy, retorna o último)

// Uso comum: valores padrão
const nome = "" || "Usuário";  // Se nome for vazio, usa "Usuário"
console.log(nome);             // "Usuário"
```

## 🔀 Operador NOT (`!`)

O operador `!` converte o valor para booleano e nega seu valor.

```js
console.log(!"Olá");      // false (string não-vazia é truthy, negada vira false)
console.log(!"");         // true (string vazia é falsy, negada vira true)
console.log(!!"Olá");     // true (dupla negação, converte para boolean true)
console.log(!!"");        // false (dupla negação, converte para boolean false)
```

## 🛠️ Aplicações Práticas

### Valores Padrão (antes do ES6)

```js
function saudar(nome) {
  // Se nome for undefined, vazio ou outro valor falsy, usa "Visitante"
  nome = nome || "Visitante";
  return "Olá, " + nome + "!";
}

console.log(saudar("Maria")); // "Olá, Maria!"
console.log(saudar(""));      // "Olá, Visitante!"
console.log(saudar());        // "Olá, Visitante!"
```

### Execução Condicional

```js
// Executa a função apenas se a condição for verdadeira
const usuario = { premium: true, nome: "João" };

// A função só é chamada se usuario.premium for truthy
usuario.premium && exibirConteudoExclusivo();

// Versão moderna (ES6+): parâmetros padrão
function saudar(nome = "Visitante") {
  return `Olá, ${nome}!`;
}
```

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/> 