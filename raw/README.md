# raw/ — Inbox

Pasta de entrada para arquivos brutos que serão triados pelo agente.

## O que colocar aqui

- Prints de painel (.png, .jpg)
- Exports de relatório (.csv, .xlsx)
- Documentos com instruções soltas (.txt, .md)
- Links em arquivo único (`links.md`)

## Fluxo

1. Operador joga o arquivo aqui.
2. Em sessão, pedir ao agente: "processa o que tem em raw/".
3. O agente identifica o tipo, roteia para o SOP correspondente e move o conteúdo para o destino final (geralmente `Memorias/Contas/<conta>/outputs/`).
4. Após processado, o arquivo bruto pode ser removido ou arquivado.
