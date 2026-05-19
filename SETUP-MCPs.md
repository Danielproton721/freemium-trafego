---
title: SETUP - MCPs
type: setup
description: "Lista de MCPs necessários para o funcionamento completo do agente. Consultar no primeiro boot."
---

# SETUP — MCPs Necessários

Este arquivo lista os MCPs (Model Context Protocol servers) que o agente usa. Instalar antes do primeiro boot para que todas as capacidades fiquem ativas.

Sem os MCPs, o agente continua funcionando para análise sobre dados colados manualmente. Com os MCPs, ele acessa as fontes diretamente.

---

## 1. adspower-local-api

**Função:** gestão de perfis de navegador isolado e automação DOM nativa.

**Usado pelo agente em:** `SOPs/12-Gestao-Perfis-AdsPower.md`.

**Pré-requisito:** ter o aplicativo **AdsPower Desktop** instalado, logado e aberto antes de iniciar o agente.

**Endpoint padrão:** `http://127.0.0.1:50325`

**Verificação:** o agente deve conseguir executar `mcp__adspower-local-api__check-status` e receber resposta sem erro.

---

## 2. Gmail

**Função:** leitura de e-mails, busca por mensagens, contexto sobre comunicações com clientes ou plataformas de mídia.

**Tipo:** integração OAuth (autenticação na primeira conexão).

**Verificação:** o agente deve conseguir listar mensagens recentes sem erro de autenticação.

---

## 3. Google Calendar

**Função:** consulta de agenda, criação de eventos, verificação de compromissos relacionados a campanhas e contas.

**Tipo:** integração OAuth.

**Verificação:** o agente deve conseguir listar eventos do calendário sem erro de autenticação.

---

## 4. Google Drive

**Função:** acesso a planilhas e documentos compartilhados de campanha, exportações de relatório, materiais de criativo.

**Tipo:** integração OAuth.

**Verificação:** o agente deve conseguir listar arquivos sem erro de autenticação.

---

## 5. n8n

**Função:** integração com fluxos de automação externos (webhooks, ETL, automações de notificação).

**Tipo:** depende da configuração do servidor n8n.

**Verificação:** o agente deve conseguir consultar o status do servidor n8n configurado.

---

## Ordem de Instalação Recomendada

1. AdsPower Desktop (aplicativo) + MCP `adspower-local-api`.
2. Gmail.
3. Google Calendar.
4. Google Drive.
5. n8n.

Os quatro primeiros são suficientes para a maioria dos fluxos. n8n é opcional e depende de existir infraestrutura própria configurada.

---

## Diagnóstico de Falha

Se algum MCP não conectar:

1. Verificar se o aplicativo correspondente está rodando (caso seja MCP local).
2. Verificar se a autenticação OAuth está válida (caso seja integração de conta).
3. Reportar ao operador antes de tentar fluxo que dependa do MCP indisponível.
4. Continuar operando com os MCPs que conectaram.
