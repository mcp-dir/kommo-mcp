---
name: kommo-mcp
description: Skill da REST API do Kommo na MCP.AI: 42 endpoints em /api/kommo. Kommo CRM (ex-amoCRM), o CRM de vendas por conversa (WhatsApp, Instagram, Telegram) usado por PMEs e agências. Leia e escreva leads, contatos, empresas, tarefas, notas, funis, tags, campos personalizados, usuários, eventos, conversas e catálogos pela API v4 oficial. Você informa o subdomínio da sua conta e um Token de Longa Duração e a plataforma opera na sua conta. Inclui uma ferramenta de chamada crua para qualquer endpoint da API. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# Kommo — REST API skill

Você tem acesso à **Kommo** REST API na MCP.AI.

> Kommo CRM (ex-amoCRM), o CRM de vendas por conversa (WhatsApp, Instagram, Telegram) usado por PMEs e agências. Leia e escreva leads, contatos, empresas, tarefas, notas, funis, tags, campos personalizados, usuários, eventos, conversas e catálogos pela API v4 oficial. Você informa o subdomínio da sua conta e um Token de Longa Duração e a plataforma opera na sua conta. Inclui uma ferramenta de chamada crua para qualquer endpoint da API.

## Base URL

```
https://api.mcp.ai/api/kommo
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/kommo/account \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/kommo/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (42)

#### `kommo_account`

Dados da conta Kommo conectada (id, nome, subdomínio, moeda, fuso, e opcionalmente usuários/campos/pipelines via `with`). _(POST /api/kommo/account)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `with` | string | Não | Blocos extras separados por vírgula (ex.: "users,pipelines,task_types,custom_fields,amojo_id"). |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |

#### `kommo_catalogs_elements`

Catálogos (listas: produtos, etc.). _(POST /api/kommo/catalogs/elements)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `catalog_id` | integer|string | Não | Id do catálogo (obrigatório em elements). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `catalog_ids` | integer|string[] | Não | Bulk mode: multiple values for catalog_id |

#### `kommo_catalogs_list`

Catálogos (listas: produtos, etc.). _(POST /api/kommo/catalogs/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `catalog_id` | integer|string | Não | Id do catálogo (obrigatório em elements). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `catalog_ids` | integer|string[] | Não | Bulk mode: multiple values for catalog_id |

#### `kommo_companies_create`

Companies do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/companies/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"ACME Ltda","custom_fields_values":[{"field_code":"EMAIL","values":[{"value":"contato@acme.com"}]}]}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_companies_get`

Companies do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/companies/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"ACME Ltda","custom_fields_values":[{"field_code":"EMAIL","values":[{"value":"contato@acme.com"}]}]}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_companies_list`

Companies do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/companies/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"ACME Ltda","custom_fields_values":[{"field_code":"EMAIL","values":[{"value":"contato@acme.com"}]}]}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_companies_update`

Companies do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/companies/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"ACME Ltda","custom_fields_values":[{"field_code":"EMAIL","values":[{"value":"contato@acme.com"}]}]}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_contacts_create`

Contacts do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/contacts/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"Maria","custom_fields_values":[{"field_code":"PHONE","values":[{"value":"+5511999998888"}]}]}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_contacts_get`

Contacts do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/contacts/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"Maria","custom_fields_values":[{"field_code":"PHONE","values":[{"value":"+5511999998888"}]}]}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_contacts_list`

Contacts do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/contacts/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"Maria","custom_fields_values":[{"field_code":"PHONE","values":[{"value":"+5511999998888"}]}]}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_contacts_update`

Contacts do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/contacts/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"Maria","custom_fields_values":[{"field_code":"PHONE","values":[{"value":"+5511999998888"}]}]}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_custom_fields`

Campos personalizados de um tipo de entidade (leads/contacts/companies/customers). _(POST /api/kommo/custom/fields)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `entity_type` | string | Sim | Tipo de entidade: "leads", "contacts", "companies" ou "customers". (leads, contacts, companies, customers) |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |

#### `kommo_customers_create`

Clientes (módulo de vendas recorrentes/RFM do Kommo). _(POST /api/kommo/customers/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"Cliente recorrente","next_price":9900,"next_date":1690000000}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_customers_get`

Clientes (módulo de vendas recorrentes/RFM do Kommo). _(POST /api/kommo/customers/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"Cliente recorrente","next_price":9900,"next_date":1690000000}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_customers_list`

Clientes (módulo de vendas recorrentes/RFM do Kommo). _(POST /api/kommo/customers/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"Cliente recorrente","next_price":9900,"next_date":1690000000}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_customers_update`

Clientes (módulo de vendas recorrentes/RFM do Kommo). _(POST /api/kommo/customers/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"Cliente recorrente","next_price":9900,"next_date":1690000000}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_events`

Eventos/atividades da conta (mudança de estágio, criação, etc.). _(POST /api/kommo/events)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |

#### `kommo_leads_create`

Leads do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/leads/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"Lead site","price":2500,"pipeline_id":123,"status_id":456,"_embedded":{"tags":[{"name":"quente"}]}}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_leads_get`

