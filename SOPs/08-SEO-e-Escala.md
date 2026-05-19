---
title: 08 - SEO e Escala Programática
type: SOP
tags: [seo, busca-organica, programatico, escala]
description: "Auditoria de SEO e padrões para escala via SEO programático."
---

# 08 - SEO e Escala Programática

Procedimento para auditoria de SEO técnico e estruturação de páginas em escala via templates programáticos.

---

## Auditoria Estrutural SEO

**Gatilho de uso:** diagnóstico geral de marca, queda no tráfego orgânico relatado no GA4 ou na Search Console.

### Entrega esperada

- Ranking do Top 10 de problemas técnicos por impacto financeiro estimado (exemplo: páginas de checkout desindexadas do robô de busca).
- Gap de keywords vs concorrentes — quais palavras-chave os concorrentes ranqueiam na primeira página em que a marca analisada está ausente.
- Estimativa de tráfego incremental projetado caso a pauta recomendada seja adotada.

---

## SEO Programático

**Gatilho de uso:** produto pronto, domínio com autoridade já estabelecida, intenção de capturar long-tail em escala sem aumentar o gasto em mídia paga.

### Padrões de URL

Estruturação recomendada de landing pages geradas em escala para capturar fundo de funil de Google Search:

- **Localização estática:** `/servico-em-cidade` (exemplo: `/advogado-em-sao-paulo`)
- **Grid de comparação:** `/marca-vs-concorrente` (exemplo: `/nossa_marca-vs-rdstation`)
- **Top directories:** `/melhor-categoria-para-uso` (exemplo: `/melhor-crm-para-clinica`)

### Regras Fixas

- **Títulos com variáveis:** padrão como `[Sua Ferramenta] alternative para [Nicho]`.
- **Corpo de texto não pode ser idêntico entre páginas** com troca apenas da palavra-chave. Inserir blocos de componentes dinâmicos (tabelas de funcionalidade, comparativos, listas específicas) para evitar penalidade por spam.
- **Mínimo de 300 palavras únicas acima da dobra** em cada página programática. Conteúdo abaixo desse volume tende a ser tratado como thin content pelo Google e sofre penalidade de ranqueamento.

---

## Anti-padrões

1. Gerar páginas programáticas em massa sem variação de conteúdo entre elas.
2. Indexar páginas de checkout, login ou área restrita.
3. Subir páginas programáticas sem componentes únicos (apenas substituição de variável no template).
