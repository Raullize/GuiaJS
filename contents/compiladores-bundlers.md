<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=header"/>

# 🛠️ Compiladores e Bundlers JavaScript

Compiladores e bundlers são ferramentas essenciais no desenvolvimento JavaScript moderno, permitindo usar recursos avançados da linguagem, otimizar código e gerenciar dependências.

## 🎯 Conceitos Fundamentais

### O que são Compiladores?

**Compiladores** transformam código JavaScript moderno (ES6+) em versões compatíveis com navegadores mais antigos.

### O que são Bundlers?

**Bundlers** combinam múltiplos arquivos JavaScript e suas dependências em um ou poucos arquivos otimizados para produção.

### Por que usar?

- ✅ **Compatibilidade**: Usar recursos modernos em navegadores antigos
- ✅ **Otimização**: Minificação, tree shaking, code splitting
- ✅ **Modularização**: Organizar código em módulos
- ✅ **Desenvolvimento**: Hot reload, source maps, debugging
- ✅ **Performance**: Carregamento otimizado de recursos

## 🔧 Principais Compiladores

### Babel

O compilador JavaScript mais popular para transformar código ES6+ em ES5.

#### Instalação e Configuração

```bash
# Instalação
npm install --save-dev @babel/core @babel/cli @babel/preset-env

# Para React
npm install --save-dev @babel/preset-react

# Para TypeScript
npm install --save-dev @babel/preset-typescript
```

#### Configuração (.babelrc.json)

```json
{
  "presets": [
    [
      "@babel/preset-env",
      {
        "targets": {
          "browsers": ["> 1%", "last 2 versions"]
        },
        "useBuiltIns": "usage",
        "corejs": 3
      }
    ],
    "@babel/preset-react"
  ],
  "plugins": [
    "@babel/plugin-proposal-class-properties",
    "@babel/plugin-proposal-optional-chaining",
    "@babel/plugin-proposal-nullish-coalescing-operator"
  ]
}
```

#### Exemplo de Transformação

```javascript
// Código ES6+ (entrada)
class Usuario {
  constructor(nome) {
    this.nome = nome;
  }
  
  saudar = () => {
    return `Olá, ${this.nome}!`;
  }
  
  obterInfo() {
    return this.dados?.pessoais?.idade ?? 'Não informado';
  }
}

const usuarios = ['Ana', 'Bruno'].map(nome => new Usuario(nome));
```

```javascript
// Código ES5 (saída após Babel)
"use strict";

function _classCallCheck(instance, Constructor) {
  if (!(instance instanceof Constructor)) {
    throw new TypeError("Cannot call a class as a function");
  }
}

var Usuario = function Usuario(nome) {
  var _this = this;
  
  _classCallCheck(this, Usuario);
  
  this.saudar = function () {
    return "Ol\xE1, ".concat(_this.nome, "!");
  };
  
  this.nome = nome;
};

Usuario.prototype.obterInfo = function obterInfo() {
  var _this$dados, _this$dados$pessoais;
  
  return (_this$dados = this.dados) === null || _this$dados === void 0 ? 
    void 0 : (_this$dados$pessoais = _this$dados.pessoais) === null || 
    _this$dados$pessoais === void 0 ? void 0 : _this$dados$pessoais.idade) !== null && 
    _temp !== void 0 ? _temp : 'Não informado';
};

var usuarios = ['Ana', 'Bruno'].map(function (nome) {
  return new Usuario(nome);
});
```

### TypeScript Compiler (tsc)

Compilador oficial do TypeScript que também pode processar JavaScript.

#### Configuração (tsconfig.json)

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "ESNext",
    "moduleResolution": "node",
    "allowJs": true,
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": false
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "dist"]
}
```

## 📦 Principais Bundlers

### Webpack

O bundler mais popular e configurável do ecossistema JavaScript.

#### Instalação

```bash
npm install --save-dev webpack webpack-cli webpack-dev-server
npm install --save-dev html-webpack-plugin css-loader style-loader
npm install --save-dev babel-loader @babel/core @babel/preset-env
```

#### Configuração Básica (webpack.config.js)

```javascript
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.[contenthash].js',
    clean: true
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['@babel/preset-env']
          }
        }
      },
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader']
      },
      {
        test: /\.(png|svg|jpg|jpeg|gif)$/i,
        type: 'asset/resource'
      }
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: './src/index.html'
    })
  ],
  devServer: {
    static: './dist',
    hot: true,
    open: true
  },
  optimization: {
    splitChunks: {
      chunks: 'all'
    }
  }
};
```

#### Configuração Avançada

```javascript
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const MiniCssExtractPlugin = require('mini-css-extract-plugin');
const { BundleAnalyzerPlugin } = require('webpack-bundle-analyzer');

