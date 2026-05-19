# Agente de Análise de Tráfego

Sistema de análise de tráfego pago baseado em SOPs, memória persistente e integrações MCP.

## Como Começar

1. **Primeiro uso:** abrir [`SETUP-MCPs.md`](SETUP-MCPs.md) e instalar os MCPs listados.
2. **Iniciar uma sessão:** abrir o projeto no Claude Code e digitar:

   ```
   boot
   ```

   O agente vai listar contas cadastradas, ler o último evento global e perguntar o foco da sessão.

3. **Cadastrar uma nova conta:** copiar [`Templates/conta.md`](Templates/conta.md) para `Memorias/Contas/<nome-da-conta>/<nome-da-conta>.md` e preencher.

## Estrutura

- [`CLAUDE.md`](CLAUDE.md) — instruções carregadas automaticamente pelo Claude Code.
- [`AGENTS-CORE.md`](AGENTS-CORE.md) — identidade, arquitetura e protocolo de boot.
- [`AGENTS-ROUTING.md`](AGENTS-ROUTING.md) — roteamento de pedidos para SOPs.
- [`SETUP-MCPs.md`](SETUP-MCPs.md) — lista de MCPs necessários.
- `SOPs/` — procedimentos operacionais.
- `Metricas/` — referência sobre métricas de tráfego pago.
- `Conhecimento/Referencias/` — material de apoio.
- `Memorias/` — estado persistente: contas, logs, preferências.
- `Templates/` — esqueletos para criação de novos arquivos.
- `skills/` — habilidades carregáveis.
- `raw/` — inbox para arquivos brutos a serem triados (prints, exports, links).

## Comandos Úteis

| Comando | O que faz |
|---|---|
| `boot` | Inicia sessão e lê o estado do sistema |
| `gerar relatório de <conta>` | Lê dados e formata em tabela |
| `diagnóstico de <conta>` | Aplica SOP 05 sobre os dados disponíveis |
| `atualizar SOPs` | Aciona SOP 99 (governança) |

## Suporte

Para preferências e calibração do agente, editar `Memorias/Preferencia-Usuario.md`.
