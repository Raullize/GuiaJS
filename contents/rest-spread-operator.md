<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🔄 Rest/Spread Operator (...)

O operador `...` (três pontos) é uma das funcionalidades mais versáteis do ES6+. Ele pode atuar como **Rest Operator** ou **Spread Operator**, dependendo do contexto de uso.

## 🎯 Conceitos Fundamentais

### Rest Operator (Operador Rest)
- **Coleta** múltiplos elementos em uma estrutura
- Usado em **parâmetros de função** e **desestruturação**
- Sempre aparece do **lado esquerdo** de uma atribuição

### Spread Operator (Operador Spread)
- **Expande** elementos de uma estrutura
- Usado para **espalhar** arrays, objetos e strings
- Sempre aparece do **lado direito** de uma atribuição

## 📥 Rest Operator

### Rest em Parâmetros de Função

Permite que uma função aceite um número indefinido de argumentos:

```javascript
// Função tradicional com argumentos limitados
function somarDois(a, b) {
    return a + b;
}

// Função com rest parameters
function somar(...numeros) {
    return numeros.reduce((total, num) => total + num, 0);
}

console.log(somar(1, 2, 3, 4, 5)); // 15
console.log(somar(10, 20)); // 30
console.log(somar()); // 0

// Combinando parâmetros normais com rest
function apresentar(nome, idade, ...hobbies) {
    console.log(`Nome: ${nome}`);
    console.log(`Idade: ${idade}`);
    console.log(`Hobbies: ${hobbies.join(', ')}`);
}

apresentar('Ana', 25, 'leitura', 'natação', 'culinária');
// Nome: Ana
// Idade: 25
// Hobbies: leitura, natação, culinária
```

### Rest em Desestruturação de Arrays

```javascript
const frutas = ['maçã', 'banana', 'laranja', 'uva', 'manga'];

// Extraindo alguns elementos e agrupando o resto
const [primeira, segunda, ...restante] = frutas;

console.log(primeira); // 'maçã'
console.log(segunda); // 'banana'
console.log(restante); // ['laranja', 'uva', 'manga']

// Ignorando elementos do meio
const [inicio, , , ...fim] = frutas;
console.log(inicio); // 'maçã'
console.log(fim); // ['uva', 'manga']
```

### Rest em Desestruturação de Objetos

```javascript
const usuario = {
    id: 1,
    nome: 'João',
    email: 'joao@email.com',
    idade: 30,
    cidade: 'São Paulo',
    profissao: 'Desenvolvedor'
};

// Extraindo algumas propriedades e agrupando o resto
const { id, nome, ...outrasInfo } = usuario;

console.log(id); // 1
console.log(nome); // 'João'
console.log(outrasInfo);
// { email: 'joao@email.com', idade: 30, cidade: 'São Paulo', profissao: 'Desenvolvedor' }

// Útil para remover propriedades
const { senha, ...usuarioSemSenha } = {
    id: 1,
    nome: 'Maria',
    email: 'maria@email.com',
    senha: '123456'
};

console.log(usuarioSemSenha);
// { id: 1, nome: 'Maria', email: 'maria@email.com' }
```

## 📤 Spread Operator

### Spread com Arrays

#### Copiando Arrays

```javascript
const original = [1, 2, 3];
const copia = [...original];

console.log(copia); // [1, 2, 3]
console.log(original === copia); // false (arrays diferentes)

// Modificando a cópia não afeta o original
copia.push(4);
console.log(original); // [1, 2, 3]
console.log(copia); // [1, 2, 3, 4]
```

#### Concatenando Arrays

```javascript
const array1 = [1, 2, 3];
const array2 = [4, 5, 6];
const array3 = [7, 8, 9];

// Método tradicional
const concatenado1 = array1.concat(array2, array3);

// Com spread operator (mais limpo)
const concatenado2 = [...array1, ...array2, ...array3];

console.log(concatenado2); // [1, 2, 3, 4, 5, 6, 7, 8, 9]

// Inserindo elementos no meio
const resultado = [...array1, 'meio', ...array2];
console.log(resultado); // [1, 2, 3, 'meio', 4, 5, 6]
```

#### Convertendo String em Array

```javascript
const palavra = 'JavaScript';
const letras = [...palavra];

console.log(letras); // ['J', 'a', 'v', 'a', 'S', 'c', 'r', 'i', 'p', 't']

// Útil para contar caracteres únicos
const caracteresUnicos = [...new Set(palavra.toLowerCase())];
console.log(caracteresUnicos); // ['j', 'a', 'v', 's', 'c', 'r', 'i', 'p', 't']
```

### Spread com Objetos

#### Copiando Objetos

```javascript
const original = {
    nome: 'Pedro',
    idade: 25,
    cidade: 'Rio de Janeiro'
};

const copia = { ...original };

console.log(copia); // { nome: 'Pedro', idade: 25, cidade: 'Rio de Janeiro' }
console.log(original === copia); // false (objetos diferentes)
```

#### Mesclando Objetos