module.exports = (env, argv) => {
  const isProduction = argv.mode === 'production';
  
  return {
    entry: {
      main: './src/index.js',
      vendor: './src/vendor.js'
    },
    output: {
      path: path.resolve(__dirname, 'dist'),
      filename: isProduction 
        ? '[name].[contenthash].js' 
        : '[name].js',
      clean: true
    },
    module: {
      rules: [
        {
          test: /\.js$/,
          exclude: /node_modules/,
          use: 'babel-loader'
        },
        {
          test: /\.css$/,
          use: [
            isProduction ? MiniCssExtractPlugin.loader : 'style-loader',
            'css-loader',
            'postcss-loader'
          ]
        }
      ]
    },
    plugins: [
      new HtmlWebpackPlugin({
        template: './src/index.html',
        minify: isProduction
      }),
      ...(isProduction ? [
        new MiniCssExtractPlugin({
          filename: '[name].[contenthash].css'
        }),
        new BundleAnalyzerPlugin({
          analyzerMode: 'static',
          openAnalyzer: false
        })
      ] : [])
    ],
    optimization: {
      splitChunks: {
        cacheGroups: {
          vendor: {
            test: /[\\/]node_modules[\\/]/,
            name: 'vendors',
            chunks: 'all'
          }
        }
      }
    },
    devtool: isProduction ? 'source-map' : 'eval-source-map'
  };
};
```

### Vite

Bundler moderno e extremamente rápido, especialmente para desenvolvimento.

#### Instalação e Configuração

```bash
npm create vite@latest meu-projeto -- --template vanilla
# ou
npm create vite@latest meu-projeto -- --template react
# ou
npm create vite@latest meu-projeto -- --template vue
```

#### Configuração (vite.config.js)

```javascript
import { defineConfig } from 'vite';
import { resolve } from 'path';

export default defineConfig({
  // Configuração de desenvolvimento
  server: {
    port: 3000,
    open: true,
    hot: true
  },
  
  // Configuração de build
  build: {
    outDir: 'dist',
    sourcemap: true,
    minify: 'terser',
    rollupOptions: {
      input: {
        main: resolve(__dirname, 'index.html'),
        admin: resolve(__dirname, 'admin.html')
      },
      output: {
        manualChunks: {
          vendor: ['lodash', 'axios'],
          ui: ['react', 'react-dom']
        }
      }
    }
  },
  
  // Aliases
  resolve: {
    alias: {
      '@': resolve(__dirname, 'src'),
      '@components': resolve(__dirname, 'src/components'),
      '@utils': resolve(__dirname, 'src/utils')
    }
  },
  
  // Plugins
  plugins: [
    // Plugins específicos aqui
  ],
  
  // Variáveis de ambiente
  define: {
    __APP_VERSION__: JSON.stringify(process.env.npm_package_version)
  }
});
```

### Rollup

Bundler focado em ES modules, ideal para bibliotecas.

#### Configuração (rollup.config.js)

```javascript
import resolve from '@rollup/plugin-node-resolve';
import commonjs from '@rollup/plugin-commonjs';
import babel from '@rollup/plugin-babel';
import terser from '@rollup/plugin-terser';
import { readFileSync } from 'fs';

const pkg = JSON.parse(readFileSync('./package.json', 'utf8'));

export default {
  input: 'src/index.js',
  output: [
    {
      file: pkg.main,
      format: 'cjs',
      sourcemap: true
    },
    {
      file: pkg.module,
      format: 'esm',
      sourcemap: true
    },
    {
      file: 'dist/bundle.umd.js',
      format: 'umd',
      name: 'MinhaLib',
      sourcemap: true
    }
  ],
  plugins: [
    resolve({
      browser: true
    }),
    commonjs(),
    babel({
      babelHelpers: 'bundled',
      exclude: 'node_modules/**'
    }),
    terser()
  ],
  external: ['react', 'react-dom']
};
```

### Parcel

Bundler com configuração zero, muito simples de usar.

#### Uso Básico

```bash
# Instalação
npm install --save-dev parcel

