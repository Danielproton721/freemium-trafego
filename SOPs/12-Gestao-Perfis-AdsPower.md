---
title: 12 - Gestão de Perfis AdsPower (MCP)
type: SOP
tags: [adspower, mcp, perfis, execucao]
description: "Referência operacional do MCP adspower-local-api. Gestão de perfis, fingerprint, proxy e automação de navegador nativa."
---

# 12 - Gestão de Perfis AdsPower via MCP

Referência operacional do MCP `adspower-local-api`.

## Conexão

- **MCP:** `adspower-local-api`
- **Endpoint padrão:** `http://127.0.0.1:50325`
- **Autenticação:** Bearer token em header
- **Pré-requisito:** AdsPower Desktop aberto e logado antes de qualquer chamada

## Regra de Conexão

- Testar a conexão via `check-status` ao iniciar.
- Em caso de falha, tentar reconectar no máximo duas vezes.
- Se a segunda tentativa falhar, parar a operação e reportar ao operador.

## Macro de Abertura de Perfil

Para executar automação DOM em um perfil, o fluxo é sempre de três passos:

```
1. open-browser            { profileId }                    → guardar wsUrl
2. connect-browser-with-ws { wsUrl, userId: profileId }     → conexão CDP
3. navigate / click / fill / ...                            → ações no DOM
```

Se a operação for manual (o operador dirige o navegador), parar no passo 1.

## Recuperação de Conexão CDP

A conexão CDP é frágil e não sobrevive a navegador fechado pelo usuário ou a intervalos longos entre chamadas. Quando uma ferramenta retornar "Browser not connected":

```
get-opened-browser
  ├─ vazio        → navegador caído: open-browser + connect-browser-with-ws + retry
  └─ perfil ativo → só a conexão CDP caiu: connect-browser-with-ws com wsUrl atual + retry
```

Antes de qualquer ação irreversível (publicar, alterar configuração crítica, deletar), revalidar a conexão.

## Referência das Ferramentas

Todas sob o prefixo `mcp__adspower-local-api__`.

### Perfis (CRUD)

| Tool | Uso |
|---|---|
| `get-browser-list` | Listar todos os perfis |
| `create-browser` | Criar perfil novo |
| `update-browser` | Editar perfil existente |
| `delete-browser` | Deletar perfil |
| `move-browser` | Mover perfil entre grupos |
| `update-patch` | Atualizar kernel/patch do perfil |
| `share-profile` | Gerar link de compartilhamento |

### Configuração Padrão de Criação de Perfil

Ao criar um perfil novo via `create-browser`:

1. **Navegador:** SunBrowser (base Chrome). Não usar Firefox.
2. **Sistema operacional declarado:** Windows. Não usar macOS.
3. **Proxy:** obrigatório. Não criar perfil sem proxy. Preferência por SOCKS5 e IPv6.
4. **Fingerprint:** gerar nova fingerprint após configurar proxy e navegador.

### Navegador (abrir / fechar / inspecionar)

| Tool | Uso |
|---|---|
| `open-browser` | Abrir navegador do perfil → retorna `ws_endpoint` + `webdriver` |
| `close-browser` | Fechar um perfil |
| `close-all-profiles` | Fechar todos os perfis abertos |
| `get-browser-active` | Checar se um perfil está aberto |
| `get-opened-browser` | Listar perfis abertos no momento |
| `connect-browser-with-ws` | Conectar em sessão já aberta |

### Automação DOM

| Tool | Uso |
|---|---|
| `navigate` | Ir para uma URL |
| `open-new-page` | Abrir aba nova |
| `click-element` | Clicar |
| `fill-input` | Preencher input |
| `hover-element` | Hover |
| `drag-element` | Arrastar |
| `press-key` | Teclar (Enter, Tab, Esc, etc.) |
| `select-option` | Selecionar opção em `<select>` |
| `scroll-element` | Rolar até elemento |
| `iframe-click-element` | Clicar dentro de iframe |
| `screenshot` | Capturar tela |
| `get-page-html` | HTML da página |
| `get-page-visible-text` | Apenas texto visível |
| `evaluate-script` | Executar JS arbitrário |

### Fingerprint / Identidade

| Tool | Uso |
|---|---|
| `new-fingerprint` | Gerar fingerprint aleatória |
| `get-profile-cookies` | Exportar cookies do perfil |
| `get-profile-ua` | User-Agent ativo |

### Proxy

| Tool | Uso |
|---|---|
| `get-proxy-list` | Listar proxies configurados |
| `create-proxy` | Adicionar proxy |
| `update-proxy` | Editar proxy |
| `delete-proxy` | Remover proxy |

### Grupos e Tags

| Tool | Uso |
|---|---|
| `get-group-list` / `create-group` / `update-group` | Grupos de perfis |
| `get-tag-list` / `create-tag` / `update-tag` / `delete-tag` | Tags de perfil |

### Sistema

| Tool | Uso |
|---|---|
| `check-status` | Healthcheck do daemon |
| `get-application-list` | Aplicativos instalados |
| `get-cloud-active` | Status cloud |
| `get-kernel-list` / `download-kernel` | Kernels disponíveis |
| `delete-cache-v2` | Limpar cache do perfil |

## Quando Usar Este MCP

- Operações que envolvem identidade, fingerprint e proxy do perfil.
- Ciclos simples de automação (click, fill, navigate, screenshot).
- Gestão de perfis em lote.

## Fluxo Operacional Padrão

```
1. check-status                        → confirma daemon ativo
2. get-browser-list                    → identificar o user_id do perfil
3. open-browser(user_id)               → abre o navegador, retorna ws_endpoint
4. connect-browser-with-ws             → conecta CDP
5. navigate(url)                       → navega para o destino
6. screenshot                          → evidência inicial
7. [loop de inspeção + ação]
8. screenshot                          → evidência final
9. close-browser(user_id)              → encerra sessão
```

## Regras de Segurança

1. Não abrir múltiplos perfis simultâneos sem necessidade — cada perfil consome recurso e aumenta risco de cruzamento de identidade.
2. Validar configuração de proxy antes de abrir um perfil que dependa dele.
3. Capturar screenshot antes de qualquer ação irreversível.
4. Fechar o navegador ao final da operação.

## Troubleshooting

- **`check-status` falha:** daemon do AdsPower está fechado. Pedir ao operador para abrir o aplicativo.
- **`get-browser-list` retorna lista vazia:** confirmar com o operador se os perfis ainda existem no AdsPower antes de tentar diagnosticar a API.
- **`open-browser` trava:** verificar extensões ativas no perfil ou tentar perfil alternativo.
- **Cookies ausentes:** perfil pode ter feito logout. Validar via `get-profile-cookies` e pedir login manual se necessário.
- **Fingerprint rejeitado:** gerar nova fingerprint com `new-fingerprint` e limpar cache com `delete-cache-v2` antes de reabrir.
