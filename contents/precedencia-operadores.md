<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 📊 Precedência de Operadores

A precedência de operadores em JavaScript determina a ordem na qual as operações são processadas em uma expressão.

## 📋 Tabela de Precedência

Os operadores abaixo estão listados em ordem decrescente de precedência (dos mais prioritários para os menos prioritários):

| Precedência | Categoria | Operadores |
|-------------|-----------|------------|
| 1 | Agrupamento | `( ... )` |
| 2 | Acesso a membros/índices | `obj.prop`, `obj["prop"]`, `array[i]` |
| 3 | Chamada de função/expressões `new` | `func()`, `new Objeto()` |
| 4 | Incremento/Decremento | `++`, `--` (como sufixo ou prefixo) |
| 5 | Negação/Conversão de tipos | `!`, `+`, `-`, `typeof`, `void`, `delete` |
| 6 | Exponenciação | `**` |
| 7 | Multiplicação/Divisão/Módulo | `*`, `/`, `%` |
| 8 | Adição/Subtração | `+`, `-` |
| 9 | Operadores bit a bit | `<<`, `>>`, `>>>` |
| 10 | Comparações | `<`, `<=`, `>`, `>=`, `instanceof`, `in` |
| 11 | Igualdade | `==`, `!=`, `===`, `!==` |
| 12 | AND bit a bit | `&` |
| 13 | XOR bit a bit | `^` |
| 14 | OR bit a bit | `\|` |
| 15 | AND lógico | `&&` |
| 16 | OR lógico | `\|\|` |
| 17 | Optional Chaining | `?.` |
| 18 | Condicional (ternário) | `? :` |
| 19 | Atribuição | `=`, `+=`, `-=`, `*=`, etc. |
| 20 | Vírgula | `,` |

## 📚 Exemplos Práticos

### Expressões Matemáticas

```js
// Precedência entre multiplicação e adição
console.log(2 + 3 * 4);     // 14 (não 20)
console.log((2 + 3) * 4);   // 20 (parênteses alteram a precedência)

// Exponenciação tem precedência sobre multiplicação
console.log(2 * 3 ** 2);    // 18 (não 36)
console.log((2 * 3) ** 2);  // 36
```

### Operadores Lógicos

```js
// && tem precedência maior que ||
console.log(true || false && false); // true
console.log((true || false) && false); // false
```

### Múltiplos Operadores

```js
let a = 5;
let b = 10;
let c = 15;

// Avaliação complexa
let resultado = a + b * c / 5 - 3;
console.log(resultado); // 32

// Equivalente a:
let resultadoDecomposto = a + ((b * c) / 5) - 3;
console.log(resultadoDecomposto); // 32
```

### Operadores de Incremento/Decremento

```js
let x = 5;
let y = 10;
let z;

// Precedência entre incremento e atribuição
z = x++ + y;
console.log(z);  // 15 (x é usado e depois incrementado)
console.log(x);  // 6

// Redefinindo
x = 5;
z = ++x + y;
console.log(z);  // 16 (x é incrementado primeiro)
console.log(x);  // 6
```

## 🔧 Dicas para Evitar Problemas de Precedência

1. **Use parênteses** para deixar claro a ordem desejada de operações
2. **Divida expressões complexas** em expressões menores e mais simples
3. **Atribua resultados intermediários** a variáveis para maior clareza
4. **Evite confiar implicitamente** na precedência de operadores para código mais legível

```js
// Expressão complexa
let resultado = a && b || c && d;

// Mais claro com parênteses
let resultadoClaro = (a && b) || (c && d);

// Ainda mais claro com variáveis intermediárias
let parte1 = a && b;
let parte2 = c && d;
let resultadoMuitoClaro = parte1 || parte2;
```

## 🔗 Optional Chaining (?.) - Detalhado

O Optional Chaining é um operador introduzido no ES2020 que permite acessar propriedades aninhadas de objetos sem gerar erros se alguma propriedade intermediária for `null` ou `undefined`.

### 🎯 Sintaxe Básica

```javascript
// Sintaxe tradicional (pode gerar erro)
const nome = usuario.perfil.nome;

// Com Optional Chaining (seguro)
const nome = usuario?.perfil?.nome;
```

### 📋 Casos de Uso

#### 1. Acesso a Propriedades de Objetos

