# Ferramentas

Kommo expõe 42 ferramentas.

### 1. `kommo_list_accounts`
**Input**: `account` (opcional)

Lista as contas Kommo conectadas a este install (id/subdomínio, label).

### 2. `kommo_account`
**Input**: `with` (opcional), `account` (opcional)

Dados da conta Kommo conectada (id, nome, subdomínio, moeda, fuso, e opcionalmente usuários/campos/pipelines via `with`).

### 3. `kommo_leads_list`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Leads do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: list] Bulk support:…

### 4. `kommo_leads_get`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Leads do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: get] Bulk support:…

### 5. `kommo_leads_create`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Leads do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: create] Bulk suppor…

### 6. `kommo_leads_update`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Leads do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: update] Bulk suppor…

### 7. `kommo_contacts_list`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Contacts do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: list] Bulk suppo…

### 8. `kommo_contacts_get`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Contacts do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: get] Bulk suppor…

### 9. `kommo_contacts_create`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Contacts do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: create] Bulk sup…

### 10. `kommo_contacts_update`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Contacts do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: update] Bulk sup…

### 11. `kommo_companies_list`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Companies do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: list] Bulk supp…

### 12. `kommo_companies_get`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Companies do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: get] Bulk suppo…

### 13. `kommo_companies_create`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Companies do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: create] Bulk su…

### 14. `kommo_companies_update`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Companies do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: update] Bulk su…

### 15. `kommo_tasks_list`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Tasks do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: list] Bulk support:…

### 16. `kommo_tasks_get`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Tasks do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: get] Bulk support:…

### 17. `kommo_tasks_create`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Tasks do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: create] Bulk suppor…

### 18. `kommo_tasks_update`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Tasks do Kommo. action: list (busca paginada com filtros), get (por id), create (cria, body em `data`), update (atualiza; com `id` = 1 item, sem `id` = bulk com array em `data`). [Flattened action: update] Bulk suppor…

### 19. `kommo_customers_list`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Clientes (módulo de vendas recorrentes/RFM do Kommo).

### 20. `kommo_customers_get`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Clientes (módulo de vendas recorrentes/RFM do Kommo).

### 21. `kommo_customers_create`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Clientes (módulo de vendas recorrentes/RFM do Kommo).

### 22. `kommo_customers_update`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Clientes (módulo de vendas recorrentes/RFM do Kommo).

### 23. `kommo_notes_list`
**Input**: `entity_type`, `entity_id` (opcional), `page` (opcional), `limit` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `entity_ids` (opcional)

