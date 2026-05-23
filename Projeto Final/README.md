# 🔧 ReparoTech — Sistema de Gestão para Oficina de Manutenção de Computadores 🛠️

> [!NOTE]
> Projeto acadêmico de **documentação, modelagem e arquitetura de software** desenvolvido na disciplina **Projeto de Software** (PUC Minas, 2026/1). Este repositório reúne os artefatos de modelagem do sistema **ReparoTech** — diagramas UML, modelo de dados, contratos de operação e descrição arquitetural — **sem implementação de código-fonte funcional**. O foco é demonstrar competências de engenharia, modelagem e diagramação.

<table>
  <tr>
    <td width="800px">
      <div align="justify">
        O <b>ReparoTech</b> é um sistema concebido para organizar o ciclo completo de atendimento de uma oficina de manutenção de computadores: do cadastro de clientes e equipamentos até a entrega final, passando por diagnóstico técnico, geração de orçamentos, execução de serviços, controle de estoque de peças, registro de pagamentos e geração de relatórios gerenciais. Este projeto entrega <b>documentação completa em formato UML</b>, sob a abordagem de <i>Layered Architecture</i>, contemplando os modelos de domínio, casos de uso, contratos de operação, arquitetura, componentes, implantação, classes, sequência, comunicação, estados e dados.
      </div>
    </td>
  </tr>
</table>

---

## 🚧 Status do Projeto

