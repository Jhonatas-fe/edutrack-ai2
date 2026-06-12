<div align="center">

# 📚 EduTrack AI

**Portal Acadêmico Inteligente para Gestão de Desempenho Estudantil**

[![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python&logoColor=white)](https://python.org)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.x-FF4B4B?logo=streamlit&logoColor=white)](https://streamlit.io)
[![Xano](https://img.shields.io/badge/Backend-Xano-6366F1?logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PC9zdmc+)](https://xano.com)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

> Desenvolvido como projeto final da disciplina **Innovation Lab: Advanced No/Low Code** — IMPACTA Tecnologia · 2026

</div>

---

## 🌐 Acesso Online

O sistema está disponível publicamente — não é necessário instalar nada:

**🔗 [(https://edutrack-ai2grupo4.streamlit.app/)]**

> Acesse diretamente pelo navegador, crie uma conta e comece a usar.

---

## 🎯 Sobre o Projeto

O **EduTrack AI** é uma plataforma web de gestão acadêmica desenvolvida para auxiliar estudantes no acompanhamento do seu desempenho ao longo do semestre. O sistema permite cadastrar professores, disciplinas e atividades, visualizar métricas de desempenho em tempo real, definir metas por matéria e gerar relatórios completos em PDF.

O projeto foi construído com uma stack de **No/Low Code** moderna, integrando Python + Streamlit no frontend com Xano como backend sem servidor, demonstrando como é possível criar aplicações completas e funcionais sem infraestrutura complexa.

---

## 🚀 Funcionalidades

### 📊 Dashboard
- Métricas em tempo real: disciplinas, atividades, média geral, melhor e pior nota
- Contador de atividades por disciplina com média e status
- 4 gráficos interativos com Plotly:
  - Notas por atividade
  - Média por disciplina (barras horizontais coloridas por faixa)
  - Evolução temporal das notas
  - Radar 360° de desempenho multidimensional
- Alertas automáticos de tarefas com prazo próximo
- Geração de relatório PDF diretamente do dashboard

### 👨‍🏫 Professores
- Cards visuais com avatar, disciplinas vinculadas e média geral
- CRUD completo com confirmação de exclusão
- **Deleção em cascata**: ao remover professor, suas disciplinas, tarefas, metas e anotações são removidas automaticamente

### 📖 Disciplinas
- Vinculação a professores
- Calculadora de média necessária
- Deleção em cascata de dados relacionados

### ✅ Tarefas e Notas
- Registro de atividades com nota, prioridade e prazo de entrega
- Filtros por disciplina, status e prioridade
- Busca por nome de atividade
- Ordenação por prazo, nota, prioridade ou nome
- Checkbox de conclusão com salvamento no banco de dados
- Exportação para **Excel** com aba Dashboard de métricas e gráfico

### 📅 Calendário
- Grade mensal em português com pontinhos coloridos por tipo de evento
- Tipos: 📝 Prova · 📌 Entrega · 🎯 Apresentação · 📖 Outro
- Lista de próximos eventos com countdown de dias
- CRUD completo de eventos

### 🗂️ Meu Espaço
- **Metas**: defina uma meta de média por disciplina com barra de progresso
- **Anotações**: salve resumos e links por disciplina
- **Histórico**: linha do tempo das atividades concluídas com badges por nota

### 👤 Perfil
- Edição de nome, curso, instituição e semestre
- Dados persistidos no banco de dados (sobrevivem ao logout)
- Progresso por disciplina com barras coloridas

### 📄 Relatório PDF
- Gerado com ReportLab diretamente no browser
- Inclui: métricas, tabela de notas, agenda, metas e anotações
- Design profissional com cores por faixa de nota

---

## 🛠️ Stack Tecnológica

| Camada | Tecnologia | Uso |
|---|---|---|
| **Frontend** | Python + Streamlit | Interface web interativa |
| **Gráficos** | Plotly Express | Visualizações interativas |
| **Dados** | Pandas | Manipulação e análise de dados |
| **Backend** | Xano (No-Code) | API REST + banco de dados PostgreSQL |
| **PDF** | ReportLab | Geração de relatórios |
| **Excel** | OpenPyXL | Exportação de planilhas |
| **Auth** | JWT via Xano | Autenticação segura por token |

---

## 🏗️ Arquitetura

```
┌─────────────────────────────────────────────┐
│              EduTrack AI (Frontend)          │
│              Python + Streamlit              │
│                                             │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  │
│  │Dashboard │  │  CRUD    │  │Relatórios│  │
│  │ Plotly   │  │Professores│  │PDF/Excel │  │
│  │  Radar   │  │Disciplinas│  │ReportLab │  │
│  │  Charts  │  │ Tarefas  │  │OpenPyXL  │  │
│  └────┬─────┘  └────┬─────┘  └──────────┘  │
└───────┼─────────────┼────────────────────────┘
        │  HTTP REST  │  JWT Auth
        ▼             ▼
┌─────────────────────────────────────────────┐
│              Xano (Backend)                  │
│         API REST + PostgreSQL                │
│                                             │
│  users │ professores │ disciplinas          │
│  tarefas │ eventos │ metas │ anotacoes      │
└─────────────────────────────────────────────┘
```

---

## 📂 Estrutura do Projeto

```
edutrack-ai/
│
├── edutrack_xano.py      # Arquivo principal — toda a aplicação
├── requirements.txt      # Dependências Python
├── .streamlit/
│   ├── config.toml       # Configuração do Streamlit (tema, porta)
│   └── secrets.toml      # Credenciais da API (não commitado)
└── README.md             # Este arquivo
```

---

## ⚙️ Como Executar Localmente

### Pré-requisitos
- Python 3.12+
- Conta no [Xano](https://xano.com)

### Instalação

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/edutrack-ai.git
cd edutrack-ai

# Crie e ative o ambiente virtual
python -m venv .venv
source .venv/bin/activate  # Linux/Mac
.venv\Scripts\activate     # Windows

# Instale as dependências
pip install -r requirements.txt
```

### Configuração

Crie o arquivo `.streamlit/secrets.toml`:

```toml
[xano]
base_url = "https://sua-url.xano.io/api:seu-grupo"
```

### Execução

```bash
streamlit run edutrack_xano.py
```

Acesse `http://localhost:8501`

---

## 📦 Dependências

```txt
streamlit
requests
pandas
plotly
reportlab
openpyxl
```

---

## 🗄️ Banco de Dados (Xano)

| Tabela | Campos principais |
|---|---|
| `user` | id, name, email, password, curso, instituicao, semestre, foto |
| `professores` | id, nome, email, user_id |
| `disciplinas` | id, nome, prof_id, user_id |
| `tarefas` | id, nome, disc_id, nota, concluida, prioridade, prazo, user_id |
| `eventos` | id, nome, data_evento, tipo, user_id |
| `metas` | id, disc_id, valor_meta, user_id |
| `anotacoes` | id, disc_id, texto, user_id |

---

## 🔐 Segurança

- Autenticação via **JWT** (JSON Web Token) gerenciado pelo Xano
- Todos os endpoints do Xano filtram dados por `user_id` — cada usuário vê **apenas seus próprios dados**
- Token salvo em `st.query_params` para persistir sessão no refresh
- Senhas hasheadas pelo Xano (não armazenadas em texto plano)

---

## 🎓 Contexto Acadêmico

Este projeto foi desenvolvido como trabalho final do curso **Innovation Lab: Advanced No/Low Code** na **IMPACTA Tecnologia**, turma 2026.

**Características diferenciais em relação ao básico proposto:**
- Relatório PDF completo gerado no browser
- Exportação Excel com aba Dashboard e gráfico embutido
- Deleção em cascata entre entidades relacionadas
- Radar 360° de desempenho multidimensional
- Persistência de sessão via URL token
- Cache isolado por usuário
- Calendário visual com pontinhos coloridos
- Busca e ordenação avançada nas tarefas

---

## 👥 Equipe

- Lael Gonsalves Rodrigues Junior
- Jhonatas Felipe de Jesus Mendes
- Gabriel Vitor Martins Loureiro Castelo Branco
- Vinícius de Oliveira Cardoso

---

<div align="center">

Desenvolvido com ❤️ para a disciplina Innovation Lab · IMPACTA 2026

</div>
