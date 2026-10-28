# Registro de decisões

Registre aqui decisões técnicas relevantes com data, contexto, alternativas, consequência e condição de revisão.

## DEC-001 — Uma única fonte da verdade para reservas

**Estado:** proposta aceita para a arquitetura inicial.

**Decisão:** apenas um motor decide disponibilidade e conflitos. Outros projetos podem fornecer interface, exemplos, relatórios ou adaptadores, mas não devem manter reservas concorrentes.

**Motivo:** evitar dupla reserva, divergência de estado e sincronização frágil.

## DEC-002 — Importar antes de refatorar

**Estado:** proposta aceita.

**Decisão:** preservar a implementação original primeiro, registrar versão/licença e demonstrar que roda isoladamente. Conectar por API/adapter antes de refatorar gradualmente.

**Motivo:** manter procedência, facilitar comparação e permitir identificar qual mudança causou uma falha.

## DEC-003 — Pagamentos manuais primeiro

**Estado:** proposta aceita para MVP.

**Decisão:** registrar Pix conferido manualmente e pagamentos presenciais; gateway online fica fora do primeiro ciclo.

**Motivo:** validar o fluxo operacional sem dependência inicial de fornecedor pago.
