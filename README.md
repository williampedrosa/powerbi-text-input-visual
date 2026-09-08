
# 🔎 Power BI Text Input Visual

> Custom Visual para Power BI desenvolvido para realizar pesquisas textuais e aplicar filtros dinamicamente em relatórios e dashboards.

![Power BI](https://img.shields.io/badge/Power%20BI-Custom%20Visual-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-18%2B-339933?style=for-the-badge&logo=node.js&logoColor=white)
![Status](https://img.shields.io/badge/Status-Em%20desenvolvimento-orange?style=for-the-badge)

---

## 📌 Sobre o projeto

O **Power BI Text Input Visual** é um Custom Visual desenvolvido para o Power BI com o objetivo de permitir que usuários realizem pesquisas textuais diretamente dentro de relatórios e dashboards.

A ideia surgiu a partir de uma necessidade prática:

> **"Procurei um visual que atendesse ao cenário que precisava, mas não encontrei. Então desenvolvi o meu próprio."**

O visual utiliza a **Power BI Visuals API** para aplicar filtros dinamicamente ao modelo de dados a partir dos valores informados pelo usuário.

Além da pesquisa convencional, o componente possui recursos para validação de entrada, utilização de expressões regulares (Regex), tratamento de diferentes formatos do mesmo valor e configuração de pesquisa obrigatória.

---

## 🎯 Objetivo

Criar uma solução simples e flexível para permitir que usuários pesquisem informações em relatórios Power BI sem depender exclusivamente dos filtros e segmentações tradicionais.

O visual foi pensado principalmente para cenários onde existe a necessidade de:

- Pesquisa textual;
- Localização rápida de registros;
- Filtros personalizados;
- Pesquisa em diferentes colunas;
- Validação do formato informado;
- Tratamento de identificadores;
- Pesquisa por diferentes representações do mesmo valor;
- Controle de preenchimento obrigatório.

---

## 🚀 Funcionalidades

### 🔎 Pesquisa textual

Permite que o usuário informe um ou mais termos para realizar uma pesquisa.

Exemplo:

```text
12345
````

Ou múltiplos termos:

```text
12345 67890 54321
```

Os termos são processados e utilizados para aplicação dos filtros no Power BI.

---

### 🧩 Filtro em múltiplas colunas

O visual permite definir uma ou mais colunas do modelo de dados como destino dos filtros.

As colunas são identificadas através de uma **Data Role**:

```text
colunaFiltro
```

Isso permite utilizar o mesmo visual em diferentes cenários e modelos de dados.

---

### ⚙️ Suporte a Regex

É possível configurar uma expressão regular para validar os valores informados pelo usuário.

Exemplo:

```regex
^\d{5}-\d{4}$
```

Caso o valor informado não esteja de acordo com o padrão definido, o visual apresenta uma mensagem de validação.

```text
Valor fora do padrão esperado.
```

---

### 🔄 Tratamento de diferentes formatos

Um dos recursos desenvolvidos é a possibilidade de tratar diferentes representações do mesmo valor.

Por exemplo, considerando:

```text
123.456/789-00
```

O visual pode gerar diferentes representações para realizar a busca:

```text
123.456/789-00
123/456/789/00
123.456.789.00
123-456-789-00
```

Isso é especialmente útil quando os dados armazenados no modelo podem possuir diferentes padrões de formatação.

---

### 🔐 Busca obrigatória

O visual possui uma configuração chamada:

```text
Busca obrigatória
```

Quando habilitada, o usuário precisa informar um valor de pesquisa.

Enquanto não houver uma entrada válida, o visual pode aplicar um filtro específico para impedir que todo o conjunto de dados seja apresentado.

Mensagem exibida:

```text
Preenchimento obrigatório.
```

---

### ❌ Limpeza de filtros

O botão de limpeza permite remover o filtro aplicado pelo visual.

Isso permite ao usuário retornar ao estado inicial da análise de forma rápida.

---

### ⌨️ Atalho pelo teclado

A pesquisa pode ser executada pressionando:

```text
Enter
```

Além do botão de pesquisa disponível na interface.

---

### 🚨 Validação e mensagens

O visual possui tratamento para diferentes situações, incluindo:

* Entrada vazia;
* Regex inválida;
* Valor fora do padrão esperado;
* Busca obrigatória;
* Limpeza dos filtros.

Exemplo:

```text
Valor fora do padrão esperado.
```

---

## 🏗️ Arquitetura

O visual utiliza a arquitetura de Custom Visuals do Power BI.

Fluxo simplificado:

```text
┌───────────────────────┐
│       Usuário         │
│                       │
│  Digita termo de      │
│      pesquisa         │
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│   Text Input Visual   │
│                       │
│  Validação / Regex    │
│  Tratamento do texto  │
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│   Power BI Visuals    │
│         API           │
│                       │
│  applyJsonFilter()    │
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│     Modelo Power BI   │
│                       │
│   Aplicação do filtro │
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│       Relatório       │
│                       │
│ Dados filtrados       │
└───────────────────────┘
```

---

# 🛠️ Tecnologias utilizadas

## Linguagem

* TypeScript

## Plataforma

* Microsoft Power BI

## API

* Power BI Visuals API

## Desenvolvimento

* Node.js
* npm
* Webpack
* ESLint
* TypeScript

## Controle de versão

* Git
* GitHub

---

# 📂 Estrutura do projeto

A estrutura principal do projeto segue o padrão utilizado no desenvolvimento de Power BI Custom Visuals.

```text
powerbi-text-input-visual/
│
├── src/
│   └── visual.ts
│
├── style/
│   └── visual.less
│
├── capabilities.json
├── pbiviz.json
├── package.json
├── package-lock.json
├── tsconfig.json
├── eslint.config.mjs
├── .gitignore
└── README.md
```

> A estrutura pode variar de acordo com a versão do Power BI Visual Tools utilizada no projeto.

---

# ⚙️ Configuração do Visual

O visual possui uma Data Role chamada:

```text
colunaFiltro
```

Essa propriedade representa as colunas que poderão receber os filtros gerados pelo componente.

No Power BI:

```text
Coluna para filtrar
        ↓
colunaFiltro
```

---

# 🔧 Configurações disponíveis

O visual disponibiliza uma seção de configurações:

## Configurações de Busca

### Regex da busca

Permite definir uma expressão regular utilizada para validar os termos digitados.

Exemplo:

```regex
^\d{11}$
```

Esse padrão permite validar um valor composto por exatamente 11 números.

---

### Busca obrigatória

Tipo:

```text
Boolean
```

Valores:

```text
Ativado
Desativado
```

Quando ativada, o visual exige o preenchimento da pesquisa antes de permitir a utilização normal do filtro.

---

# 🔍 Como funciona a pesquisa

Quando o usuário realiza uma pesquisa, o visual:

1. Captura o valor digitado;
2. Remove espaços desnecessários;
3. Divide múltiplos termos;
4. Valida os termos através da Regex, quando configurada;
5. Gera as variações necessárias do valor;
6. Remove valores duplicados;
7. Identifica as colunas configuradas;
8. Constrói o filtro;
9. Envia o filtro para o Power BI através da API.

A aplicação do filtro é realizada utilizando:

```typescript
this.host.applyJsonFilter()
```

Com filtros avançados utilizando condições:

```typescript
operator: "Contains"
```

e lógica:

```typescript
logicalOperator: "Or"
```

---

# 💻 Exemplo de utilização

Imagine uma tabela:

```text
Clientes
--------------------------------
CPF
Nome
Cidade
```

E o usuário informa:

```text
12345678900
```

O visual pode utilizar o valor para gerar um filtro sobre:

```text
Clientes[CPF]
```

O Power BI recebe dinamicamente o filtro e atualiza os demais elementos do relatório relacionados ao contexto filtrado.

---

# 🧪 Exemplo com Regex

Configuração:

```regex
^\d{11}$
```

Entrada válida:

```text
12345678900
```

Resultado:

```text
Pesquisa executada
```

Entrada inválida:

```text
123456
```

Resultado:

```text
Valor fora do padrão esperado.
```

---

# 🧑‍💻 Desenvolvimento

## Pré-requisitos

Para desenvolver ou modificar o projeto, recomenda-se possuir:

* Node.js 18+
* npm
* Visual Studio Code
* Power BI Desktop
* Power BI Visual Tools

---

## Instalação

Clone o repositório:

```bash
git clone https://github.com/williampedrosa/powerbi-text-input-visual.git
```

Entre no diretório:

```bash
cd powerbi-text-input-visual
```

Instale as dependências:

```bash
npm install
```

---

# ▶️ Executando o projeto

Para iniciar o ambiente de desenvolvimento:

```bash
npm start
```

ou utilize o comando definido no `package.json` do projeto.

Durante o desenvolvimento, o visual pode ser testado utilizando o ambiente de desenvolvimento disponibilizado pelas ferramentas de Custom Visual do Power BI.

---

# 📦 Gerando o pacote do visual

Para gerar o pacote `.pbiviz`, utilize:

```bash
pbiviz package
```

O pacote gerado poderá ser importado no Power BI Desktop ou utilizado conforme as políticas de implantação da organização.

---

# 📊 Integração com Power BI

O projeto utiliza a API de extensibilidade do Power BI para interagir com o relatório.

Uma das principais funcionalidades utilizadas é:

```typescript
this.host.applyJsonFilter()
```

Essa API permite que o visual aplique filtros diretamente ao contexto do relatório.

Exemplo simplificado:

```typescript
this.host.applyJsonFilter(
    filter,
    "general",
    "filter",
    powerbi.FilterAction.merge
);
```

Para remover o filtro:

```typescript
this.host.applyJsonFilter(
    null,
    "general",
    "filter",
    powerbi.FilterAction.remove
);
```

---

# 🧠 Conceitos utilizados

Durante o desenvolvimento foram aplicados conceitos de:

* TypeScript;
* Programação orientada a objetos;
* Manipulação do DOM;
* Eventos de interface;
* Expressões regulares;
* Validação de dados;
* Tratamento de exceções;
* APIs;
* JSON;
* Filtros avançados do Power BI;
* Power BI Visuals API;
* Data Roles;
* DataView;
* Metadados do Power BI;
* Desenvolvimento de componentes personalizados;
* Integração entre aplicação e modelo de dados.

---

# 🎯 Motivação do projeto

Este projeto nasceu de uma necessidade real de desenvolvimento.

Em vez de utilizar somente os recursos disponíveis no Power BI, a abordagem adotada foi criar uma solução personalizada.

O projeto representa uma forma de trabalho baseada em:

```text
Problema
   ↓
Análise da necessidade
   ↓
Pesquisa de soluções existentes
   ↓
Identificação das limitações
   ↓
Desenvolvimento
   ↓
Integração com Power BI
   ↓
Testes
   ↓
Solução personalizada
```

---

# 🚧 Roadmap

Algumas funcionalidades que podem ser consideradas para versões futuras:

* [ ] Melhorias de interface;
* [ ] Personalização completa de cores;
* [ ] Personalização de tamanho dos botões;
* [ ] Suporte a diferentes operadores de filtro;
* [ ] Configuração do comportamento de busca;
* [ ] Mais opções de tratamento de texto;
* [ ] Melhor feedback visual durante a pesquisa;
* [ ] Histórico de pesquisas;
* [ ] Documentação de exemplos avançados;
* [ ] Melhorias de acessibilidade;
* [ ] Testes automatizados;
* [ ] Publicação de versões/releases.

---

# 🔒 Privacidade e segurança

O visual não possui privilégios adicionais definidos no manifesto:

```json
"privileges": []
```

A aplicação dos filtros ocorre através das APIs disponibilizadas pelo próprio ambiente de Custom Visuals do Power BI.

O visual não foi desenvolvido para coletar ou armazenar dados do usuário fora do contexto do relatório.

---

# 👨‍💻 Autor

**William Pedrosa dos Santos**

Desenvolvedor / Engenheiro de Dados

Atuação com:

* Python
* SQL
* Power BI
* DAX
* ETL
* Engenharia de Dados
* APIs
* TypeScript
* Desenvolvimento de soluções personalizadas
* Automação
* Inteligência Artificial

---

E esse projeto é **ótimo para sustentar esse posicionamento**, porque demonstra uma coisa muito mais interessante do que simplesmente saber usar Power BI: **você criou uma extensão da própria ferramenta para resolver um problema real.**
