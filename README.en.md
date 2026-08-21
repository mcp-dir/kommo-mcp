# Kommo

### Kommo for Claude, ChatGPT and AI agents

Kommo CRM (formerly amoCRM), the conversation-first sales CRM (WhatsApp, Instagram, Telegram) used by SMBs and agencies. Read and write leads, contacts, companies, tasks, notes, pipelines, tags, custom fields, users, events, conversations and catalogs through the official v4 API. You provide your account subdomain and a Long-Lived Token and the platform operates on your account. Includes a raw call tool for any API endpoint.

- 📊 **42 tools**
- ✏️ **Read and write**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Portuguese version](README.md) · [Full docs (PT-BR)](docs/)

---

## One-click install

### Claude (Web and Desktop)

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → name `Kommo`, URL `https://api.mcp.ai/p_kommo`.

### Cursor

[➕ Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=kommo&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9rb21tbyJ9)

### VS Code (Copilot Chat)

[➕ Install in VS Code](vscode:mcp/install?name=kommo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_kommo%22%7D)

### Any other MCP-over-HTTP client

```
https://api.mcp.ai/p_kommo
```

---

## 42 tools

| Tool | Description |
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

---

## Pricing

See [docs/precos.md](docs/precos.md) (PT-BR).

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_kommo` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
