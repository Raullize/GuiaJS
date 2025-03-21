<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🔢 Variáveis: `var`, `let`, `const`

| Tipo  | Escopo | Mutável? | Boas Práticas |
|-------|--------|----------|--------------|
| `var` | Global/Função | Sim | Evitar o uso |
| `let` | Bloco | Sim | Usar para variáveis mutáveis |
| `const` | Bloco | Não | Usar para constantes |

**Dicas:**
- JavaScript é **case-sensitive** (`minhaVar` e `minhavar` são variáveis diferentes).
- Escolha uma notação consistente para nomes de variáveis:
  - **camelCase**: `minhaVariavel` (primeira palavra em minúscula, demais com iniciais maiúsculas)
  - **PascalCase**: `MinhaVariavel` (todas as palavras com iniciais maiúsculas)
  - **snake_case**: `minha_variavel` (palavras separadas por underscores)
  - **kebab-case**: Não é permitido em JavaScript (`minha-variavel` é inválido)

```js
// Exemplos das diferentes notações
let nomeUsuario = "Maria";    // camelCase (comum para variáveis e funções)
let PessoaClasse = {};        // PascalCase (comum para classes)
let primeiro_nome = "João";   // snake_case (menos comum em JS)
```

> 📝 **Importante**: As variáveis em JavaScript são afetadas pelo conceito de "hoisting", o que influencia como e quando elas podem ser usadas. Para entender esse comportamento, consulte o [guia sobre hoisting](hoisting.md).

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>