```javascript
const usuario = {
    id: 1,
    nome: 'João',
    endereco: {
        rua: 'Rua das Flores, 123',
        cidade: 'São Paulo',
        coordenadas: {
            lat: -23.5505,
            lng: -46.6333
        }
    }
};

// ✅ Funciona normalmente
console.log(usuario?.nome); // 'João'
console.log(usuario?.endereco?.cidade); // 'São Paulo'
console.log(usuario?.endereco?.coordenadas?.lat); // -23.5505

// ✅ Retorna undefined sem erro
console.log(usuario?.telefone); // undefined
console.log(usuario?.endereco?.cep); // undefined
console.log(usuario?.trabalho?.empresa?.nome); // undefined

// ❌ Sem Optional Chaining geraria erro
// console.log(usuario.trabalho.empresa.nome); // TypeError!
```

#### 2. Chamada de Métodos Opcionais

```javascript
const api = {
    usuarios: {
        buscar: function(id) {
            return { id, nome: `Usuário ${id}` };
        }
    }
};

// ✅ Chama o método se existir
const usuario = api?.usuarios?.buscar?.(123);
console.log(usuario); // { id: 123, nome: 'Usuário 123' }

// ✅ Retorna undefined se o método não existir
const resultado = api?.produtos?.listar?.();
console.log(resultado); // undefined

// ❌ Sem Optional Chaining geraria erro
// api.produtos.listar(); // TypeError!
```

#### 3. Acesso a Arrays e Índices

```javascript
const dados = {
    usuarios: [
        { nome: 'Ana', idade: 25 },
        { nome: 'Bruno', idade: 30 },
        { nome: 'Carlos', idade: 35 }
    ]
};

// ✅ Acesso seguro a elementos do array
console.log(dados?.usuarios?.[0]?.nome); // 'Ana'
console.log(dados?.usuarios?.[10]?.nome); // undefined
console.log(dados?.produtos?.[0]?.preco); // undefined

// Exemplo com array que pode não existir
const config = null;
console.log(config?.servidores?.[0]?.url); // undefined
```

### 🔄 Comparação: Antes vs Depois

#### Antes do Optional Chaining

```javascript
// Verificações manuais verbosas
function obterCidadeUsuario(usuario) {
    if (usuario && 
        usuario.endereco && 
        usuario.endereco.cidade) {
        return usuario.endereco.cidade;
    }
    return 'Cidade não informada';
}

// Ou usando try/catch
function obterLatitude(usuario) {
    try {
        return usuario.endereco.coordenadas.lat;
    } catch (error) {
        return null;
    }
}
```

#### Depois do Optional Chaining

```javascript
// Muito mais conciso e legível
function obterCidadeUsuario(usuario) {
    return usuario?.endereco?.cidade ?? 'Cidade não informada';
}

function obterLatitude(usuario) {
    return usuario?.endereco?.coordenadas?.lat ?? null;
}
```

### 🎨 Exemplos Práticos

#### 1. Processamento de Dados de API

```javascript
// Resposta de API que pode ter estruturas variáveis
const respostaAPI = {
    status: 'success',
    data: {
        usuario: {
            id: 123,
            perfil: {
                nome: 'Maria Silva',
                avatar: 'https://exemplo.com/avatar.jpg',
                configuracoes: {
                    tema: 'escuro',
                    notificacoes: {
                        email: true,
                        push: false
                    }
                }
            },
            historico: [
                { acao: 'login', timestamp: '2024-01-15T10:30:00Z' },
                { acao: 'logout', timestamp: '2024-01-15T18:45:00Z' }
            ]
        }
    }
};

// Extraindo dados com segurança
const nomeUsuario = respostaAPI?.data?.usuario?.perfil?.nome;
const temaPref = respostaAPI?.data?.usuario?.perfil?.configuracoes?.tema;
const emailNotif = respostaAPI?.data?.usuario?.perfil?.configuracoes?.notificacoes?.email;
const ultimaAcao = respostaAPI?.data?.usuario?.historico?.[0]?.acao;

console.log({
    nome: nomeUsuario ?? 'Nome não disponível',
    tema: temaPref ?? 'claro',
    notificacaoEmail: emailNotif ?? false,
    ultimaAcao: ultimaAcao ?? 'Nenhuma ação registrada'
});
```

#### 2. Configuração de Aplicação

```javascript
class ConfiguradorApp {
    constructor(config = {}) {
        this.config = config;
    }
    
    obterConfiguracao(chave, valorPadrao = null) {
        // Suporte a chaves aninhadas como 'database.host'
        const chaves = chave.split('.');
        let valor = this.config;
        
        for (const k of chaves) {
            valor = valor?.[k];
            if (valor === undefined) break;
        }
        
        return valor ?? valorPadrao;
    }
    
    // Métodos específicos usando Optional Chaining
    obterHostBanco() {
        return this.config?.database?.host ?? 'localhost';
    }
    
    obterPortaServidor() {
        return this.config?.servidor?.porta ?? 3000;
    }
    
    obterChaveAPI() {
        return this.config?.apis?.externa?.chave ?? null;
    }
    
    isDebugHabilitado() {
        return this.config?.desenvolvimento?.debug ?? false;
    }
}

// Uso
const config = new ConfiguradorApp({
    database: {
        host: 'db.exemplo.com',
        porta: 5432
    },
    servidor: {
        porta: 8080
    },
    desenvolvimento: {
        debug: true
    }
});

console.log(config.obterHostBanco()); // 'db.exemplo.com'
console.log(config.obterChaveAPI()); // null
console.log(config.isDebugHabilitado()); // true
```

