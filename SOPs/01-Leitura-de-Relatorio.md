# Leitura de Relatório de Campanha

## Objetivo

Organizar os números de uma campanha em formato legível para o operador.

## Passos

1. Identificar o período do relatório.
2. Listar as campanhas presentes nos dados.
3. Para cada campanha, extrair:
   - Gasto total
   - Impressões
   - Cliques
   - Conversões
   - Receita (se disponível)
4. Calcular as métricas derivadas:
   - CTR = Cliques / Impressões
   - CPC = Gasto / Cliques
   - CPA = Gasto / Conversões
   - ROAS = Receita / Gasto
5. Apresentar em tabela.

## Modelo de Saída

```
Período: <início> a <fim>

| Campanha | Gasto | Impressões | Cliques | CTR | Conversões | CPA | ROAS |
|----------|-------|------------|---------|-----|------------|-----|------|
| ...      | ...   | ...        | ...     | ... | ...        | ... | ...  |
```

## Observações

- Se algum campo estiver ausente, marcar como `—` na tabela.
- Apresentar os números sem interpretação. Interpretação só quando o operador pedir.