[![Status](https://img.shields.io/badge/Status-Conclu%C3%ADdo-007ec6?style=for-the-badge)](#)
[![Versão](https://img.shields.io/badge/Vers%C3%A3o-1.0-007ec6?style=for-the-badge)](#)
[![Disciplina](https://img.shields.io/badge/PUC%20Minas-Projeto%20de%20Software-007ec6?style=for-the-badge)](#)
[![PlantUML](https://img.shields.io/badge/PlantUML-Diagramas-007ec6?style=for-the-badge)](https://plantuml.com/)
[![Graphviz](https://img.shields.io/badge/Graphviz-DOT-007ec6?style=for-the-badge)](https://graphviz.org/)
[![UML](https://img.shields.io/badge/UML-2.5-007ec6?style=for-the-badge)](https://www.omg.org/spec/UML/)

---

## 📚 Índice

- [Sobre o Projeto](#-sobre-o-projeto)
- [Escopo e Entregáveis](#-escopo-e-entregáveis)
- [Stack Modelada](#-stack-modelada)
- [Atores e Casos de Uso](#-atores-e-casos-de-uso)
- [Visão Arquitetural](#-visão-arquitetural)
- [Galeria de Diagramas](#-galeria-de-diagramas)
- [Modelo de Dados](#-modelo-de-dados)
- [Estrutura do Repositório](#-estrutura-do-repositório)
- [Como Visualizar e Renderizar os Diagramas](#-como-visualizar-e-renderizar-os-diagramas)
- [Autor](#-autor)
- [Agradecimentos](#-agradecimentos)
- [Licença](#-licença)

---

## 📝 Sobre o Projeto

O **ReparoTech** atende uma necessidade real de pequenas e médias oficinas de manutenção de computadores: organizar o fluxo de atendimento — do cliente que chega ao balcão até a retirada do equipamento — em um sistema único, com rastreabilidade de cada Ordem de Serviço, controle de estoque de peças e visibilidade gerencial sobre o desempenho da operação.

O projeto foi desenvolvido em nível de **documentação, modelagem, arquitetura e diagramação**. Não há código-fonte funcional: cada decisão arquitetural, cada classe, cada fluxo está formalizado em diagramas UML padrão e em descrições textuais consistentes entre si. O objetivo é demonstrar a capacidade de **modelar um sistema do mundo real com rigor de engenharia**.

### Domínio em poucas palavras

Uma oficina recebe equipamentos para reparo. Para cada um, é aberta uma **Ordem de Serviço**, que percorre 12 estados ao longo do ciclo de atendimento: diagnóstico técnico → orçamento → aprovação do cliente → execução do serviço (com possível espera por peça) → pagamento → finalização → retirada. O sistema acompanha cada transição, mantém histórico para auditoria, controla estoque e gera relatórios gerenciais.

---

## 🎯 Escopo e Entregáveis

Este projeto entrega exclusivamente **artefatos de modelagem**:

- ✅ **15 casos de uso** detalhados — com fluxos principal, alternativo e de exceção, pré e pós-condições, e regras de negócio.
- ✅ **4 contratos de operação** (estilo Larman) para as operações de fronteira centrais.
- ✅ **1 diagrama de casos de uso** com relações `<<include>>` e `<<extend>>`.
- ✅ **3 Diagramas de Sequência do Sistema (DSS)** em notação caixa-preta.
- ✅ **2 visões arquiteturais** em UML (Subsistemas + Layered/Camadas).
- ✅ **1 diagrama de componentes** com interfaces lollipop (`o--` fornece, `..>` requer).
- ✅ **1 diagrama de implantação** baseado em Docker.
- ✅ **1 diagrama de classes** com 13 classes + 5 enums, hierarquia abstrata e composição forte.
- ✅ **3 diagramas de sequência detalhados** caixa-branca (Controllers → Services → Repositories → Prisma).
- ✅ **3 diagramas de comunicação** (UC-03, UC-05 e UC-09) em notação Graphviz DOT, com numeração de Larman.
- ✅ **1 diagrama de estados** da Ordem de Serviço (12 estados, super-estado, auto-loops).
- ✅ **Esquema relacional PostgreSQL** com 11 tabelas, índices e restrições.
- ✅ **Estratégia ORM** (Prisma + Table Per Hierarchy + soft-delete + auditoria temporal).

---

## 🛠 Stack Modelada

A arquitetura modelada (não implementada) considera as seguintes tecnologias:

| Camada            | Tecnologia                         | Papel                                                                   |
| ----------------- | ---------------------------------- | ----------------------------------------------------------------------- |
| 💻 Frontend       | **Angular 21**                     | Aplicação web no navegador do Funcionário e do Gerente.                 |
| 🖥️ Backend        | **Next.js (Node.js)**              | API REST autenticada com JWT, organizada em 9 módulos de domínio.       |
| 🗄️ ORM            | **Prisma**                         | Camada de persistência com cliente _type-safe_ e migrações versionadas. |
| 💾 Banco de Dados | **PostgreSQL 16**                  | Persistência relacional com enums nativos e CHECK constraints.          |
| 🔐 Autenticação   | **JWT**                            | Token _stateless_ validado por middleware em toda rota da API.          |
| 💳 Pagamento      | **Sistema de Pagamento** (externo) | Integração síncrona via HTTPS REST para cartão e PIX.                   |
| 📧 Notificação    | **Serviço SMTP** (externo)         | Envio assíncrono de e-mails ao Cliente.                                 |
| 🐳 Deploy         | **Docker**                         | Cada subsistema (Frontend, Backend, PostgreSQL) em container próprio.   |

---

## 👥 Atores e Casos de Uso

O sistema é operado por **4 atores**:

| Ator                      | Tipo            | Papel                                                                              |
| ------------------------- | --------------- | ---------------------------------------------------------------------------------- |
| **Cliente**               | Humano externo  | Receptor passivo; entrega o equipamento e aprova/recusa orçamento via funcionário. |
| **Funcionário (Técnico)** | Humano interno  | Operador do dia-a-dia: cadastros, diagnóstico, orçamento, execução, pagamento.     |
| **Gerente**               | Humano interno  | Herda do Funcionário e adiciona operações administrativas.                         |
| **Sistema de Pagamento**  | Sistema externo | Integração para processamento de pagamentos.                                       |

São **15 casos de uso** distribuídos em duas categorias:

| Categoria                            | Casos de Uso                                                                                            |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| 🛎️ **Atendimento** (UC-01 a UC-11)   | Cadastros, abertura/diagnóstico/orçamento/aprovação/execução/pagamento/finalização da Ordem de Serviço. |
| 🛠️ **Administração** (UC-12 a UC-15) | Gestão de peças e estoque, serviços e preços, funcionários e relatórios gerenciais.                     |

---

## 🏗 Visão Arquitetural

A arquitetura é descrita por **dois diagramas UML de pacotes complementares**:

### 1. Visão de Subsistemas

Apresenta o ReparoTech como um pacote `<<subsystem>>` formado por Frontend + Backend + PostgreSQL, e suas relações com os atores e com dois sistemas externos (Sistema de Pagamento e Serviço SMTP, ambos `<<external system>>`).

### 2. Visão Lógica em Camadas

Estilo arquitetural **_Layered_ clássico**, com 4 camadas e dependência unidirecional descendente:

```
┌─────────────────────────────────────────┐
│  Apresentação   (Web App - Angular 21)  │
└──────────────┬──────────────────────────┘
               ↓ depende
┌─────────────────────────────────────────┐
│  Aplicação      (Controllers + Services)│
└──────────────┬──────────────────────────┘
               ↓ depende
┌─────────────────────────────────────────┐
│  Domínio        (Entidades + Regras)    │
└──────────────┬──────────────────────────┘
               ↓ depende
┌─────────────────────────────────────────┐
│  Infraestrutura (Prisma, Auth, Clients) │
└─────────────────────────────────────────┘
```

A escolha pelo _Layered_ clássico reflete o porte do projeto e prioriza **clareza didática** sem prejuízo à organização do código.

---

## 🖼 Galeria de Diagramas

Todos os diagramas estão em **`docs/diagramas-puml/`** (fontes em PlantUML para os UML e em Graphviz DOT para os de comunicação) e em **`docs/diagramas-img/`** (PNGs renderizados).

| #   | Diagrama                       | Arquivo PUML                                                                         | Imagem                                                 |
| --- | ------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------ |
| 01  | Casos de Uso                   | [`01-casos-de-uso.puml`](docs/diagramas-puml/01-casos-de-uso.puml)                   | [PNG](docs/diagramas-img/01-casos-de-uso.png)          |
| 02  | Sequência do Sistema (3 UCs)   | [`02-sequencia-de-sistema/`](docs/diagramas-puml/02-sequencia-de-sistema/)           | [pasta](docs/diagramas-img/02-sequencia-de-sistema/)   |
| 03  | Arquitetura (2 visões)         | [`03-arquitetura.puml`](docs/diagramas-puml/03-arquitetura.puml)                     | [PNG](docs/diagramas-img/03-arquitetura.png)           |
| 04  | Componentes                    | [`04-componentes.puml`](docs/diagramas-puml/04-componentes.puml)                     | [PNG](docs/diagramas-img/04-componentes.png)           |
| 05  | Implantação                    | [`05-implantacao.puml`](docs/diagramas-puml/05-implantacao.puml)                     | [PNG](docs/diagramas-img/05-implantacao.png)           |
| 06  | Classes                        | [`06-classes.puml`](docs/diagramas-puml/06-classes.puml)                             | [PNG](docs/diagramas-img/06-classes.png)               |
| 07  | Sequência Detalhada (3 UCs)    | [`07-sequencia-de-projeto/`](docs/diagramas-puml/07-sequencia-de-projeto/)           | [pasta](docs/diagramas-img/07-sequencia-de-projeto/)   |
| 08  | Comunicação (3 UCs, DOT)       | [`08-comunicacao/`](docs/diagramas-puml/08-comunicacao/)                             | [pasta](docs/diagramas-img/08-comunicacao/)            |
| 09  | Estados (Ordem de Serviço)     | [`09-estados-ordem-servico.puml`](docs/diagramas-puml/09-estados-ordem-servico.puml) | [PNG](docs/diagramas-img/09-estados-ordem-servico.png) |
| 10  | Modelo Entidade-Relacionamento | [`10-modelo-dados.puml`](docs/diagramas-puml/10-modelo-dados.puml)                   | [PNG](docs/diagramas-img/10-modelo-dados.png)          |

> [!NOTE]
> Os UCs **UC-03 (Abrir Ordem de Serviço)**, **UC-05 (Gerar Orçamento)** e **UC-09 (Registrar Pagamento)** foram escolhidos como casos de uso recorrentes para os diagramas comportamentais (DSS, sequência detalhada e comunicação) por representarem os fluxos mais ricos do sistema.

---

## 💾 Modelo de Dados

São **11 tabelas no PostgreSQL**, derivadas diretamente do diagrama de classes:

`usuario`, `cliente`, `equipamento`, `ordem_servico`, `diagnostico`, `orcamento`, `item_orcamento`, `servico`, `peca`, `pagamento`, `historico_status`.

### Destaques de modelagem

- 🔄 **Table Per Hierarchy (TPH)** para `Usuario` — uma única tabela `usuario` discriminada pela coluna `tipo` (`FUNCIONARIO` / `GERENTE`).
- ⛔ **CHECK constraint XOR** em `item_orcamento` — garante que cada item referencie ou um `servico_id` ou um `peca_id`, nunca ambos.
- 🗑️ **Soft-delete** via coluna `ativo` em `usuario`, `servico` e `peca`.
- 🕒 **Auditoria temporal** via colunas `data_cadastro`, `data_abertura`, `data_alteracao` com `@default(now())`.
- 📚 **Append-only** em `historico_status` — uma linha por transição de estado da Ordem de Serviço.
- 🎯 **Índices** otimizados para filtros do dashboard operacional e dos relatórios gerenciais.

---

## 📂 Estrutura do Repositório

```
.
├── 📘 README.md                                # Este arquivo
├── ⚖️ LICENSE                                  # Licença do projeto
└── 📁 docs/
    ├── 📁 diagramas-puml/                      # 🛠 Fontes (PlantUML + Graphviz DOT)
    │   ├── 01-casos-de-uso.puml
    │   ├── 03-arquitetura.puml                 # 2 blocos: visao-subsistemas + visao-camadas
    │   ├── 04-componentes.puml
    │   ├── 05-implantacao.puml
    │   ├── 06-classes.puml
    │   ├── 09-estados-ordem-servico.puml
    │   ├── 10-modelo-dados.puml
    │   ├── 📁 02-sequencia-de-sistema/         # DSS - 1 arquivo por UC
    │   │   ├── dss-uc03-abrir-ordem-servico.puml
    │   │   ├── dss-uc05-gerar-orcamento.puml
    │   │   └── dss-uc09-registrar-pagamento.puml
    │   ├── 📁 07-sequencia-de-projeto/         # Sequência detalhada - 1 arquivo por UC
    │   │   ├── seq-uc03-abrir-ordem-servico.puml
    │   │   ├── seq-uc05-gerar-orcamento.puml
    │   │   └── seq-uc09-registrar-pagamento.puml
    │   └── 📁 08-comunicacao/                  # Comunicação - notação Graphviz DOT, 1 arquivo por UC
    │       ├── 08-comunicacao-uc03.dot
    │       ├── 08-comunicacao-uc05.dot
    │       └── 08-comunicacao-uc09.dot
    └── 📁 diagramas-img/                       # 🖼 Imagens .png renderizadas
        ├── 01-casos-de-uso.png
        ├── 03-arquitetura.png
        ├── 04-componentes.png
        ├── 05-implantacao.png
        ├── 06-classes.png
        ├── 09-estados-ordem-servico.png
        ├── 10-modelo-dados.png
        ├── 📁 02-sequencia-de-sistema/         # 3 PNGs
        ├── 📁 07-sequencia-de-projeto/         # 3 PNGs
        └── 📁 08-comunicacao/                  # 3 PNGs
```

> [!NOTE]
> A pasta `diagramas-img/` espelha exatamente a estrutura de `diagramas-puml/`, com extensão `.png` no lugar de `.puml`. Isso facilita encontrar a imagem correspondente a cada fonte.

---

## 🔧 Como Visualizar e Renderizar os Diagramas

O projeto usa **duas notações**: **PlantUML** (`.puml`) para todos os diagramas UML e **Graphviz DOT** (`.dot`) para os três diagramas de comunicação. As imagens já renderizadas estão prontas em `docs/diagramas-img/`, mas se precisar **regenerar** depois de uma alteração:

### 🌐 Online (mais simples)

- **PlantUML** (`.puml`): cole o conteúdo em **[PlantUML Online](https://www.plantuml.com/plantuml/uml/)**.
- **Graphviz DOT** (`.dot`): cole o conteúdo em **[Graphviz Online](https://dreampuf.github.io/GraphvizOnline/)** ou **[Edotor](https://edotor.net/)**.

### 💻 Localmente — PlantUML CLI

**Requisitos:** Java 8+ e o `plantuml.jar` ([download oficial](https://plantuml.com/download)).

```bash
# Renderiza um diagrama específico
java -jar plantuml.jar docs/diagramas-puml/01-casos-de-uso.puml

# Renderiza todos os diagramas .puml da pasta raiz
java -jar plantuml.jar docs/diagramas-puml/*.puml

# Renderiza as pastas de sequência
java -jar plantuml.jar docs/diagramas-puml/02-sequencia-de-sistema/*.puml
java -jar plantuml.jar docs/diagramas-puml/07-sequencia-de-projeto/*.puml
```

### 💻 Localmente — Graphviz CLI (diagramas de comunicação)

**Requisitos:** Graphviz instalado (`brew install graphviz` no macOS, `apt install graphviz` no Linux, ou [download oficial](https://graphviz.org/download/)).

```bash
# Renderiza um diagrama de comunicação específico
dot -Tpng docs/diagramas-puml/08-comunicacao/08-comunicacao-uc03.dot \
    -o docs/diagramas-img/08-comunicacao/comunicacao-uc03-abrir-ordem-servico.png

# Renderiza todos os diagramas de comunicação
for f in docs/diagramas-puml/08-comunicacao/*.dot; do
  dot -Tpng "$f" -o "docs/diagramas-img/08-comunicacao/$(basename "${f%.dot}").png"
done
```

### 🧩 IDE com plugins

- **PlantUML**: [VS Code](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml), IntelliJ, Eclipse.
- **Graphviz DOT**: [Graphviz Preview](https://marketplace.visualstudio.com/items?itemName=EFanZh.graphviz-preview) ou [Graphviz Interactive Preview](https://marketplace.visualstudio.com/items?itemName=tintinweb.graphviz-interactive-preview) no VS Code.

---

## 👤 Autor

| 👤 Nome             | :octocat: GitHub                             | 📤 Contato           |
| ------------------- | -------------------------------------------- | -------------------- |
| **Vicenzo Fonseca** | [@vicenzofms](https://github.com/vicenzofms) | vicenzofms@gmail.com |

---

## 🙏 Agradecimentos

- [**Engenharia de Software PUC Minas**](https://www.instagram.com/engsoftwarepucminas/) — pelo apoio institucional, estrutura acadêmica e fomento a boas práticas de engenharia.
- **Disciplina Projeto de Software (2026/1)** — pela orientação metodológica que guiou a elaboração dos modelos e diagramas.

---

## 📄 Licença

Este projeto é distribuído sob a **[Licença MIT](https://github.com/joaopauloaramuni/laboratorio-de-desenvolvimento-de-software/blob/main/LICENSE)**.