Notas de uma entidade. action: list (todas as notas do tipo de entidade), list_by_entity (notas de 1 registro), create (adiciona nota; `data` = JSON). Tipos comuns: common, call_in, call_out, sms_in/out, attachment. […

### 24. `kommo_notes_list_by_entity`
**Input**: `entity_type`, `entity_id` (opcional), `page` (opcional), `limit` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `entity_ids` (opcional)

Notas de uma entidade. action: list (todas as notas do tipo de entidade), list_by_entity (notas de 1 registro), create (adiciona nota; `data` = JSON). Tipos comuns: common, call_in, call_out, sms_in/out, attachment. […

### 25. `kommo_notes_create`
**Input**: `entity_type`, `entity_id` (opcional), `page` (opcional), `limit` (opcional), `filter` (opcional), `order` (opcional), `data` (opcional), `account` (opcional), `entity_ids` (opcional)

Notas de uma entidade. action: list (todas as notas do tipo de entidade), list_by_entity (notas de 1 registro), create (adiciona nota; `data` = JSON). Tipos comuns: common, call_in, call_out, sms_in/out, attachment. […

### 26. `kommo_tags_list`
**Input**: `entity_type`, `page` (opcional), `limit` (opcional), `query` (opcional), `filter` (opcional), `data` (opcional), `account` (opcional)

Tags de um tipo de entidade. action: list (com busca) | create (cria tags; `data` = JSON, ex.: [{"name":"vip"}]). [Flattened action: list]

### 27. `kommo_tags_create`
**Input**: `entity_type`, `page` (opcional), `limit` (opcional), `query` (opcional), `filter` (opcional), `data` (opcional), `account` (opcional)

Tags de um tipo de entidade. action: list (com busca) | create (cria tags; `data` = JSON, ex.: [{"name":"vip"}]). [Flattened action: create]

### 28. `kommo_pipelines_list`
**Input**: `pipeline_id` (opcional), `page` (opcional), `limit` (opcional), `account` (opcional), `pipeline_ids` (opcional)

Funis (pipelines) e seus estágios.

### 29. `kommo_pipelines_get`
**Input**: `pipeline_id` (opcional), `page` (opcional), `limit` (opcional), `account` (opcional), `pipeline_ids` (opcional)

Funis (pipelines) e seus estágios.

### 30. `kommo_pipelines_statuses`
**Input**: `pipeline_id` (opcional), `page` (opcional), `limit` (opcional), `account` (opcional), `pipeline_ids` (opcional)

Funis (pipelines) e seus estágios.

### 31. `kommo_custom_fields`
**Input**: `entity_type`, `page` (opcional), `limit` (opcional), `account` (opcional)

Campos personalizados de um tipo de entidade (leads/contacts/companies/customers).

### 32. `kommo_users_list`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `with` (opcional), `account` (opcional), `ids` (opcional)

Usuários da conta. action: list | get (por id). `with`=role,group para incluir permissões/grupos. [Flattened action: list] Bulk support: accepts ids for batched execution.

### 33. `kommo_users_get`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `with` (opcional), `account` (opcional), `ids` (opcional)

Usuários da conta. action: list | get (por id). `with`=role,group para incluir permissões/grupos. [Flattened action: get] Bulk support: accepts ids for batched execution.

### 34. `kommo_events`
**Input**: `page` (opcional), `limit` (opcional), `with` (opcional), `filter` (opcional), `order` (opcional), `account` (opcional)

Eventos/atividades da conta (mudança de estágio, criação, etc.).

### 35. `kommo_talks_list`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `filter` (opcional), `account` (opcional), `ids` (opcional)

Conversas (talks) do inbox unificado.

### 36. `kommo_talks_get`
**Input**: `id` (opcional), `page` (opcional), `limit` (opcional), `filter` (opcional), `account` (opcional), `ids` (opcional)

Conversas (talks) do inbox unificado.

### 37. `kommo_catalogs_list`
**Input**: `catalog_id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `filter` (opcional), `account` (opcional), `catalog_ids` (opcional)

Catálogos (listas: produtos, etc.).

### 38. `kommo_catalogs_elements`
**Input**: `catalog_id` (opcional), `page` (opcional), `limit` (opcional), `query` (opcional), `filter` (opcional), `account` (opcional), `catalog_ids` (opcional)

Catálogos (listas: produtos, etc.).

### 39. `kommo_links_list`
**Input**: `entity_type`, `entity_id`, `page` (opcional), `limit` (opcional), `filter` (opcional), `data` (opcional), `account` (opcional), `entity_ids` (opcional)

Vínculos entre entidades (ex.: ligar um contato a um lead).

### 40. `kommo_links_link`
**Input**: `entity_type`, `entity_id`, `page` (opcional), `limit` (opcional), `filter` (opcional), `data` (opcional), `account` (opcional), `entity_ids` (opcional)

Vínculos entre entidades (ex.: ligar um contato a um lead).

### 41. `kommo_links_unlink`
**Input**: `entity_type`, `entity_id`, `page` (opcional), `limit` (opcional), `filter` (opcional), `data` (opcional), `account` (opcional), `entity_ids` (opcional)

Vínculos entre entidades (ex.: ligar um contato a um lead).

### 42. `kommo_request`
**Input**: `method`, `path`, `query_params` (opcional), `body` (opcional), `account` (opcional)

Chamada crua à API v4 do Kommo — qualquer endpoint, com o seu token.

## Prompts de exemplo

```
Liste os leads no funil de vendas que estão parados há mais de 7 dias
Crie um lead novo para a Maria com telefone e uma tarefa de retorno amanhã
Mostre as conversas abertas no inbox e quem é o responsável
```
