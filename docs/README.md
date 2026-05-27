# Sistema de Gestão de Projetos EAD — Firjan SENAI

> **Aplicação web de uso interno** para gerenciamento de projetos dos clientes da área de educação a distância.

---

## Visão Geral

Sistema desenvolvido em HTML5/CSS3/JavaScript puro, sem frameworks, com backend em tempo real via **Firebase Realtime Database** e autenticação via **Firebase Authentication**. Cobre o ciclo de vida completo dos projetos EAD: do cadastro até a conclusão, com rastreabilidade de etapas, cronogramas automáticos, responsáveis, prazos e histórico.

---

## Autoria e Propriedade

| Campo | Valor |
|---|---|
| **Autor** | Daniel David |
| **Instituição** | Firjan SENAI |
| **Finalidade** | Uso interno corporativo — gestão de projetos EAD |
| **Versão atual** | 3.0 |
| **Ano de criação** | 2026 |
| **Copyright** | © 2026 Firjan SENAI. Todos os direitos reservados. |

---

## Tecnologias

| Camada | Tecnologia |
|---|---|
| Frontend | HTML5, CSS3, JavaScript ES6+ (arquivo único, zero dependências locais) |
| Banco de dados | Firebase Realtime Database v10.12.0 |
| Autenticação | Firebase Authentication v10.12.0 |
| Exportação PDF | jsPDF + AutoTable (CDN) |
| Exportação Excel | SheetJS / XLSX (CDN) |
| Tipografia | Google Fonts — Plus Jakarta Sans, DM Sans |

---

## Módulos (10 views)

| Módulo | Descrição |
|---|---|
| **Dashboard** | Cards de resumo: total, em andamento, concluídos, atrasados, homologações e medições pendentes |
| **Kanban** | 14 colunas visíveis com drag-and-drop, scroll horizontal e scroll por coluna |
| **Lista de Projetos** | Tabela com filtros avançados, busca global e exportação |
| **Linha do Tempo** | Gráfico de Gantt mensal com barras de progresso por etapa |
| **KPIs** | 10 indicadores gerenciais com filtro de período |
| **Relatório de Atrasos** | Etapas fora do prazo com motivos e dias de atraso |
| **Homologações** | Controle de homologação, autorização e instalação no SIRH |
| **Medição** | Envio e confirmação de medição por projeto |
| **Carga de Trabalho** | Mapa de projetos ativos por membro da equipe |
| **Histórico** | Log de criações, edições e cancelamentos com autor e data |

---

## Kanban — Fluxo de Colunas

```
0  Aguardando Reunião Inicial
1  Aguardando Material Base
2  Fazer Cronograma          ← oculta (cronograma é automático)
3  Projeto Instrucional (PI)
4  Validação - PI
5  Fila de Espera - Produção
6  Desenvolvimento
7  Validação - Desenvolvimento
8  Revisão Textual/Tradução
9  PELD
10 Autoria Digital
11 Homologação/Instalação
12 Pré-Medição               ← botão de medição ativo
13 Upload BDOC - Files e Scorm
14 Projetos Concluídos
```

---

## Recursos EAD com Template e Cronograma Automático

| Recurso | Etapas | Dias Úteis |
|---|---|---|
| Web Rise Básico | 19 | 51 du |
| Web Rise Intermediário | 19 | 64 du |
| Web Rise Avançado | 19 | 78 du |
| Encapsulamento | 8 | 24 du |
| Produção Apostila/E-book | 14 | 52 du |
| Autoria Digital | 5 | 6 du |
| Manutenção | 11 | (sem prazo automático) |

> Recursos complementares (Web Storyline, Projeto Gráfico, Personagem, Banco de Questões, Gráficos/Imagens, Tradução) são usados como marcadores opcionais dentro dos projetos principais.

---

## Cronograma Automático

Ao selecionar um recurso com template e informar a **data de início**:
- Etapas preenchidas automaticamente com responsáveis
- Prazos calculados em cascata em **dias úteis**
- **15 feriados** considerados: 9 nacionais fixos + 4 móveis (Carnaval, Páscoa, Corpus Christi) + 2 estaduais RJ (São Sebastião, São Jorge)
- Ao alterar qualquer prazo de etapa, as etapas seguintes se ajustam em cascata automaticamente
- Campo de Prazo de Entrega preenchido automaticamente e bloqueado para edição

---

## Segurança

- Firebase Authentication obrigatório — nenhum dado carrega sem login
- Firebase Security Rules: `".read": "auth != null"` / `".write": "auth != null"`
- Credenciais não hardcoded — salvas no `localStorage` do navegador
- Meta tags: `X-Frame-Options: SAMEORIGIN`, `X-Content-Type-Options: nosniff`, `robots: noindex`

---

## Exportações

| Formato | Conteúdo |
|---|---|
| PDF — Ficha do Projeto | Dados completos, etapas, histórico de um projeto |
| PDF — Lista Geral | 4 páginas: Lista, Atrasos, Homologações, Medição |
| Excel (XLSX) | 5 abas: Projetos, Etapas, Atrasos, Homologações, Medição |
| CSV | Dados tabulares de todos os projetos |

---

## Configuração e Deploy

### Pré-requisitos
1. Projeto criado no [Firebase Console](https://console.firebase.google.com)
2. **Realtime Database** habilitado com Security Rules configuradas
3. **Authentication** habilitado com provedor E-mail/Senha
4. Usuários cadastrados em Authentication → Usuários

### Implantação
1. Hospedar `index.html` em qualquer servidor web estático
2. No primeiro acesso, preencher o modal de configuração com:
   - `apiKey`
   - `authDomain`
   - `databaseURL`
   - `projectId`
3. As configurações são salvas no `localStorage` do navegador

### Gerenciamento de usuários
```
Firebase Console → Authentication → Usuários → Adicionar usuário
```

---

## Histórico de Versões

| Versão | Data | Descrição |
|---|---|---|
| 1.0 | Mar/2026 | Lançamento: Kanban, Dashboard, KPIs, Firebase Auth, Timeline, Histórico |
| 2.0 | Mar–Abr/2026 | Templates e cronogramas automáticos (6 recursos), feriados RJ, cascata de datas, fluxos por recurso, scroll por coluna, drag horizontal, comentários, filtro por Academia, 10 KPIs, exportação XLSX/PDF |

---

## Licença

© 2026 **Firjan SENAI** — Todos os direitos reservados.
Desenvolvido por **Daniel David**.
Uso interno exclusivo. Proibida a redistribuição ou uso externo sem autorização expressa.
