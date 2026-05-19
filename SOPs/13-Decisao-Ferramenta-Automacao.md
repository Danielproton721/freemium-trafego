---
title: 13 - Decisão de Ferramenta de Automação
type: SOP
tags: [execucao, automacao, decisao]
description: "Critério para escolha do tipo de ferramenta de automação conforme a complexidade da tarefa."
---

# 13 - Decisão de Ferramenta de Automação

Critério para decidir qual abordagem de automação usar quando uma tarefa exige interação com navegador ou interface gráfica.

## Princípio

Ferramentas de automação variam em complexidade e custo de operação. Tarefas simples não justificam o overhead de uma ferramenta robusta; tarefas complexas quebram quando feitas com ferramenta simples demais.

## Quando Usar Automação Simples

- Fluxo conhecido e estável.
- Elementos da interface não mudam com frequência.
- Sequência curta de ações (abrir, preencher, clicar, capturar).
- Não há necessidade de inspecionar requisições de rede ou eventos do console.

## Quando Usar Automação Robusta

- Interface complexa que muda com frequência (painéis de anunciante, dashboards de plataforma).
- Necessidade de esperar por condições específicas no carregamento.
- Necessidade de inspecionar chamadas de rede.
- Necessidade de lidar com diálogos do navegador.
- Upload de arquivos.
- Múltiplas abas.

## Regra Geral

Começar pela abordagem simples. Migrar para a robusta apenas quando a tarefa exigir explicitamente uma das capacidades acima.

## Anti-Padrão

Usar ferramenta robusta para tarefa simples gera overhead desnecessário e torna o fluxo mais frágil. Usar ferramenta simples em tarefa complexa gera retrabalho e quebra silenciosa.