Leads do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/leads/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"Lead site","price":2500,"pipeline_id":123,"status_id":456,"_embedded":{"tags":[{"name":"quente"}]}}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_leads_list`

Leads do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/leads/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"Lead site","price":2500,"pipeline_id":123,"status_id":456,"_embedded":{"tags":[{"name":"quente"}]}}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_leads_update`

Leads do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/leads/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"name":"Lead site","price":2500,"pipeline_id":123,"status_id":456,"_embedded":{"tags":[{"name":"quente"}]}}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_links_link`

Vínculos entre entidades (ex.: ligar um contato a um lead). _(POST /api/kommo/links/link)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `entity_type` | string | Sim | Tipo de entidade: "leads", "contacts", "companies" ou "customers". (leads, contacts, companies, customers) |
| `entity_id` | integer|string | Sim | Id do registro de origem. |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `data` | string | Não | Vínculo(s) como JSON. Ex.: [{"to_entity_id":456,"to_entity_type":"contacts"}]. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `entity_ids` | integer|string[] | Não | Bulk mode: multiple values for entity_id |

#### `kommo_links_list`

Vínculos entre entidades (ex.: ligar um contato a um lead). _(POST /api/kommo/links/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `entity_type` | string | Sim | Tipo de entidade: "leads", "contacts", "companies" ou "customers". (leads, contacts, companies, customers) |
| `entity_id` | integer|string | Sim | Id do registro de origem. |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `data` | string | Não | Vínculo(s) como JSON. Ex.: [{"to_entity_id":456,"to_entity_type":"contacts"}]. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `entity_ids` | integer|string[] | Não | Bulk mode: multiple values for entity_id |

#### `kommo_links_unlink`

Vínculos entre entidades (ex.: ligar um contato a um lead). _(POST /api/kommo/links/unlink)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `entity_type` | string | Sim | Tipo de entidade: "leads", "contacts", "companies" ou "customers". (leads, contacts, companies, customers) |
| `entity_id` | integer|string | Sim | Id do registro de origem. |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `data` | string | Não | Vínculo(s) como JSON. Ex.: [{"to_entity_id":456,"to_entity_type":"contacts"}]. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `entity_ids` | integer|string[] | Não | Bulk mode: multiple values for entity_id |

#### `kommo_list_accounts`

Lista as contas Kommo conectadas a este install (id/subdomínio, label). _(POST /api/kommo/list/accounts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |

#### `kommo_notes_create`

Notas de uma entidade. action: list (todas as notas do tipo de entidade), list_by_entity (notas de 1 registro), create (adiciona nota; `data` = JSON). Tipos comuns: common, call_in, call_out, sms_in/o _(POST /api/kommo/notes/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `entity_type` | string | Sim | Tipo de entidade: "leads", "contacts", "companies" ou "customers". (leads, contacts, companies, customers) |
| `entity_id` | integer|string | Não | Id do registro (obrigatório em list_by_entity e recomendado em create). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo da nota como JSON. Ex.: {"note_type":"common","params":{"text":"Comentário"}}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `entity_ids` | integer|string[] | Não | Bulk mode: multiple values for entity_id |

#### `kommo_notes_list`

Notas de uma entidade. action: list (todas as notas do tipo de entidade), list_by_entity (notas de 1 registro), create (adiciona nota; `data` = JSON). Tipos comuns: common, call_in, call_out, sms_in/o _(POST /api/kommo/notes/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `entity_type` | string | Sim | Tipo de entidade: "leads", "contacts", "companies" ou "customers". (leads, contacts, companies, customers) |
| `entity_id` | integer|string | Não | Id do registro (obrigatório em list_by_entity e recomendado em create). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo da nota como JSON. Ex.: {"note_type":"common","params":{"text":"Comentário"}}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `entity_ids` | integer|string[] | Não | Bulk mode: multiple values for entity_id |

#### `kommo_notes_list_by_entity`

Notas de uma entidade. action: list (todas as notas do tipo de entidade), list_by_entity (notas de 1 registro), create (adiciona nota; `data` = JSON). Tipos comuns: common, call_in, call_out, sms_in/o _(POST /api/kommo/notes/list/by/entity)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `entity_type` | string | Sim | Tipo de entidade: "leads", "contacts", "companies" ou "customers". (leads, contacts, companies, customers) |
| `entity_id` | integer|string | Não | Id do registro (obrigatório em list_by_entity e recomendado em create). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo da nota como JSON. Ex.: {"note_type":"common","params":{"text":"Comentário"}}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `entity_ids` | integer|string[] | Não | Bulk mode: multiple values for entity_id |

#### `kommo_pipelines_get`

Funis (pipelines) e seus estágios. _(POST /api/kommo/pipelines/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `pipeline_id` | integer|string | Não | Id do funil (obrigatório em get e statuses). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `pipeline_ids` | integer|string[] | Não | Bulk mode: multiple values for pipeline_id |

#### `kommo_pipelines_list`

Funis (pipelines) e seus estágios. _(POST /api/kommo/pipelines/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `pipeline_id` | integer|string | Não | Id do funil (obrigatório em get e statuses). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `pipeline_ids` | integer|string[] | Não | Bulk mode: multiple values for pipeline_id |

#### `kommo_pipelines_statuses`

Funis (pipelines) e seus estágios. _(POST /api/kommo/pipelines/statuses)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `pipeline_id` | integer|string | Não | Id do funil (obrigatório em get e statuses). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `pipeline_ids` | integer|string[] | Não | Bulk mode: multiple values for pipeline_id |

#### `kommo_request`

Chamada crua à API v4 do Kommo — qualquer endpoint, com o seu token. _(POST /api/kommo/request)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `method` | string | Sim | Método HTTP. (GET, POST, PATCH, DELETE) |
| `path` | string | Sim | Caminho relativo da API v4 (ex.: "/leads", "/leads/unsorted", "/salesbot", "/sources"). O prefixo /api/v4 é adicionado se faltar. |
| `query_params` | string | Não | Query string como JSON. Ex.: {"limit":50,"filter":{"pipeline_id":[123]}}. |
| `body` | string | Não | Corpo como JSON (objeto ou array), para POST/PATCH. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |

#### `kommo_tags_create`

Tags de um tipo de entidade. action: list (com busca) | create (cria tags; `data` = JSON, ex.: [{"name":"vip"}]). _(POST /api/kommo/tags/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `entity_type` | string | Sim | Tipo de entidade: "leads", "contacts", "companies" ou "customers". (leads, contacts, companies, customers) |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `data` | string | Não | Tags como JSON (array). Ex.: [{"name":"vip"},{"name":"parceiro"}]. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |

#### `kommo_tags_list`

Tags de um tipo de entidade. action: list (com busca) | create (cria tags; `data` = JSON, ex.: [{"name":"vip"}]). _(POST /api/kommo/tags/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `entity_type` | string | Sim | Tipo de entidade: "leads", "contacts", "companies" ou "customers". (leads, contacts, companies, customers) |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `data` | string | Não | Tags como JSON (array). Ex.: [{"name":"vip"},{"name":"parceiro"}]. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |

#### `kommo_talks_get`

Conversas (talks) do inbox unificado. _(POST /api/kommo/talks/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | talk_id (get). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `filter` | string | Não | Filtro JSON. Ex.: {"contact_id":[123]} ou {"only_in_work":""}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_talks_list`

