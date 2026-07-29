# 💡 Lúmen — Planner de Estudos e Produtividade Acadêmica

Lúmen é uma plataforma web acadêmica focada na organização inteligente de estudos e produtividade pessoal. Com uma interface SaaS minimalista e fluxo dinâmico, o sistema une planejamento semanal (Planner), gestão de atividades com indicadores de prioridade e prazo, e técnica Pomodoro integrada para que estudantes alcancem maior consistência e controle sobre sua rotina diária.

---

## 📋 Visão Geral

Desenvolvido como um MVP acadêmico premium e de alta fidelidade visual, o **Lúmen** nasceu para sanar a dispersão e falta de organização que muitos estudantes enfrentam em seu dia a dia. Ao combinar a visualização ágil das matérias com um cronograma semanal fluido e sessões integradas de foco, o aplicativo atua como um companheiro completo para:
- Planejamento visual de tempo e matérias.
- Monitoramento de prazos e urgências acadêmicas.
- Gestão ativa de foco, auxiliando no combate à procrastinação.

Seu público-alvo principal é composto por estudantes universitários, secundaristas e autodidatas que buscam uma solução elegante, limpa e centralizada para gerenciar sua rotina de aprendizado.

---

## ✨ Funcionalidades Principais

O Lúmen é composto pelas seguintes funcionalidades funcionais e finalizadas:

1. **Onboarding Inicial (Welcome Page)**: Fluxo interativo de boas-vindas estruturado em 3 etapas que apresenta a proposta de valor do Lúmen antes do login.
2. **Autenticação Segura**: Telas de login e cadastro totalmente integradas com JWT e encriptação de senha pelo back-end.
3. **Dashboard Consolidado**: Painel central premium com indicadores KPIs de progresso (atividades pendentes, tarefas agendadas para o dia e horas semanais de foco), atalhos rápidos e pré-visualização integrada da semana atual.
4. **Gerenciamento de Matérias**: Cadastro de disciplinas com personalização de cores e categorias visuais.
5. **Gerenciamento de Atividades**: Listagem completa de tarefas acadêmicas com filtros por status (pendentes/concluídas), prioridade (Alta, Média, Baixa) e matéria, além de indicadores visuais de atrasos e prazos finais.
6. **Planner Semanal**: Grade visual de 7 dias (Dom a Sáb) para alocar blocos de estudo vinculados às matérias e planejar a semana atual com facilidade.
7. **Timer Pomodoro**: Temporizador de foco integrado, estruturado com contagem regressiva e suporte para rastrear tempos de foco dedicados a matérias cadastradas.
8. **Modal Global de Criação**: Atalho rápido (botão "+") acessível de qualquer tela para criar novas atividades, matérias e blocos no planner de forma instantânea.
9. **Navegação Responsiva**: Experiência visual mobile refinada (utilizando barra de navegação inferior estilo app nativo) e barra lateral com gradiente fluido no desktop.

---

## 🛠️ Tecnologias e Stack

O ecossistema do Lúmen é estruturado em um monorepositório gerenciado via workspaces do **pnpm**, utilizando as seguintes stacks:

### Frontend (Client)
- **React 19** & **TypeScript**: Construção de componentes fortemente tipados e ciclo de vida otimizado.
- **Vite**: Ferramenta de build e runtime extremamente rápido.
- **React Router DOM 7**: Controle de roteamento declarativo e rotas protegidas por autenticação.
- **Tailwind CSS v4**: Estilização moderna e responsiva utilizando o motor nativo integrado ao Vite.

### Backend (Server)
- **Node.js** & **Express v5**: API RESTful robusta e modular.
- **Prisma ORM**: Gerenciador de banco de dados para consultas tipadas e migrações ágeis.
- **PostgreSQL**: Banco de dados relacional para persistência de dados.
- **JWT (JSON Web Tokens)**: Mecanismo de autenticação sem estado.
- **BcryptJS**: Encriptação e hashing seguro de senhas.

---

## 📁 Estrutura do Projeto

O projeto adota uma estrutura modular baseada em monorepositório:

```text
senac-lumen/
├── client/                  # Aplicação Frontend
│   ├── src/
│   │   ├── components/      # Componentes reutilizáveis (Card, Modais, Proteção de Rotas)
│   │   ├── hooks/           # Custom hooks do React (useAuth, useActivities, useSubjects, etc.)
│   │   ├── pages/           # Telas da aplicação (Dashboard, Planner, Pomodoro, Auth, etc.)
│   │   ├── types/           # Declarações de tipos e interfaces TypeScript
│   │   ├── App.tsx          # Definição das rotas e inicialização do React
│   │   └── main.tsx         # Ponto de entrada da aplicação cliente
│   ├── package.json
│   └── vite.config.ts
│
├── server/                  # Aplicação Backend (API REST)
│   ├── prisma/              # Schema do banco de dados (schema.prisma) e migrações
│   ├── src/
│   │   ├── controllers/     # Lógica das requisições e regras de validação (Auth, Activities, etc.)
│   │   ├── middlewares/     # Middlewares Express (validação de JWT, tratamento de erros)
│   │   ├── routes/          # Definições de endpoints da API
│   │   ├── lib/             # Instanciação compartilhada de bibliotecas (Prisma client)
│   │   └── server.ts        # Inicialização do servidor Express
│   └── package.json
│
├── package.json             # Definição do workspace pnpm e scripts centrais
└── pnpm-workspace.yaml      # Configuração de escopo dos pacotes do monorepositório
```