```javascript
const dadosPessoais = {
    nome: 'Ana',
    idade: 28
};

const dadosProfissionais = {
    profissao: 'Designer',
    empresa: 'TechCorp'
};

const dadosContato = {
    email: 'ana@email.com',
    telefone: '(11) 99999-9999'
};

// Mesclando múltiplos objetos
const perfilCompleto = {
    ...dadosPessoais,
    ...dadosProfissionais,
    ...dadosContato
};

console.log(perfilCompleto);
// {
//   nome: 'Ana',
//   idade: 28,
//   profissao: 'Designer',
//   empresa: 'TechCorp',
//   email: 'ana@email.com',
//   telefone: '(11) 99999-9999'
// }
```

#### Sobrescrevendo Propriedades

```javascript
const configuracaoPadrao = {
    tema: 'claro',
    idioma: 'pt-BR',
    notificacoes: true,
    autoSave: false
};

const configuracaoUsuario = {
    tema: 'escuro',
    autoSave: true
};

// A ordem importa: propriedades posteriores sobrescrevem as anteriores
const configuracaoFinal = {
    ...configuracaoPadrao,
    ...configuracaoUsuario
};

console.log(configuracaoFinal);
// {
//   tema: 'escuro',        // sobrescrito
//   idioma: 'pt-BR',       // mantido
//   notificacoes: true,    // mantido
//   autoSave: true         // sobrescrito
// }
```

### Spread em Chamadas de Função

```javascript
// Função que espera argumentos separados
function calcularMedia(a, b, c, d) {
    return (a + b + c + d) / 4;
}

const notas = [8, 7, 9, 6];

// Método tradicional
const media1 = calcularMedia.apply(null, notas);

// Com spread operator (mais limpo)
const media2 = calcularMedia(...notas);

console.log(media2); // 7.5

// Encontrando o maior valor em um array
const numeros = [10, 5, 8, 3, 12, 7];
const maior = Math.max(...numeros);
const menor = Math.min(...numeros);

console.log(maior); // 12
console.log(menor); // 3
```

## 🔄 Combinando Rest e Spread

### Função que Remove Elementos

```javascript
function removerElementos(array, ...elementosParaRemover) {
    return array.filter(item => !elementosParaRemover.includes(item));
}

const numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const resultado = removerElementos(numeros, 2, 4, 6, 8);

console.log(resultado); // [1, 3, 5, 7, 9, 10]
```

### Função de Merge Avançada

```javascript
function mesclarObjetos(base, ...objetos) {
    return objetos.reduce((resultado, obj) => {
        return { ...resultado, ...obj };
    }, { ...base });
}

const base = { a: 1, b: 2 };
const obj1 = { c: 3, d: 4 };
const obj2 = { e: 5, f: 6 };
const obj3 = { a: 10 }; // sobrescreve 'a'

const resultado = mesclarObjetos(base, obj1, obj2, obj3);
console.log(resultado); // { a: 10, b: 2, c: 3, d: 4, e: 5, f: 6 }
```

## 🎨 Casos de Uso Práticos

### 1. Sistema de Logging

```javascript
class Logger {
    static log(nivel, mensagem, ...detalhes) {
        const timestamp = new Date().toISOString();
        console.log(`[${timestamp}] ${nivel.toUpperCase()}: ${mensagem}`);
        
        if (detalhes.length > 0) {
            console.log('Detalhes:', ...detalhes);
        }
    }
    
    static info(mensagem, ...detalhes) {
        this.log('info', mensagem, ...detalhes);
    }
    
    static error(mensagem, ...detalhes) {
        this.log('error', mensagem, ...detalhes);
    }
}

// Uso
Logger.info('Usuário logado', { id: 123, nome: 'João' });
Logger.error('Erro na API', { status: 500, url: '/api/users' }, 'Timeout');
```

### 2. Manipulação de Estado (React-style)

```javascript
class EstadoApp {
    constructor() {
        this.estado = {
            usuario: null,
            configuracoes: {
                tema: 'claro',
                idioma: 'pt-BR'
            },
            dados: []
        };
    }
    
    // Atualizar estado mantendo imutabilidade
    atualizarEstado(novoEstado) {
        this.estado = {
            ...this.estado,
            ...novoEstado
        };
    }
    
    // Atualizar configurações específicas
    atualizarConfiguracoes(novasConfiguracoes) {
        this.estado = {
            ...this.estado,
            configuracoes: {
                ...this.estado.configuracoes,
                ...novasConfiguracoes
            }
        };
    }
    
    // Adicionar item aos dados
    adicionarDados(...novosItens) {
        this.estado = {
            ...this.estado,
            dados: [...this.estado.dados, ...novosItens]
        };
    }
}

const app = new EstadoApp();
app.atualizarConfiguracoes({ tema: 'escuro' });
app.adicionarDados({ id: 1, nome: 'Item 1' }, { id: 2, nome: 'Item 2' });
```

### 3. Utilitários de Array