Conversas (talks) do inbox unificado. _(POST /api/kommo/talks/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | talk_id (get). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `filter` | string | Não | Filtro JSON. Ex.: {"contact_id":[123]} ou {"only_in_work":""}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_tasks_create`

Tasks do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/tasks/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"text":"Ligar para o lead","complete_till":1690000000,"entity_id":123,"entity_type":"leads"}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_tasks_get`

Tasks do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/tasks/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"text":"Ligar para o lead","complete_till":1690000000,"entity_id":123,"entity_type":"leads"}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_tasks_list`

Tasks do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/tasks/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"text":"Ligar para o lead","complete_till":1690000000,"entity_id":123,"entity_type":"leads"}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_tasks_update`

Tasks do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). _(POST /api/kommo/tasks/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do registro (get, ou update de 1 item). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `query` | string | Não | Busca textual livre nos campos da entidade. |
| `with` | string | Não | Entidades relacionadas a incluir, separadas por vírgula (ex.: "contacts,catalog_elements,loss_reason"). |
| `filter` | string | Não | Filtros como JSON. Ex.: {"responsible_user_id":[123],"created_at":{"from":1690000000}} (timestamps Unix). |
| `order` | string | Não | Ordenação como JSON. Ex.: {"updated_at":"desc"} ou {"id":"asc"}. |
| `data` | string | Não | Corpo de create/update como JSON (objeto ou array). Ex.: {"text":"Ligar para o lead","complete_till":1690000000,"entity_id":123,"entity_type":"leads"}. |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_users_get`

Usuários da conta. action: list | get (por id). `with`=role,group para incluir permissões/grupos. _(POST /api/kommo/users/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do usuário (get). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `with` | string | Não | Extras separados por vírgula (ex.: "role,group"). |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

#### `kommo_users_list`

Usuários da conta. action: list | get (por id). `with`=role,group para incluir permissões/grupos. _(POST /api/kommo/users/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | integer|string | Não | Id do usuário (get). |
| `page` | integer | Não | Página da listagem (default 1). |
| `limit` | integer | Não | Itens por página (máx 250, cap do servidor). |
| `with` | string | Não | Extras separados por vírgula (ex.: "role,group"). |
| `account` | string | Não | Quando há múltiplas contas Kommo conectadas: id/subdomínio/label da conexão. Veja kommo_list_accounts. |
| `ids` | integer|string[] | Não | Bulk mode: multiple values for id |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_kommo` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
