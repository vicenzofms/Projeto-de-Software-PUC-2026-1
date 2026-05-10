# 🏅 Sistema de Gestão das Olimpíadas (SGO) 🏆

> [!NOTE]
> Sistema de modelagem e gestão para coordenar competições olímpicas, inscrições de atletas, alocação de locais e controle de resultados.  
> Trabalho SGO | Projeto de Software | PUC Minas — 4º Período

---

## 🚧 Status do Projeto

[![Versão](https://img.shields.io/badge/Versão-v1.0.0-blue?style=for-the-badge)](https://github.com/seunome/sistema-gestao-olimpiadas/releases)
[![Licença](https://img.shields.io/badge/Licença-MIT-007ec6?style=for-the-badge&logo=opensourceinitiative)](./LICENSE)
[![PlantUML](https://img.shields.io/badge/PlantUML-UML%20Diagrams-brightgreen?style=for-the-badge)](https://plantuml.com/)
[![PUC Minas](https://img.shields.io/badge/PUC%20Minas-Engenharia%20de%20Software-blue?style=for-the-badge)](https://www.pucminas.br/)
[![Disciplina](https://img.shields.io/badge/Disciplina-Projeto%20de%20Software-orange?style=for-the-badge)](https://github.com/joaopauloaramuni)

---

## 🔗 Links Úteis

* 📖 **PlantUML:** [plantuml.com](https://plantuml.com/)
* 📖 **Guia PlantUML:** [plantuml.com/guide](https://plantuml.com/guide)
* 🛠️ **PlantUML API (Prof. Aramuni):** [Projeto PlantUML API](https://github.com/joaopauloaramuni/projeto-de-software/tree/main/PROJETOS/Python/Projeto%20PlantUML%20API)
* 🌐 **Editor Online PlantUML:** [editor.plantuml.com](https://editor.plantuml.com)

---

## 📝 Sobre o Projeto

Com a chegada das Olimpíadas, um novo sistema de gestão se torna necessário para coordenar os diferentes aspectos do evento. O **SGO — Sistema de Gestão das Olimpíadas** foi concebido para suprir essa demanda, oferecendo uma solução estruturada para:

- **Cadastrar e gerenciar competições** por modalidade, data, horário e local;
- **Inscrever atletas** de diferentes países em competições específicas, respeitando a regra de representação única por modalidade;
- **Alocar locais** de forma a evitar conflitos de horário, garantindo que um espaço abrigue apenas uma competição por vez;
- **Registrar resultados** com os classificados em 1º, 2º e 3º lugares;
- **Gerar relatórios de medalhas** consolidados por país.

O projeto é de caráter **exclusivamente de modelagem**, não exigindo implementação de código. Todos os artefatos foram produzidos em **PlantUML** e seguem a notação **UML 2.x**.

---

## 📋 Regras de Negócio

1. **Cadastro de competições:** O sistema deve permitir o cadastro de competições com nome da modalidade, data, horário, local e lista de atletas inscritos.
2. **Inscrição de atletas:** Atletas de diferentes países devem se inscrever em competições específicas. Cada atleta pode participar de várias competições, mas só pode representar um país em cada modalidade.
3. **Alocação de locais:** Os locais devem ser alocados evitando conflitos de horário. Um local só pode abrigar uma competição por vez.
4. **Controle de resultados:** Após a realização das competições, os resultados devem ser registrados, determinando o atleta vencedor e os classificados em 2º e 3º lugares.
5. **Relatórios de medalhas:** O sistema deve gerar relatórios mostrando o desempenho de cada país com base nas medalhas de ouro, prata e bronze conquistadas.

---

## 📖 Histórias de Usuário

**US01 — Cadastrar Competição**
> *Como **Organizador**, quero cadastrar uma competição informando a modalidade, data, horário e local, para que os atletas possam se inscrever e o evento seja gerenciado corretamente.*

**Critérios de aceitação:**
- O sistema deve aceitar nome da modalidade, data, horário, local e lista de atletas.
- Não deve ser possível cadastrar duas competições no mesmo local e horário.

---

**US02 — Inscrever Atleta em Competição**
> *Como **Atleta**, quero me inscrever em uma competição específica representando meu país, para que eu possa participar oficialmente do evento olímpico.*

**Critérios de aceitação:**
- Um atleta pode se inscrever em múltiplas competições.
- Um atleta só pode representar um único país por modalidade.
- O sistema deve impedir inscrições duplicadas na mesma modalidade com países distintos.

---

**US03 — Alocar Local para Competição**
> *Como **Organizador**, quero alocar um local para uma competição, para que o espaço físico esteja reservado sem conflitos de horário com outros eventos.*

**Critérios de aceitação:**
- O sistema deve verificar a disponibilidade do local na data e horário desejados.
- Um local só pode abrigar uma competição por vez.
- O sistema deve alertar o organizador em caso de conflito.

---

**US04 — Registrar Resultado de Competição**
> *Como **Organizador**, quero registrar os resultados de uma competição informando os atletas classificados em 1º, 2º e 3º lugares, para que as medalhas sejam contabilizadas corretamente.*

**Critérios de aceitação:**
- O resultado deve referenciar uma competição já cadastrada.
- Devem ser registrados obrigatoriamente os três primeiros colocados.
- Cada colocação deve gerar a contagem de medalha (ouro, prata ou bronze) para o país do atleta.

---

**US05 — Gerar Relatório de Medalhas**
> *Como **Organizador**, quero visualizar um relatório com o desempenho de cada país em termos de medalhas de ouro, prata e bronze, para acompanhar o quadro geral das Olimpíadas.*

**Critérios de aceitação:**
- O relatório deve listar todos os países com pelo menos uma medalha.
- Os países devem ser ordenados pela quantidade de ouros, depois pratas e depois bronzes.
- O relatório deve ser atualizável após cada novo resultado registrado.

---

**US06 — Consultar Competições Disponíveis**
> *Como **Atleta**, quero consultar a lista de competições disponíveis com datas, horários e locais, para planejar minhas inscrições.*

**Critérios de aceitação:**
- A listagem deve exibir modalidade, data, horário e local de cada competição.
- Deve ser possível filtrar por modalidade ou data.

---

**US07 — Cancelar Inscrição em Competição**
> *Como **Atleta**, quero cancelar minha inscrição em uma competição, caso não possa mais participar.*

**Critérios de aceitação:**
- O cancelamento só deve ser permitido antes do início da competição.
- A vaga liberada deve estar disponível para outros atletas.

---

## ✨ Funcionalidades Principais

- 🏟️ **Cadastro de Competições:** Registro de modalidade, data, horário, local e atletas inscritos.
- 🧑‍🤝‍🧑 **Inscrição de Atletas:** Participação em múltiplas competições com representação única por modalidade.
- 📍 **Alocação de Locais:** Verificação automática de conflitos de horário por local.
- 🏆 **Controle de Resultados:** Registro dos três primeiros colocados por competição.
- 📊 **Relatório de Medalhas:** Consolidação do desempenho por país (ouro, prata e bronze).
- 🔔 **Notificação de Atletas:** Confirmação automática de inscrição e resultado.

---

## 🛠 Tecnologias Utilizadas

### 🖊️ Modelagem

| Ferramenta | Finalidade |
|---|---|
| [PlantUML](https://plantuml.com/) | Geração de todos os diagramas UML |
| [PlantUML Editor Online](https://editor.plantuml.com) | Visualização e edição dos diagramas |

### 📐 Notação

| Padrão | Versão |
|---|---|
| UML (Unified Modeling Language) | 2.x |

---

## 🏗 Arquitetura e Diagramas UML

O sistema foi modelado com quatro tipos de diagramas UML, cada um responsável por uma perspectiva diferente da arquitetura do SGO.

A arquitetura segue uma organização em **pacotes de responsabilidade** bem definidos (`model.usuarios`, `model.competicoes`, `model.inscricoes`, `model.resultados`, `model.paises`, `service.relatorios`) com separação clara entre camadas de apresentação, aplicação e dados, refletida nos diagramas de componentes e implantação.

---

### 📌 Diagrama de Casos de Uso

Modela os atores **Atleta**, **Organizador** e **Sistema (Automático)** e suas interações com os casos de uso principais do SGO, incluindo relações de `<<include>>` e `<<extend>>`.

<img width="600px" src="https://github.com/vicenzofms/Projeto-de-Software-PUC-2026-1/blob/main/Trabalho-SGO/imagens/diagrama-casos-de-uso.svg"/>

---

### 📌 Diagrama de Classes e Pacotes

Apresenta a estrutura estática do sistema com as classes `Atleta`, `Organizador`, `Competicao`, `Local`, `Inscricao`, `Resultado`, `Classificacao`, `Pais`, `MedalhaContagem` e `RelatorioMedalhas`, organizadas em pacotes por responsabilidade.

<img width="600px" src="https://github.com/vicenzofms/Projeto-de-Software-PUC-2026-1/blob/main/Trabalho-SGO/imagens/diagrama-classes-pacotes.svg"/>

---

### 📌 Diagrama de Componentes

Exibe os módulos principais do sistema (Inscrições, Competições, Alocação, Resultados e Relatórios), as interfaces que cada um fornece e requer, além das dependências entre as camadas de UI, aplicação e dados.

<img width="600px" src="https://github.com/vicenzofms/Projeto-de-Software-PUC-2026-1/blob/main/Trabalho-SGO/imagens/diagrama-de-componentes.svg"/>

---

### 📌 Diagrama de Implantação

Ilustra a arquitetura física do SGO, com dispositivos dos usuários, servidor de borda (Firewall + Balanceador de Carga), servidores de aplicação primário e réplica, servidor de cache (Redis) e servidores de banco de dados primário e secundário.

<img width="600px" src="https://github.com/vicenzofms/Projeto-de-Software-PUC-2026-1/blob/main/Trabalho-SGO/imagens/diagrama-de-implantacao.svg"/>

---

## 📂 Estrutura de Pastas

```
sistema-gestao-olimpiadas/
│
├── README.md                                  # 📘 Documentação principal do projeto
│
├── imagens/                                   # 🖼️ Diagramas exportados como imagem
│   ├── diagrama-de-caso-de-uso.png
│   ├── diagrama-de-classes-pacotes.png
│   ├── diagrama-de-componentes.png
│   └── diagrama-de-implantacao.png
│
└── codigos/                                   # 📝 Arquivos-fonte PlantUML (.puml)
    ├── diagrama-de-caso-de-uso.puml
    ├── diagrama-de-classes-pacotes.puml
    ├── diagrama-de-componentes.puml
    └── diagrama-de-implantacao.puml
```

---

## 👥 Autores

| 👤 Nome | :octocat: GitHub | 💼 LinkedIn | 📤 Gmail |
|---------|-----------------|-------------|-----------|
| Vicenzo Fonseca | <div align="center"><a href="https://github.com/vicenzofms"><img src="https://joaopauloaramuni.github.io/image/github6.png" width="50px" height="50px"></a></div> | <div align="center"><a href="https://www.linkedin.com/in/vicenzo-fonseca"><img src="https://joaopauloaramuni.github.io/image/linkedin2.png" width="50px" height="50px"></a></div> | <div align="center"><a href="vicenzofms@gmail.com"><img src="https://joaopauloaramuni.github.io/image/gmail3.png" width="50px" height="50px"></a></div> |

---

## 🙏 Agradecimentos

* [**Engenharia de Software PUC Minas**](https://www.instagram.com/engsoftwarepucminas/) — Pelo apoio institucional e estrutura acadêmica.
* [**Prof. Dr. João Paulo Carneiro Aramuni**](https://github.com/joaopauloaramuni) — Pelos ensinamentos em Projeto de Software, Arquitetura e boas práticas de modelagem UML.
* [**PlantUML**](https://plantuml.com/) — Pela excelente ferramenta open-source de diagramação UML.