---

## 🚀 Como Executar Localmente

### Pré-requisitos
- Node.js (v18 ou superior)
- pnpm (instalador de pacotes global recomendado)
- Banco de dados PostgreSQL rodando localmente ou remotamente.

### Passo 1: Clonar o Repositório
```bash
git clone https://github.com/seu-usuario/senac-lumen.git
cd senac-lumen
```

### Passo 2: Instalar as Dependências
Instale todas as dependências do cliente e do servidor de forma centralizada:
```bash
pnpm install
```

### Passo 3: Configurar as Variáveis de Ambiente
Crie um arquivo `.env` na raiz do diretório `server/` (ou na raiz global se desejar) baseando-se no arquivo `.env.example`:
```bash
cp .env.example server/.env
```
Edite o arquivo `server/.env` e ajuste as credenciais de acesso ao seu banco de dados e a chave de criptografia.

### Passo 4: Rodar as Migrações do Banco de Dados
A partir do diretório raiz, gere o client do Prisma e sincronize a estrutura do banco:
```bash
pnpm --filter server prisma db push
```

### Passo 5: Executar o Projeto em Desenvolvimento
Inicie o cliente e o servidor simultaneamente usando o comando central:
```bash
pnpm dev
```
- A API do backend estará rodando em: `http://localhost:3333`
- A aplicação frontend estará disponível em: `http://localhost:5173`

### Passo 6: Compilação de Produção (Build)
Para compilar e empacotar a aplicação cliente para produção:
```bash
pnpm --filter client build
```

---

## ⚙️ Variáveis de Ambiente

As seguintes variáveis de ambiente devem ser configuradas no arquivo `.env` localizado na pasta `/server`:

| Variável | Descrição | Exemplo / Padrão |
| :--- | :--- | :--- |
| `DATABASE_URL` | URL de conexão com o banco de dados PostgreSQL | `postgresql://postgres:senha@localhost:5432/lumen?schema=public` |
| `JWT_SECRET` | String arbitrária secreta usada para assinar os tokens JWT | `sua_chave_secreta_super_forte_aqui` |
| `PORT` | Porta onde a API HTTP Express estará escutando | `3333` |
| `CORS_ORIGIN` | Origem autorizada a consumir a API (URL do front-end) | `http://localhost:5173` |

---

## 📸 Capturas de Tela e Demonstração

*(Abaixo estão os placeholders reservados para anexar capturas da interface gráfica do Lúmen)*

| Tela de Onboarding | Dashboard Principal |
| :---: | :---: |
| ![Onboarding Placeholder](https://via.placeholder.com/600x400.png?text=Onboarding+Lumen) | ![Dashboard Placeholder](https://via.placeholder.com/600x400.png?text=Dashboard+Lumen) |

| Planner Semanal | Timer Pomodoro |
| :---: | :---: |
| ![Planner Placeholder](https://via.placeholder.com/600x400.png?text=Planner+Lumen) | ![Pomodoro Placeholder](https://via.placeholder.com/600x400.png?text=Pomodoro+Lumen) |

---

## 🎓 Aprendizados e Objetivos Acadêmicos

Este projeto foi construído sob um escopo pedagógico avançado de desenvolvimento de software full-stack, consolidando os seguintes tópicos técnicos:
- **Modelagem de Dados**: Estruturação de relacionamentos um-para-muitos (`User` ➔ `Subjects`, `Subjects` ➔ `Activities`) usando o Prisma ORM e PostgreSQL.
- **Autenticação Segura**: Implementação prática de autenticação por tokens (JWT), cookies/headers, e segurança criptográfica usando hash Bcrypt.
- **Desenvolvimento Componentizado**: Criação de interfaces dinâmicas, limpas e reutilizáveis em React e TypeScript, focando no desacoplamento de estado e regras visuais.
- **UX/UI Moderno**: Experiência visual polida com base nos padrões do Figma de referência, com foco em responsividade multiplataforma (mobile-first para navegação e desktop para visualização de tabelas estruturadas).

---

## 🚀 Status do Projeto

O projeto encontra-se **Funcional e Finalizado** como MVP para a entrega acadêmica do segundo semestre do curso de tecnologia da informação/desenvolvimento de software do SENAC.

---

## 👥 Autores

- **João Watanabe** — [GitHub](https://github.com/joaowatanabe)
- **Guilherme Lambrecht** — [GitHub](https://github.com/GuilhermeLambrecht)

