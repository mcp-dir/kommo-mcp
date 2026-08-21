# Kommo

### Kommo para Claude, ChatGPT e agentes de IA

Kommo CRM (ex-amoCRM), o CRM de vendas por conversa (WhatsApp, Instagram, Telegram) usado por PMEs e agências. Leia e escreva leads, contatos, empresas, tarefas, notas, funis, tags, campos personalizados, usuários, eventos, conversas e catálogos pela API v4 oficial. Você informa o subdomínio da sua conta e um Token de Longa Duração e a plataforma opera na sua conta. Inclui uma ferramenta de chamada crua para qualquer endpoint da API.

- 📊 **42 ferramentas**
- ✏️ **Leitura e escrita**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `Kommo` e **URL** `https://api.mcp.ai/p_kommo`.

### Cursor

[➕ Instalar Kommo no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=kommo&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9rb21tbyJ9)

### VS Code (Copilot Chat)

[➕ Instalar Kommo no VS Code](vscode:mcp/install?name=kommo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_kommo%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_kommo
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Liste os leads no funil de vendas que estão parados há mais de 7 dias
Crie um lead novo para a Maria com telefone e uma tarefa de retorno amanhã
Mostre as conversas abertas no inbox e quem é o responsável
```

---

## 42 ferramentas disponíveis

| Tool | Descrição |
|---|---|
| `kommo_list_accounts` | Lista as contas Kommo conectadas a este install (id/subdomínio, label). |
| `kommo_account` | Dados da conta Kommo conectada (id, nome, subdomínio, moeda, fuso, e opcionalmente usuários/campos/pipelines via `with`). |
| `kommo_leads_list` | Leads do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: list] Bulk support:… |
| `kommo_leads_get` | Leads do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: get] Bulk support:… |
| `kommo_leads_create` | Leads do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: create] Bulk suppor… |
| `kommo_leads_update` | Leads do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: update] Bulk suppor… |
| `kommo_contacts_list` | Contacts do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: list] Bulk suppo… |
| `kommo_contacts_get` | Contacts do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: get] Bulk suppor… |
| `kommo_contacts_create` | Contacts do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: create] Bulk sup… |
| `kommo_contacts_update` | Contacts do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: update] Bulk sup… |
| `kommo_companies_list` | Companies do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: list] Bulk supp… |
| `kommo_companies_get` | Companies do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: get] Bulk suppo… |
| `kommo_companies_create` | Companies do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: create] Bulk su… |
| `kommo_companies_update` | Companies do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: update] Bulk su… |
| `kommo_tasks_list` | Tasks do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: list] Bulk support:… |
| `kommo_tasks_get` | Tasks do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: get] Bulk support:… |
| `kommo_tasks_create` | Tasks do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: create] Bulk suppor… |
| `kommo_tasks_update` | Tasks do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: update] Bulk suppor… |
| `kommo_customers_list` | Clientes (módulo de vendas recorrentes/RFM do Kommo). |
| `kommo_customers_get` | Clientes (módulo de vendas recorrentes/RFM do Kommo). |
| `kommo_customers_create` | Clientes (módulo de vendas recorrentes/RFM do Kommo). |
| `kommo_customers_update` | Clientes (módulo de vendas recorrentes/RFM do Kommo). |
| `kommo_notes_list` | Notas de uma entidade. action: list (todas as notas do tipo de entidade), list_by_entity (notas de 1 registro), create (adiciona nota; `data` = JSON). Tipos comuns: common, call_in, call_out, sms_in/out, attachment. [… |
| `kommo_notes_list_by_entity` | Notas de uma entidade. action: list (todas as notas do tipo de entidade), list_by_entity (notas de 1 registro), create (adiciona nota; `data` = JSON). Tipos comuns: common, call_in, call_out, sms_in/out, attachment. [… |
| `kommo_notes_create` | Notas de uma entidade. action: list (todas as notas do tipo de entidade), list_by_entity (notas de 1 registro), create (adiciona nota; `data` = JSON). Tipos comuns: common, call_in, call_out, sms_in/out, attachment. [… |
| `kommo_tags_list` | Tags de um tipo de entidade. action: list (com busca) | create (cria tags; `data` = JSON, ex.: [{"name":"vip"}]). [Flattened action: list] |
| `kommo_tags_create` | Tags de um tipo de entidade. action: list (com busca) | create (cria tags; `data` = JSON, ex.: [{"name":"vip"}]). [Flattened action: create] |
| `kommo_pipelines_list` | Funis (pipelines) e seus estágios. |
| `kommo_pipelines_get` | Funis (pipelines) e seus estágios. |
| `kommo_pipelines_statuses` | Funis (pipelines) e seus estágios. |
| `kommo_custom_fields` | Campos personalizados de um tipo de entidade (leads/contacts/companies/customers). |
| `kommo_users_list` | Usuários da conta. action: list | get (por id). `with`=role,group para incluir permissões/grupos. [Flattened action: list] Bulk support: accepts ids for batched execution. |
| `kommo_users_get` | Usuários da conta. action: list | get (por id). `with`=role,group para incluir permissões/grupos. [Flattened action: get] Bulk support: accepts ids for batched execution. |
| `kommo_events` | Eventos/atividades da conta (mudança de estágio, criação, etc.). |
| `kommo_talks_list` | Conversas (talks) do inbox unificado. |
| `kommo_talks_get` | Conversas (talks) do inbox unificado. |
| `kommo_catalogs_list` | Catálogos (listas: produtos, etc.). |
| `kommo_catalogs_elements` | Catálogos (listas: produtos, etc.). |
| `kommo_links_list` | Vínculos entre entidades (ex.: ligar um contato a um lead). |
| `kommo_links_link` | Vínculos entre entidades (ex.: ligar um contato a um lead). |
| `kommo_links_unlink` | Vínculos entre entidades (ex.: ligar um contato a um lead). |
| `kommo_request` | Chamada crua à API v4 do Kommo — qualquer endpoint, com o seu token. |

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Planos a partir do tier grátis. Veja [docs/precos.md](docs/precos.md).

---

## Privacidade & LGPD

- **Sub-processadores**: Kommo (QSOFT), o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_kommo`.


---

## Suporte

- 📧 [kommo@mcp.ai](mailto:kommo@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/kommo-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_kommo` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