#### 3. Manipulação de DOM

```javascript
class ManipuladorDOM {
    // Busca elemento com segurança
    static buscarElemento(seletor) {
        return document?.querySelector?.(seletor);
    }
    
    // Obtém texto de elemento aninhado
    static obterTextoAninhado(seletor, seletorFilho) {
        return this.buscarElemento(seletor)
            ?.querySelector?.(seletorFilho)
            ?.textContent?.trim();
    }
    
    // Adiciona evento com verificação
    static adicionarEvento(seletor, evento, callback) {
        const elemento = this.buscarElemento(seletor);
        elemento?.addEventListener?.(evento, callback);
        return elemento !== null;
    }
    
    // Obtém dados de atributo
    static obterDadosAtributo(seletor, atributo) {
        return this.buscarElemento(seletor)
            ?.dataset?.[atributo];
    }
}

// Uso
const titulo = ManipuladorDOM.obterTextoAninhado('.card', 'h2');
const userId = ManipuladorDOM.obterDadosAtributo('#user-profile', 'userId');
const eventoAdicionado = ManipuladorDOM.adicionarEvento('#btn-submit', 'click', () => {
    console.log('Botão clicado!');
});

console.log({ titulo, userId, eventoAdicionado });
```

### ⚠️ Cuidados e Limitações

#### 1. Performance

```javascript
// ❌ Evitar uso excessivo em loops
for (let i = 0; i < 1000000; i++) {
    // Cada ?. tem um pequeno overhead
    const valor = dados?.lista?.[i]?.propriedade?.valor;
}

// ✅ Melhor: verificar uma vez
if (dados?.lista) {
    for (let i = 0; i < dados.lista.length; i++) {
        const item = dados.lista[i];
        if (item?.propriedade) {
            const valor = item.propriedade.valor;
        }
    }
}
```

#### 2. Não Substitui Validação Adequada

```javascript
// ❌ Optional Chaining não valida tipos
const idade = usuario?.idade; // pode ser string, null, etc.

// ✅ Combine com validação
const idade = typeof usuario?.idade === 'number' ? usuario.idade : 0;
```

#### 3. Debugging Pode Ser Mais Difícil

```javascript
// Pode ser difícil saber onde exatamente falhou
const resultado = a?.b?.c?.d?.e?.f?.g;

// Para debugging, considere dividir:
const b = a?.b;
const c = b?.c;
const d = c?.d;
// etc...
```

### 🏆 Boas Práticas

#### 1. Combine com Nullish Coalescing (??)

```javascript
// ✅ Excelente combinação
const nome = usuario?.perfil?.nome ?? 'Nome não informado';
const configuracoes = app?.config?.usuario ?? {};
```

#### 2. Use em Validações de Entrada

```javascript
function processarPedido(pedido) {
    // Validação segura de estrutura
    if (!pedido?.itens?.length) {
        throw new Error('Pedido deve ter pelo menos um item');
    }
    
    const total = pedido.itens.reduce((sum, item) => {
        return sum + (item?.preco ?? 0) * (item?.quantidade ?? 1);
    }, 0);
    
    return {
        id: pedido?.id ?? Date.now(),
        cliente: pedido?.cliente?.nome ?? 'Cliente não identificado',
        total,
        desconto: pedido?.desconto?.valor ?? 0
    };
}
```

#### 3. Documente Estruturas Esperadas

```javascript
/**
 * Processa dados do usuário
 * @param {Object} usuario - Objeto do usuário
 * @param {string} usuario.nome - Nome do usuário
 * @param {Object} [usuario.endereco] - Endereço (opcional)
 * @param {string} [usuario.endereco.cidade] - Cidade (opcional)
 * @param {Object} [usuario.configuracoes] - Configurações (opcional)
 */
function processarUsuario(usuario) {
    return {
        nome: usuario?.nome ?? 'Sem nome',
        cidade: usuario?.endereco?.cidade ?? 'Não informado',
        tema: usuario?.configuracoes?.tema ?? 'claro'
    };
}
```

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>