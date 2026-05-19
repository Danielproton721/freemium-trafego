---
title: 99 - Governança e Aprendizado
type: SOP
tags: [governanca, aprendizado, meta]
description: "Mecanismo de atualização controlada dos SOPs e da base de conhecimento. Define como mudanças entram no sistema sem perder qualidade."
---

# 99 - Governança e Aprendizado

Procedimento responsável pela manutenção do próprio sistema. Não trata de campanha. Trata das regras que o agente segue.

Sem este SOP, o sistema se torna inconsistente, acumula contradições e perde rastreabilidade das decisões.

---

## Gatilho de Ativação

Este SOP deve ser executado quando:

1. O operador solicitar explicitamente uma revisão estrutural.
2. Houver acúmulo de observações pendentes registradas durante operação.
3. Ao final de um ciclo de trabalho (semana, sprint, projeto).

---

## Materiais de Trabalho

- **Entrada:** anotações acumuladas durante operação (correções, novas regras, padrões observados).
- **Saída:** arquivos em `SOPs/`, `Metricas/` ou `Conhecimento/Referencias/`.

---

## Processo

### Passo 1: Leitura das Pendências

Ler todas as anotações pendentes desde a última execução. Identificar cada item como "correção de regra existente", "nova regra" ou "observação geral".

### Passo 2: Triagem e Destino

Para cada item, definir onde a informação deve morar:

- Regra operacional recorrente → SOP correspondente.
- Definição conceitual aplicável em qualquer caso → `Conhecimento/Referencias/`.
- Parâmetro numérico de mercado → `Metricas/`.
- Preferência de comportamento do agente → `AGENTS-CORE.md`.

### Passo 3: Detecção de Conflito

Antes de gravar, verificar se a nova regra contradiz uma regra existente no destino:

- **Sem conflito:** prosseguir ao passo 4.
- **Com conflito:** o agente não resolve sozinho. Apresentar ao operador as duas versões lado a lado e aguardar decisão explícita.

### Passo 4: Fusão Controlada

Critério de qualidade a aplicar em cada fusão:

1. **Preservação:** o detalhe específico exigido pelo operador foi mantido na íntegra. Generalização não pode apagar restrição.
2. **Não duplicação:** se a regra nova substitui uma antiga, a antiga é removida. Não acumular orientações conflitantes no mesmo arquivo.
3. **Legibilidade:** hierarquia clara (listas, negrito, alertas). O arquivo precisa ser lido rapidamente em contexto de operação.

### Passo 5: Limpeza

Após gravar a regra no destino correto, remover o item correspondente da lista de pendências. A lista termina o processo vazia.

### Passo 6: Relatório

Ao finalizar, reportar ao operador:

1. Quais arquivos foram atualizados (com resumo de uma linha por alteração).
2. Se houve conflitos e qual decisão foi tomada.
3. Recomendar reindexação de busca caso o sistema utilize busca semântica sobre os arquivos.

---

## Regras Invioláveis

1. **Nunca alterar um SOP por iniciativa do agente sem registro prévio ou ordem explícita do operador.** Toda mudança estrutural tem origem rastreável.
2. **Nunca resolver conflito de regras sozinho.** Quando há contradição, a decisão é do operador.
3. **Nunca pular o critério de qualidade.** Se a fusão não atinge a barra, refazer antes de gravar.
