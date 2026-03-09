# Sistema de Gestão de Projetos EAD — Firjan SENAI

> **Aplicação web de uso interno** para gerenciamento de projetos de educação a distância.

---

## Visão Geral

Sistema single-page (SPA) desenvolvido em HTML5/CSS3/JavaScript puro, com backend em tempo real via **Firebase Realtime Database** e autenticação via **Firebase Authentication**. Permite controle completo do ciclo de vida dos projetos de EAD: do cadastro à conclusão, com rastreabilidade de etapas, responsáveis e prazos.

---

## Autoria e Propriedade

| Campo              | Valor                                   |
|--------------------|-----------------------------------------|
| **Autor**          | Daniel David                            |
| **Instituição**    | Firjan SENAI                            |
| **Finalidade**     | Uso interno corporativo                 |
| **Versão atual**   | 1.0                                     |
| **Ano de criação** | 2026                                    |
| **Copyright**      | © 2026 Firjan SENAI. Todos os direitos reservados. |

---

## Funcionalidades

### Módulos principais

- **Dashboard** — cards de resumo com totais por status (em andamento, concluídos, atrasados, aguardando, cancelados)
- **Kanban** — quadro de colunas arrastáveis com drag-and-drop de projetos entre status
- **Lista de Projetos** — tabela filtrada com busca global, filtros avançados e exportação CSV
- **Linha do Tempo (Gantt)** — visualização mensal dos projetos com barras de progresso por etapa
- **Indicadores (KPIs)** — gráficos de status, atrasos, etapas e tipos de produto
- **Relatório de Atrasos** — listagem de projetos fora do prazo com motivos registrados
- **Carga de Trabalho** — mapa de projetos ativos por membro da equipe
- **Cancelados** — histórico de projetos cancelados com justificativas
- **Histórico** — log de criações e edições com data e responsável

### Gestão de projetos (CRUD completo)

- Cadastro com nome, tipo de produto, prioridade, responsáveis, recursos, datas e descrição
- Etapas configuráveis com status individual, datas previstas/realizadas e registro de atraso com motivo
- Avanço de coluna (Kanban) com um clique
- Cancelamento com justificativa
- Reativação de projetos cancelados
- Duplicação de projetos

### Segurança e acesso

- Autenticação obrigatória via Firebase Authentication (e-mail + senha)
- Recuperação de senha por e-mail
- Tela de login institucional com validação de credenciais
- Sem senhas armazenadas no código-fonte
- Meta tags de segurança: `noindex/nofollow`, `X-Frame-Options: SAMEORIGIN`, `X-Content-Type-Options: nosniff`

---

## Tecnologias Utilizadas

| Camada         | Tecnologia                                      |
|----------------|-------------------------------------------------|
| Frontend       | HTML5, CSS3, JavaScript (ES6+)                  |
| Backend / BaaS | Firebase Realtime Database v10.12.0             |
| Autenticação   | Firebase Authentication v10.12.0                |
| Tipografia     | Google Fonts — Plus Jakarta Sans, DM Sans       |
| Deploy         | Arquivo único `index.html` (zero dependências locais) |

---

## Estrutura do Arquivo

```
index.html
├── <head>         — Meta tags, segurança, fontes
├── <style>        — CSS completo (~300 linhas, design system com variáveis)
├── <body>
│   ├── Login overlay
│   ├── Sidebar de navegação
│   ├── Topbar com busca e ações globais
│   ├── Views: kanban | projetos | timeline | kpis | atrasos | carga | cancelados | historico
│   ├── Modais: novo projeto | detalhe | cancelar | motivo de atraso
│   └── Firebase setup modal
└── <script>       — ~1800 linhas de lógica JS
    ├── Constantes e dados de configuração
    ├── Funções utilitárias (datas, badges, avatares)
    ├── Renderizadores de cada view
    ├── CRUD de projetos
    ├── Integração Firebase (SDK, escuta em tempo real, persistência)
    └── Autenticação (login, logout, recuperação de senha)
```

---

## Configuração e Deploy

### Pré-requisitos

1. Projeto criado no [Firebase Console](https://console.firebase.google.com)
2. **Realtime Database** habilitado
3. **Authentication** habilitado com provedor E-mail/Senha
4. Usuários cadastrados manualmente em Authentication → Usuários

### Implantação

1. Hospede o arquivo `index.html` em qualquer servidor web (Apache, Nginx, GitHub Pages, Firebase Hosting, etc.)
2. No primeiro acesso, um modal de configuração solicitará as credenciais do Firebase:
   - `authDomain`
   - `databaseURL`
   - `projectId`
3. As configurações são salvas no `localStorage` do navegador do usuário
4. Não é necessário servidor Node.js ou backend próprio

### Gerenciamento de usuários

Os usuários são gerenciados exclusivamente pelo **Firebase Authentication**:
```
console.firebase.google.com → Authentication → Usuários → Adicionar usuário
```

---

## Dados e Persistência

- Todos os projetos são persistidos em tempo real no Firebase Realtime Database
- A sincronização ocorre em background; a UI atualiza automaticamente via `onValue` listener
- Exportação disponível em CSV diretamente pelo sistema
- Não há dados sensíveis armazenados no código-fonte

---

## Recursos de EAD suportados

Edição Articulate, Manutenção, Gráficos/Imagens, Web Storyline, Web Rise (Básico/Intermediário/Avançado), Encapsulamento, Questionário, Tradução, Projeto Gráfico, Personagem, Apostila/E-book, Autoria Digital

---

## Licença

© 2026 **Firjan SENAI** — Todos os direitos reservados.  
Desenvolvido por **Daniel David**.  
Uso interno exclusivo. Proibida a redistribuição ou uso externo sem autorização expressa.