# Desenvolvimento
npx parcel src/index.html

# Build para produção
npx parcel build src/index.html
```

#### Configuração (.parcelrc)

```json
{
  "extends": "@parcel/config-default",
  "transformers": {
    "*.{js,mjs,jsm,jsx,es6,cjs,ts,tsx}": [
      "@parcel/transformer-js",
      "@parcel/transformer-react-refresh-wrap"
    ]
  },
  "optimizers": {
    "*.{js,mjs,jsm,jsx,es6,cjs,ts,tsx}": [
      "@parcel/optimizer-swc"
    ]
  }
}
```

## ⚡ Ferramentas Modernas

### esbuild

Bundler extremamente rápido escrito em Go.

```javascript
// build.js
const esbuild = require('esbuild');

esbuild.build({
  entryPoints: ['src/index.js'],
  bundle: true,
  outfile: 'dist/bundle.js',
  minify: true,
  sourcemap: true,
  target: ['es2020'],
  loader: {
    '.png': 'file',
    '.svg': 'text'
  },
  define: {
    'process.env.NODE_ENV': '"production"'
  }
}).catch(() => process.exit(1));
```

### SWC

Compilador JavaScript/TypeScript extremamente rápido escrito em Rust.

```json
// .swcrc
{
  "jsc": {
    "parser": {
      "syntax": "ecmascript",
      "jsx": true,
      "decorators": true,
      "dynamicImport": true
    },
    "transform": {
      "react": {
        "pragma": "React.createElement",
        "pragmaFrag": "React.Fragment",
        "throwIfNamespace": true,
        "development": false,
        "useBuiltins": false
      }
    },
    "target": "es2020"
  },
  "module": {
    "type": "es6"
  },
  "minify": true
}
```

## 🎨 Casos de Uso Práticos

### 1. Projeto React com Webpack

```javascript
// webpack.config.js para React
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const { CleanWebpackPlugin } = require('clean-webpack-plugin');

module.exports = {
  entry: './src/index.jsx',
  output: {
    path: path.resolve(__dirname, 'build'),
    filename: 'static/js/[name].[contenthash:8].js',
    chunkFilename: 'static/js/[name].[contenthash:8].chunk.js'
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: [
              '@babel/preset-env',
              '@babel/preset-react'
            ]
          }
        }
      },
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader']
      },
      {
        test: /\.(png|jpe?g|gif|svg)$/,
        use: {
          loader: 'file-loader',
          options: {
            outputPath: 'static/media/'
          }
        }
      }
    ]
  },
  plugins: [
    new CleanWebpackPlugin(),
    new HtmlWebpackPlugin({
      template: 'public/index.html',
      favicon: 'public/favicon.ico'
    })
  ],
  resolve: {
    extensions: ['.js', '.jsx']
  },
  devServer: {
    contentBase: path.join(__dirname, 'public'),
    hot: true,
    port: 3000
  }
};
```

### 2. Biblioteca com Rollup

```javascript
// rollup.config.js para biblioteca
import resolve from '@rollup/plugin-node-resolve';
import commonjs from '@rollup/plugin-commonjs';
import babel from '@rollup/plugin-babel';
import { terser } from 'rollup-plugin-terser';
import pkg from './package.json';

const banner = `/*!
 * ${pkg.name} v${pkg.version}
 * ${pkg.description}
 * ${pkg.homepage}
 * 
 * Copyright (c) ${new Date().getFullYear()} ${pkg.author}
 * Released under the ${pkg.license} License
 */`;