```javascript
class ArrayUtils {
    // Remover duplicatas
    static removerDuplicatas(array) {
        return [...new Set(array)];
    }
    
    // Achatar array aninhado
    static achatar(array) {
        return array.reduce((acc, val) => {
            return Array.isArray(val) 
                ? [...acc, ...this.achatar(val)]
                : [...acc, val];
        }, []);
    }
    
    // Intercalar arrays
    static intercalar(...arrays) {
        const maxLength = Math.max(...arrays.map(arr => arr.length));
        const resultado = [];
        
        for (let i = 0; i < maxLength; i++) {
            arrays.forEach(array => {
                if (i < array.length) {
                    resultado.push(array[i]);
                }
            });
        }
        
        return resultado;
    }
    
    // Dividir array em chunks
    static dividirEmChunks(array, tamanho) {
        const chunks = [];
        for (let i = 0; i < array.length; i += tamanho) {
            chunks.push([...array.slice(i, i + tamanho)]);
        }
        return chunks;
    }
}

// Exemplos de uso
const numeros = [1, 2, 2, 3, 3, 3, 4, 5];
console.log(ArrayUtils.removerDuplicatas(numeros)); // [1, 2, 3, 4, 5]

const aninhado = [1, [2, 3], [4, [5, 6]]];
console.log(ArrayUtils.achatar(aninhado)); // [1, 2, 3, 4, 5, 6]

const array1 = ['a', 'b', 'c'];
const array2 = [1, 2, 3];
console.log(ArrayUtils.intercalar(array1, array2)); // ['a', 1, 'b', 2, 'c', 3]

const lista = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
console.log(ArrayUtils.dividirEmChunks(lista, 3)); // [[1, 2, 3], [4, 5, 6], [7, 8, 9], [10]]
```

### 4. Sistema de Validação

```javascript
class Validador {
    static validar(objeto, ...validacoes) {
        const erros = [];
        
        validacoes.forEach(validacao => {
            const resultado = validacao(objeto);
            if (resultado !== true) {
                erros.push(resultado);
            }
        });
        
        return {
            valido: erros.length === 0,
            erros: [...erros]
        };
    }
}

// Funções de validação
const validarNome = (obj) => 
    obj.nome && obj.nome.length >= 2 ? true : 'Nome deve ter pelo menos 2 caracteres';

const validarEmail = (obj) => 
    /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(obj.email) ? true : 'Email inválido';

const validarIdade = (obj) => 
    obj.idade >= 18 ? true : 'Idade deve ser maior ou igual a 18';

// Uso
const usuario = {
    nome: 'A',
    email: 'email-invalido',
    idade: 16
};

const resultado = Validador.validar(
    usuario,
    validarNome,
    validarEmail,
    validarIdade
);

console.log(resultado);
// {
//   valido: false,
//   erros: [
//     'Nome deve ter pelo menos 2 caracteres',
//     'Email inválido',
//     'Idade deve ser maior ou igual a 18'
//   ]
// }
```

## ⚠️ Cuidados e Limitações

### 1. Cópia Superficial (Shallow Copy)

```javascript
const original = {
    nome: 'João',
    endereco: {
        rua: 'Rua A',
        cidade: 'São Paulo'
    }
};

const copia = { ...original };

// Modificar propriedade aninhada afeta ambos os objetos
copia.endereco.cidade = 'Rio de Janeiro';

console.log(original.endereco.cidade); // 'Rio de Janeiro' (foi alterado!)
console.log(copia.endereco.cidade); // 'Rio de Janeiro'

// Para cópia profunda, use outras técnicas
const copiaCompleta = {
    ...original,
    endereco: { ...original.endereco }
};
```

### 2. Performance com Arrays Grandes

```javascript
// ❌ Ineficiente para arrays muito grandes
const arrayGigante = new Array(1000000).fill(0);
const copia = [...arrayGigante]; // Pode ser lento

// ✅ Para arrays grandes, considere outras abordagens
const copiaEficiente = Array.from(arrayGigante);
```

### 3. Rest Parameter deve ser o Último

```javascript
// ❌ Erro: Rest parameter deve ser o último
// function exemplo(...rest, ultimo) { }

// ✅ Correto
function exemplo(primeiro, segundo, ...rest) {
    console.log(primeiro, segundo, rest);
}
```

## 🏆 Boas Práticas

### 1. Use Nomes Descritivos para Rest Parameters

```javascript
// ✅ Bom
function criarUsuario(nome, email, ...permissoes) {
    return { nome, email, permissoes };
}

// ❌ Menos claro
function criarUsuario(nome, email, ...args) {
    return { nome, email, permissoes: args };
}
```

### 2. Prefira Spread para Imutabilidade

```javascript
// ✅ Imutável
const adicionarItem = (lista, novoItem) => [...lista, novoItem];

// ❌ Mutável
const adicionarItem = (lista, novoItem) => {
    lista.push(novoItem);
    return lista;
};
```

### 3. Combine com Desestruturação

```javascript
// ✅ Elegante e legível
const processarDados = ({ id, nome, ...outrosDados }) => {
    return {
        identificacao: { id, nome },
        detalhes: { ...outrosDados }
    };
};
```

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>