---
title: 00 - Modo Operacional
type: SOP
tags: [operacao, fluxo, base]
description: "Procedimento base para qualquer sessão. Define entrada, processamento e entrega."
---

# 00 - Modo Operacional

Procedimento base aplicado em qualquer sessão. Define o fluxo padrão e o roteamento para os SOPs específicos.

## Sequência Padrão

1. **Entrada** — receber pedido do operador (análise, relatório, dúvida).
2. **Roteamento** — identificar o tipo de pedido e selecionar o SOP correspondente em `AGENTS-ROUTING.md`.
3. **Leitura de dados** — acessar a fonte indicada (planilha, exportação, integração).
4. **Verificação** — confirmar que os dados estão completos para o pedido.
5. **Processamento** — aplicar o SOP escolhido.
6. **Entrega** — formatar a resposta de forma clara e objetiva.

## Mapa de SOPs Disponíveis

| Tipo de pedido | SOP aplicável |
|---|---|
| Relatório formatado de campanha | `01-Leitura-de-Relatorio.md` |
| Otimização de busca paga, mineração e negativação | `04-Google-Search-Optimization.md` |
| Diagnóstico de performance e variação de métricas | `05-Diagnostico-Performance.md` |
| Auditoria SEO e SEO programático | `08-SEO-e-Escala.md` |
| Triagem de e-mail relacionado a contas | `14-Triagem-Email.md` |
| Operação com perfis de navegador (AdsPower) | `12-Gestao-Perfis-AdsPower.md` |
| Escolha de ferramenta de automação | `13-Decisao-Ferramenta-Automacao.md` |
| Atualização controlada de SOPs e governança | `99-Governanca-e-Aprendizado.md` |

Roteamento completo em `AGENTS-ROUTING.md`.

## Formato de Resposta

- Tabela para listas de métricas.
- Lista com marcadores para itens curtos.
- Parágrafo para explicações.
- Sempre incluir o período analisado.

## Quando Pedir Esclarecimento

- Dado faltando ou inconsistente.
- Pedido ambíguo (qual período, qual campanha, qual métrica).
- Comparação sem base definida.
- Pedido que não bate com nenhum SOP do mapa.
