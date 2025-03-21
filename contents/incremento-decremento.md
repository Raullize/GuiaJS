<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🔄 Incremento e Decremento

Os operadores de incremento (`++`) e decremento (`--`) são formas concisas de adicionar ou subtrair 1 de uma variável.

## 📥 Pré-incremento vs Pós-incremento

### Pré-incremento (`++variavel`)
O valor é incrementado **antes** de ser utilizado na expressão.

```js
let contador = 5;
let resultado = ++contador; // contador é incrementado para 6, depois atribuído ao resultado

console.log(contador);  // 6
console.log(resultado); // 6
```

### Pós-incremento (`variavel++`)
O valor original é utilizado na expressão e **depois** incrementado.

```js
let contador = 5;
let resultado = contador++; // resultado recebe 5, depois contador é incrementado para 6

console.log(contador);  // 6
console.log(resultado); // 5
```

## 📉 Pré-decremento vs Pós-decremento

### Pré-decremento (`--variavel`)
O valor é decrementado **antes** de ser utilizado na expressão.

```js
let contador = 5;
let resultado = --contador; // contador é decrementado para 4, depois atribuído ao resultado

console.log(contador);  // 4
console.log(resultado); // 4
```

### Pós-decremento (`variavel--`)
O valor original é utilizado na expressão e **depois** decrementado.

```js
let contador = 5;
let resultado = contador--; // resultado recebe 5, depois contador é decrementado para 4

console.log(contador);  // 4
console.log(resultado); // 5
```

## 🛠️ Aplicações Práticas

Estes operadores são frequentemente utilizados em loops e contadores:

```js
// Usando pré-incremento em um loop
for (let i = 0; i < 5; ++i) {
    console.log(i);
}

// Usando pós-incremento para contar
let contagem = 0;
function registrarClique() {
    return contagem++;
}
```

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/> 