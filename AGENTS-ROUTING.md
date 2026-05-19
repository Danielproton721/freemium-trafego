---
title: AGENTS-ROUTING
type: config
description: "Roteamento entre pedidos do operador e materiais do projeto. Carregado sob demanda."
---

# AGENTS-ROUTING

Mapeia tipos de pedido do operador para os arquivos que devem ser consultados antes da resposta.

---

## Tabela de Roteamento

| Pedido do operador | Material a consultar |
|---|---|
| "boot" / "iniciar" / "start" | `AGENTS-CORE.md` → seção Protocolo de Início |
| "Gerar relatório de campanha" | `SOPs/01-Leitura-de-Relatorio.md` |
| "O que significa essa métrica?" | `Conhecimento/Referencias/Glossario-Metricas.md` |
| "Qual o procedimento padrão?" | `SOPs/00-Modo-Operacional.md` |
| "Análise de métricas" | `skills/analise-trafego/SKILL.md` |
| "Relatório executivo" / "resumo semanal" / "fechamento mensal" | `skills/relatorio-formatado/SKILL.md` |
| "Ver e-mails" / "triagem de e-mail" / "tem comunicação do cliente" | `SOPs/14-Triagem-Email.md` |
| "Otimizar campanha de busca" / "palavras negativas" / "mineração de termos" | `SOPs/04-Google-Search-Optimization.md` |
| "SEO" / "tráfego orgânico" / "SEO programático" | `SOPs/08-SEO-e-Escala.md` |
| "Diagnóstico de performance" / "por que o CPA subiu" / "performance caiu" | `SOPs/05-Diagnostico-Performance.md` |
| "Abrir perfil" / "gestão de perfil" / "criar perfil de navegador" | `SOPs/12-Gestao-Perfis-AdsPower.md` |
| "Qual ferramenta de automação usar" | `SOPs/13-Decisao-Ferramenta-Automacao.md` |
| "Atualizar SOPs" / "revisão estrutural" / "governança" / "aprendizado do sistema" | `SOPs/99-Governanca-e-Aprendizado.md` |

Se o pedido não bate com nenhuma linha, perguntar ao operador qual a expectativa antes de responder.

---

## Critério de Carregamento

Este arquivo é carregado sob demanda quando o operador faz um pedido que exige consulta a procedimento ou referência. Não precisa ser lido em toda sessão.