export default [
  // ES Module build
  {
    input: 'src/index.js',
    output: {
      file: pkg.module,
      format: 'esm',
      banner
    },
    plugins: [
      resolve(),
      commonjs(),
      babel({
        babelHelpers: 'bundled',
        exclude: 'node_modules/**'
      })
    ],
    external: Object.keys(pkg.peerDependencies || {})
  },
  
  // CommonJS build
  {
    input: 'src/index.js',
    output: {
      file: pkg.main,
      format: 'cjs',
      banner
    },
    plugins: [
      resolve(),
      commonjs(),
      babel({
        babelHelpers: 'bundled',
        exclude: 'node_modules/**'
      })
    ],
    external: Object.keys(pkg.peerDependencies || {})
  },
  
  // UMD build (minified)
  {
    input: 'src/index.js',
    output: {
      file: 'dist/index.umd.min.js',
      format: 'umd',
      name: 'MinhaLib',
      banner
    },
    plugins: [
      resolve(),
      commonjs(),
      babel({
        babelHelpers: 'bundled',
        exclude: 'node_modules/**'
      }),
      terser()
    ]
  }
];
```

### 3. Configuração Multi-ambiente

```javascript
// webpack.common.js
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  plugins: [
    new HtmlWebpackPlugin({
      template: './src/index.html'
    })
  ],
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: 'babel-loader'
      }
    ]
  }
};

// webpack.dev.js
const { merge } = require('webpack-merge');
const common = require('./webpack.common.js');

module.exports = merge(common, {
  mode: 'development',
  devtool: 'inline-source-map',
  devServer: {
    static: './dist',
    hot: true
  },
  module: {
    rules: [
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader']
      }
    ]
  }
});

// webpack.prod.js
const { merge } = require('webpack-merge');
const common = require('./webpack.common.js');
const MiniCssExtractPlugin = require('mini-css-extract-plugin');
const CssMinimizerPlugin = require('css-minimizer-webpack-plugin');

module.exports = merge(common, {
  mode: 'production',
  devtool: 'source-map',
  plugins: [
    new MiniCssExtractPlugin({
      filename: '[name].[contenthash].css'
    })
  ],
  module: {
    rules: [
      {
        test: /\.css$/,
        use: [MiniCssExtractPlugin.loader, 'css-loader']
      }
    ]
  },
  optimization: {
    minimizer: [
      '...',
      new CssMinimizerPlugin()
    ],
    splitChunks: {
      chunks: 'all'
    }
  }
});
```

## 📊 Comparação de Ferramentas

| Ferramenta | Velocidade | Configuração | Ecossistema | Melhor Para |
|------------|------------|--------------|-------------|-------------|
| **Webpack** | Média | Complexa | Muito Rico | Apps grandes, configuração avançada |
| **Vite** | Muito Rápida | Simples | Crescendo | Desenvolvimento moderno, protótipos |
| **Rollup** | Rápida | Média | Bom | Bibliotecas, tree shaking |
| **Parcel** | Rápida | Zero | Limitado | Projetos simples, iniciantes |
| **esbuild** | Extremamente Rápida | Simples | Limitado | Build rápido, ferramentas |

## 🏆 Boas Práticas

### 1. Configuração por Ambiente

```javascript
// Separar configurações por ambiente
const isDevelopment = process.env.NODE_ENV === 'development';

module.exports = {
  mode: isDevelopment ? 'development' : 'production',
  devtool: isDevelopment ? 'eval-source-map' : 'source-map',
  optimization: {
    minimize: !isDevelopment
  }
};
```

### 2. Code Splitting

```javascript
// Divisão automática de código
optimization: {
  splitChunks: {
    cacheGroups: {
      vendor: {
        test: /[\\/]node_modules[\\/]/,
        name: 'vendors',
        chunks: 'all'
      },
      common: {
        name: 'common',
        minChunks: 2,
        chunks: 'all',
        enforce: true
      }
    }
  }
}
```

### 3. Otimização de Performance

```javascript
// Cache e otimizações
module.exports = {
  cache: {
    type: 'filesystem',
    buildDependencies: {
      config: [__filename]
    }
  },
  optimization: {
    usedExports: true,
    sideEffects: false,
    moduleIds: 'deterministic',
    runtimeChunk: 'single'
  }
};
```

### 4. Análise de Bundle

```bash
# Webpack Bundle Analyzer
npm install --save-dev webpack-bundle-analyzer

# Rollup Plugin Visualizer
npm install --save-dev rollup-plugin-visualizer

# Vite Bundle Analyzer
npm run build -- --analyze
```

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=F7DF1E&height=120&section=footer"/>