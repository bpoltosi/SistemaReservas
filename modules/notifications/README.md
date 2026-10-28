# modules/notifications — notificações

## Canais previstos

- E-mail de confirmação/cancelamento.
- Lembrete antes do horário reservado.
- Notificação interna para recepção/admin.
- Outros canais somente depois de avaliar custo, consentimento e privacidade.

## Eventos conceituais

- `reservation.created`
- `reservation.cancelled`
- `reservation.rescheduled`
- `payment.recorded`

Esses nomes são propostas; o adaptador deve mapear os eventos reais da fonte escolhida.

## Requisitos

- Envio assíncrono quando possível, com tentativas e registro de falha.
- Idempotência para não enviar a mesma confirmação repetidamente.
- Não bloquear a criação/cancelamento de reserva se um e-mail falhar.
- Nunca incluir segredos ou dados desnecessários no conteúdo/logs.
- Configuração de envio por variáveis de ambiente e modo de teste sem envio real.

## Estado

Diretório reservado; nenhum provedor foi configurado neste PR.
